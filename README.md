# ERP FSI — Cuentas por Pagar
Proyecto académico de la Escuela Profesional de Ingeniería de Sistemas de la Universidad Nacional de San Agustín de Arequipa, desarrollado para el curso de Fundamentos de Sistemas de Información.

Este repositorio reúne el trabajo del módulo de Cuentas por Pagar, perteneciente a la Tribu de Egresos. Su código se integrará posteriormente al repositorio común del ERP, según la coordinación entre equipos.

## Objetivo

El objetivo del módulo de Cuentas por Pagar es gestionar y controlar las deudas que la empresa mantiene con sus proveedores, desde que se registra el comprobante de compra hasta que se realiza el pago. Para ello, el módulo debe identificar correctamente al proveedor, el tipo de comprobante, la moneda, el banco, el medio de pago y la clasificación de la operación, además de relacionar la deuda con las cuentas contables correspondientes.

## Primer incremento

El primer CRUD permite registrar, consultar, modificar y anular obligaciones con proveedores. Rafael define los campos, reglas y restricciones en T-02. El registro de pagos se abordará en un incremento posterior.

- [HU-01 y sus tareas](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/1).
- [Tablero: Cuentas por Pagar — Primer CRUD](https://github.com/users/LeonHatches/projects/1).
- [Planificación, responsables y diagrama del flujo](docs/planificacion/primer-crud.md).
- [Guía de colaboración](CONTRIBUTING.md).

Las instrucciones de configuración y ejecución del programa se documentarán en la guía de implementación.

## Tecnologías acordadas

- **Backend:** Python y Django REST Framework (DRF).
- **Frontend:** React, Vite y TypeScript.
- **Base de datos:** PostgreSQL.
- **Estilos:** Tailwind CSS.

## Organización del repositorio

```text
README.md
CONTRIBUTING.md
.github/
  ISSUE_TEMPLATE/
    historia_usuario.md
    tarea.md
    error.md
  pull_request_template.md
docs/
  planificacion/
    primer-crud.md
```

Daniel define la estructura técnica del programa en [T-03](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/4). Los documentos de seguimiento y entrega se incorporan conforme haya acuerdos y resultados que registrar.

## Equipo

| Integrante | Responsabilidad |
|---|---|
| CAMARGO HILACHOQUE, ROMINA GIULIANA | Analista de Odoo, investigadora tecnológica y DevOps; preparación de entornos de desarrollo y pruebas, automatización de la ejecución y el despliegue. |
| GUILLEN VALCARCEL, DANIEL JOSUE | Arquitecto de software; estructura técnica, comunicación entre componentes, integración y guía de implementación con las tecnologías acordadas. |
| HATCHES CURO, JOSÉ LEÓN ENRIQUE | Scrum Master, repositorio y seguimiento del trabajo. |
| LUQUE GUEVARA, FERNANDO GERSON | Backend, diccionario de datos y diagrama ER; implementación de modelos, migraciones, validaciones y servicios mediante APIs. |
| MENGOA VALERIANO, BRIGITTE NOELIA | Investigación y apoyo con IA y patrones de diseño; análisis de alternativas y documentación de patrones con ejemplos para orientar su aplicación en el código. |
| MOROCCO SAICO, JOSÉ MANUEL | Frontend y bocetos. |
| SOLSOL CHOQUE, FERNANDO RAFAEL | Product Owner, historias de usuario, criterios de aceptación y aceptación funcional. |
| VELAZQUE QUISPE, FLOR DE LIZ | QA, pruebas y verificación de correcciones. |

## Historias de usuario y tareas

El primer incremento se organiza mediante **HU-01: gestionar las obligaciones de Cuentas por Pagar**, desglosada en **T-01 a T-26**. La historia enlaza todas las tareas; sus títulos indican el rol y sus descripciones identifican al responsable y el entregable.

El Project mantiene los estados: **Pendiente, En proceso, Bloqueado, En revisión y Terminado**. La tabla de planificación describe el trabajo y sus dependencias; no duplica los estados del tablero.

## Cómo participar

1. Revisar el issue asignado y sus dependencias.
2. Crear la rama de la tarea desde `main` actualizado.
3. Realizar cambios y commits concretos con la cuenta del integrante.
4. Abrir un pull request, enlazar el issue y registrar las comprobaciones.
5. Solicitar revisión y atender observaciones.
6. Integrar la entrega revisada y actualizar el tablero.

La [guía de colaboración](CONTRIBUTING.md) incluye ejemplos de ramas, commits y avisos de revisión. La HU se cierra después de las pruebas y la aceptación funcional del Product Owner.
