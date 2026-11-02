# Backend

Contendrá el servidor del módulo: proyecto Django con Django REST Framework (modelos, migraciones, serializers, vistas y rutas), la documentación Swagger con drf-spectacular y las pruebas con pytest.

- **Responsable:** Fernando Gerson Luque Guevara (Backend).
- **Tareas:** [T-11](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/12) (proyecto y PostgreSQL), [T-12](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/13) (modelos y migraciones) y [T-16](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/17) (servicios del CRUD y pruebas).

La carpeta permanece vacía hasta T-11. Ver la [guía de implementación](../docs/arquitectura/GUIA_IMPLEMENTACION.md).

## Estructura prevista

Árbol orientativo; los archivos se crean en T-11 y T-12.

```text
backend/
  manage.py
  requirements.txt
  .env.example
  config/                 configuración del proyecto (settings, urls raíz)
  cuentas_por_pagar/      app del módulo
    models.py             tablas y restricciones (Meta.constraints)
    migrations/
    serializers.py        validación de datos de entrada y salida
    views.py              endpoints de la API
    urls.py               rutas bajo /api/
    admin.py              revisión de datos en Django Admin
    tests/
```

El responsable de cada tarea puede ajustar los nombres al crear el proyecto, siempre que respete la separación de capas. La explicación de cada elemento está en la [guía de implementación](../docs/arquitectura/GUIA_IMPLEMENTACION.md#estructura-prevista-de-backend-y-frontend).
