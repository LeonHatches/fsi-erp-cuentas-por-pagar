# Arquitectura del módulo de Cuentas por Pagar

Resumen del documento de arquitectura aprobado por el equipo (autores: Daniel Guillen y Brigitte Mengoa; docente: Juan Carlos Juárez Bueno). Registra las decisiones tecnológicas y su razón. La aplicación de estas decisiones al repositorio se describe en la [guía de implementación](GUIA_IMPLEMENTACION.md).

## 1. Objetivo y alcance

El primer incremento es un CRUD de obligaciones con proveedores: **registrar, consultar, modificar y anular**. Debe impedir comprobantes duplicados y datos inválidos, como montos negativos. Los campos, reglas y restricciones concretas los define el Product Owner en [T-02](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/3).

El registro de pagos se aborda en un incremento posterior; las tecnologías se eligieron también pensando en esa etapa, en la que se aplicarán pagos y se actualizarán saldos sin errores.

## 2. Criterios de comparación

| Criterio | Qué se evalúa |
|---|---|
| Integridad de los datos | Restricciones (PK, FK, UNIQUE, CHECK), transacciones y manejo exacto de montos. |
| Facilidad para el equipo | Curva de aprendizaje y documentación disponible. |
| Rapidez de implementación | Tiempo necesario para el primer incremento funcional. |
| Documentación de servicios | Facilidad para mostrar qué datos recibe y devuelve cada servicio. |
| Costo y licencia | Uso gratuito para el desarrollo del curso. |
| Crecimiento e integración | Posibilidad de ampliar el módulo y conectarlo con el ERP. |

## 3. Decisiones y alternativas

| Componente | Elegido | Alternativas evaluadas | Razón principal |
|---|---|---|---|
| Base de datos | **PostgreSQL** | MySQL, SQL Server, SQLite | Gratuito; `NUMERIC` exacto; PK, FK, UNIQUE y CHECK completas; transacciones ACID; es la base de Odoo. SQLite se descarta por no manejar decimales exactos. |
| Lenguaje | **Python** | Java, JavaScript (Node.js), C# | Curva de aprendizaje baja; tipo `Decimal` para montos; es el lenguaje de Odoo. JavaScript se descarta en el backend por usar punto flotante. |
| Backend | **Django + Django REST Framework** | FastAPI, Flask | Estructura definida (proyecto, apps, models, serializers, views, urls); ORM; panel de administración; Swagger con drf-spectacular. |
| Acceso a datos | **ORM de Django con migraciones** | Script manual + ORM sobre tablas existentes; script manual + SQL directo | Una sola definición de las tablas (los modelos), sin riesgo de desincronización, con restricciones mediante `Meta.constraints` y base de prueba creada desde las migraciones. |
| Frontend | **React + Vite** | HTML/CSS/JavaScript; plantillas de Django | Componentes reutilizables (formularios, tablas, mensajes) y separación del backend, del que consume la API. |
| Lenguaje del frontend | **TypeScript** | JavaScript | Interfaces que reflejan el contrato de API; DRF envía los montos como texto para conservar su precisión y TypeScript permite declararlos así. |
| Estilos | **Tailwind CSS** | CSS propio, Bootstrap | Escala común de colores y espaciados entre pantallas; plugin oficial para Vite; el archivo final solo incluye los estilos usados. |
| Pruebas | **pytest y pytest-django** | — | Automatizan el recorrido completo con una base de prueba creada desde las migraciones. |

### Acceso a la base de datos

La estructura se escribe una sola vez, en los modelos de Django, incluidas las restricciones UNIQUE, CHECK y FOREIGN KEY mediante `Meta.constraints`; Django las crea en PostgreSQL. Así la base aplica las reglas aunque falle el código.

- `01_estructura.sql` se obtiene con `sqlmigrate`, sirve para revisar y documentar las tablas y **no se edita a mano**: cualquier cambio se hace en los modelos y el script se vuelve a generar.
- `02_datos_prueba.sql` se escribe aparte, porque contiene registros de ejemplo y no tablas.

### Herramientas complementarias

