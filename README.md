# ERP FSI — Cuentas por Pagar
Proyecto académico de la Escuela Profesional de Ingeniería de Sistemas de la Universidad Nacional de San Agustín de Arequipa, desarrollado para el curso de Fundamentos de Sistemas de Información.

Este repositorio reúne el trabajo del módulo de Cuentas por Pagar, perteneciente a la Tribu de Egresos. Su código se integrará posteriormente al repositorio común del ERP, según la coordinación entre equipos.

## Objetivo

El objetivo del módulo de Cuentas por Pagar es gestionar y controlar las deudas que la empresa mantiene con sus proveedores, desde que se registra el comprobante de compra hasta que se realiza el pago. Para ello, el módulo debe identificar correctamente al proveedor, el tipo de comprobante, la moneda, el banco, el medio de pago y la clasificación de la operación, además de relacionar la deuda con las cuentas contables correspondientes.

## Primera implementación

El bloque 3 contempla implementar la base de datos y un programa sencillo para comprobar el siguiente recorrido:

1. Registrar el comprobante y la obligación de un proveedor.
2. Consultar las obligaciones y sus saldos pendientes.
3. Registrar un pago y comprobar la actualización del saldo.

Las tecnologías y las instrucciones de ejecución se definirán en la guía de implementación.

## Organización

```text
README.md

```

## Equipo

| Integrante | Responsabilidad |
|---|---|
| CAMARGO HILACHOQUE, ROMINA GIULIANA | Analista de Odoo e investigadora; preparación de scripts de base de datos para esta implementación. |
| GUILLEN VALCARCEL, DANIEL JOSUE | Arquitectura y guía de implementación. |
| HATCHES CURO, JOSÉ LEÓN ENRIQUE | Scrum Master, repositorio y seguimiento del trabajo. |
| LUQUE GUEVARA, FERNANDO GERSON | Backend y revisión técnica de la base de datos. |
| MENGOA VALERIANO, BRIGITTE NOELIA | Investigación y apoyo con IA. |
| MOROCCO SAICO, JOSÉ MANUEL | Frontend y bocetos. |
| SOLSOL CHOQUE, FERNANDO RAFAEL | Product Owner, historias de usuario y aceptación funcional. |
| VELAZQUE QUISPE, FLOR DE LIZ | QA, pruebas y verificación de correcciones. |

## Historias de usuario y tareas

Las historias de usuario se registran como issues con la etiqueta `historia-usuario`:

- **HU-01:** Registrar una obligación.
- **HU-02:** Consultar obligaciones y saldos pendientes.
- **HU-03:** Registrar un pago y actualizar el saldo.

Las actividades de arquitectura, scripts, Backend, Frontend y pruebas se registran como issues con la etiqueta `tarea-tecnica` y se relacionan con las historias correspondientes.

El tablero de GitHub Projects organiza los issues en: **Pendiente → En proceso → En revisión → Terminado**.

## Flujo de colaboración

1. Seleccionar un issue y confirmar quién lo realizará y quién lo revisará.
2. Crear la rama de trabajo desde la versión actualizada de `main`.
3. Registrar cambios concretos mediante commits descriptivos.
4. Abrir un Pull Request hacia `main`, indicando el issue relacionado, los cambios y cómo se comprobaron.
5. Mover la tarea a **En revisión** y avisar al revisor con el enlace del Pull Request.
6. Atender las observaciones en la misma rama y agregar los commits de corrección.
7. Incorporar los cambios revisados a `main` y actualizar el estado de la tarea.

Las tareas técnicas se cierran al completar y revisar su entrega. Las historias de usuario se cierran cuando sus criterios de aceptación estén comprobados y el Product Owner acepte el resultado.

## Ramas

| Actividad | Rama sugerida |
|---|---|
| Preparación del repositorio | `chore/estructura-inicial` |
| Arquitectura y guía | `docs/arquitectura` |
| Base de datos | `feat/base-datos` |
| Backend | `feat/backend` |
| Frontend | `feat/frontend` |
| Pruebas | `test/flujo-principal` |

## Commits

Cada commit describe un cambio concreto. Ejemplos:

```text
docs: definir el flujo del programa
feat: crear las tablas de obligaciones y pagos
feat: conectar la interfaz con los servicios
test: comprobar la actualización del saldo
fix: impedir pagos superiores al saldo pendiente
```
