# Frontend

Contendrá la interfaz del módulo: proyecto React con Vite y TypeScript, estilos con Tailwind CSS y las pantallas del CRUD, que consumen la API del backend.

- **Responsable:** José Manuel Morocco Saico (Frontend).
- **Tareas:** [T-14](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/15) (proyecto y pantallas) y [T-17](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/18) (conexión con la API).

La carpeta permanece vacía hasta T-14. Ver la [guía de implementación](../docs/arquitectura/GUIA_IMPLEMENTACION.md).

## Estructura prevista

Árbol orientativo; los archivos se crean en T-14 y T-17.

```text
frontend/
  package.json
  vite.config.ts
  src/
    api/                  llamadas a la API (fetch)
    types/                interfaces TypeScript según el contrato de API
    components/           componentes reutilizables (formularios, tablas, mensajes)
    pages/                pantallas del CRUD de obligaciones
    App.tsx
    main.tsx              punto de entrada de React
    index.css             importación de Tailwind CSS
```

El responsable de cada tarea puede ajustar los nombres al crear el proyecto, siempre que respete la separación de capas. La explicación de cada elemento está en la [guía de implementación](../docs/arquitectura/GUIA_IMPLEMENTACION.md#estructura-prevista-de-backend-y-frontend).
