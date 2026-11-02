# Base de datos

Reúne los scripts SQL de PostgreSQL. La estructura de las tablas se define en los modelos de Django, no aquí.

| Script | Contenido | Responsable | Tarea |
|---|---|---|---|
| `01_estructura.sql` | Estructura de las tablas, **generada** con `sqlmigrate`; no se edita a mano. | Fernando Gerson Luque Guevara (Backend) | [T-12](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/13) |
| `02_datos_prueba.sql` | Registros de ejemplo, escritos aparte. | Flor de Liz Velazque Quispe (QA) | [T-08](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/9) |

Si cambia la estructura, se modifican los modelos y se vuelve a generar el script mediante pull request. Los datos de prueba no incluyen credenciales ni datos personales reales.

Los scripts se incorporan cuando existan. Ver la [guía de implementación](../docs/arquitectura/GUIA_IMPLEMENTACION.md).
