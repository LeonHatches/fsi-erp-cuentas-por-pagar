# Base de datos

Contiene referencias SQL de las migraciones y datos de prueba para PostgreSQL. La estructura se define en los modelos de Django y se aplica mediante sus migraciones.

| Script | Contenido | Responsable | Tarea |
|---|---|---|---|
| `01_estructura.sql` | SQL de una migración específica obtenido con `sqlmigrate`, identificado por aplicación y migración. Referencia documental; no se edita a mano ni sustituye a `migrate`. | Fernando Gerson Luque Guevara (Backend) | [T-12](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/13) |
| `02_datos_prueba.sql` | Registros de ejemplo, escritos aparte. | Flor de Liz Velazque Quispe (QA) | [T-08](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/9) |

Los cambios de estructura se realizan en los modelos. `python manage.py makemigrations` genera las migraciones y `python manage.py migrate` las aplica y registra en la base de datos. Los modelos y las migraciones se versionan y revisan mediante pull request.

`python manage.py sqlmigrate <app> <migracion>` muestra únicamente el SQL de la migración indicada. Su salida no es un esquema completo acumulado del proyecto y no se utiliza para crear o actualizar la base manualmente. La referencia SQL se actualiza desde las migraciones cuando corresponde.

Los datos de prueba se cargan sobre una base de pruebas con las migraciones aplicadas. No incluyen credenciales ni datos personales reales.

Los scripts se incorporan cuando existan. Ver la [guía de implementación](../docs/arquitectura/GUIA_IMPLEMENTACION.md).