| Herramienta | Uso |
|---|---|
| Git y GitHub | Control de versiones, ramas por actividad y revisión mediante pull requests. |
| DBeaver o pgAdmin | Ejecutar los scripts SQL y revisar tablas y datos de prueba. |
| Panel de administración de Django | Consultar y cargar datos sin depender del frontend. |
| Swagger UI (drf-spectacular) | Documentar y probar los servicios del backend. |
| django-cors-headers | Permitir que React consuma la API desde otro puerto. |
| pytest y pytest-django | Pruebas automáticas. |
| Node.js y npm | Crear y ejecutar el proyecto React, Vite y TypeScript; instalar Tailwind CSS. |
| Entorno virtual (venv) y `requirements.txt` | Instalar las mismas dependencias de Python en todas las máquinas. |

## 4. Arquitectura propuesta

El programa se organiza en tres capas. El frontend se comunica con el backend mediante una API REST que intercambia JSON, y el backend es la única capa que accede a la base de datos.

```mermaid
flowchart LR
    subgraph presentacion["Capa de presentación"]
        react["React + Vite + TypeScript<br/>Tailwind CSS"]
    end
    subgraph negocio["Capa de aplicación"]
        api["Django + DRF<br/>serializers, views, urls<br/>Swagger (drf-spectacular)"]
    end
    subgraph datos["Capa de datos"]
        pg[("PostgreSQL<br/>restricciones UNIQUE, CHECK, FK")]
    end
    react -- "API REST · JSON" --> api
    api -- "ORM de Django" --> pg
```

### Flujo: registrar una obligación

1. El usuario completa el formulario con los datos definidos por el Product Owner.
2. El componente de React, tipado con TypeScript, envía los datos a la API en JSON.
3. El serializer de DRF valida los datos (por ejemplo, monto mayor que cero y proveedor existente).
4. Si son válidos, el backend guarda la obligación. Si el comprobante ya existe, la restricción UNIQUE de la base lo impide y la API responde con un mensaje de error.
5. La API devuelve la obligación registrada y el frontend actualiza el listado.

Consultar y modificar siguen el mismo recorrido. **Anular no elimina el registro**: cambia su estado a anulada, para conservar el historial de deudas.

### Validaciones en dos niveles

Las reglas se controlan en el backend, para mostrar mensajes claros, y también en la base de datos, para que ningún dato incorrecto se guarde aunque falle el código. Un comprobante duplicado se impide con UNIQUE y un monto negativo con CHECK; ambas se definen en los modelos. Las tablas y atributos exactos dependen del diccionario de datos ([T-04](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/5)).

### Incremento posterior: registro de pagos

Cada pago se aplicará dentro de una transacción (`transaction.atomic`): el backend verificará que no supere el saldo pendiente y, en la misma operación, registrará el pago y actualizará el saldo. Por ejemplo, una obligación de 100 con un pago de 40 queda con saldo de 60. La arquitectura no requiere cambios para esta etapa.

## 5. Integración con el ERP

Al comunicarse por API REST con JSON, el módulo puede integrarse con otros módulos del ERP aunque usen otro lenguaje. Si el curso define una tecnología común para todo el ERP, esta decisión se revisará antes de iniciar la implementación.

## Referencias

- [PostgreSQL](https://www.postgresql.org/docs/) · [MySQL](https://dev.mysql.com/doc/) · [SQLite: tipos de datos](https://www.sqlite.org/datatype3.html)
- [Python: decimal](https://docs.python.org/3/library/decimal.html)
- [Django: migraciones](https://docs.djangoproject.com/en/stable/topics/migrations/) · [Django: restricciones](https://docs.djangoproject.com/en/stable/ref/models/constraints/)
- [Django REST Framework](https://www.django-rest-framework.org/) · [drf-spectacular](https://drf-spectacular.readthedocs.io/)
- [React](https://react.dev/) · [Vite](https://vite.dev/) · [TypeScript](https://www.typescriptlang.org/docs/) · [Tailwind CSS](https://tailwindcss.com/docs)
- [Odoo: documentación para desarrolladores](https://www.odoo.com/documentation/)
