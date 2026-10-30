# Guía de colaboración

Esta guía organiza el trabajo del equipo de Cuentas por Pagar en su repositorio. La integración con el repositorio común del ERP se coordinará entre equipos.

- [Tablero del primer CRUD](https://github.com/users/LeonHatches/projects/1).
- [Planificación y flujo](docs/planificacion/primer-crud.md).
- [Historia de usuario HU-01](https://github.com/LeonHatches/fsi-erp-cuentas-por-pagar/issues/1).

## 1. Elegir una tarea

Revisar el issue existente antes de abrir otro. Confirmar responsable, entregable, dependencias y persona que revisará el trabajo. Colocar la tarea en **En proceso / In progress** al comenzar.

Los códigos HU-01 y T-01 identifican el trabajo; el número de GitHub identifica el issue. Por ejemplo, T-23 corresponde al issue #24.

## 2. Crear una rama

Cada integrante crea una rama por tarea desde `main` actualizado. La rama sugerida figura en el issue. Antes de cambiar de rama, revisar `git status`; si hay cambios pendientes, resolver cómo conservarlos antes de continuar.

Ejemplo para T-23, con el directorio de trabajo limpio:

```bash
git switch main
git pull --ff-only origin main
git switch -c docs/t-23-colaboracion
```

| Prefijo | Uso |
|---|---|
| `docs/` | Planificación, arquitectura, bocetos y documentación. |
| `feat/` | Funcionalidades y componentes del programa. |
| `test/` | Casos, pruebas y resultados. |
| `chore/` | Configuración, entornos y plantillas. |
| `ci/` | Automatización de verificaciones. |
| `fix/` | Corrección de un defecto identificado. |

Formato: `prefijo/t-NN-descripcion`. Para defectos nuevos, se puede utilizar `fix/issue-N-descripcion`, usando el número real del issue.

El Scrum Master documenta este flujo. Arquitectura define la estructura técnica de carpetas en T-03; cada integrante implementa su tarea en la rama correspondiente.

## 3. Registrar cambios

Realizar commits por cambios coherentes y comprobables. Los documentos, bocetos, configuraciones y casos de prueba también son aportes versionables. Revisar los archivos antes de incorporarlos; no incluir entornos virtuales, dependencias descargadas ni credenciales.

Ejemplo para T-23:

```bash
git diff
git add CONTRIBUTING.md
git diff --cached
git commit -m "docs: documentar flujo de colaboracion (#24)"
git push -u origin docs/t-23-colaboracion
```

Cada integrante utiliza su propia cuenta y registra sus aportes reales. Crear issues, mover tarjetas o aprobar una revisión deja actividad en GitHub, pero no genera commits. La cantidad de commits no reemplaza la evidencia del trabajo realizado.
