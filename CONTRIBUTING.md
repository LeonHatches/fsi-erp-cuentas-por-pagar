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

## 4. Abrir un pull request

Abrir un PR de la rama de trabajo hacia `main`. Completar la plantilla con el problema o tarea, los cambios, la forma de comprobación y el revisor. Un PR reúne normalmente una tarea.

- Usar `Relacionado con #24` si la entrega es parcial o falta una revisión para cerrar el issue.
- Usar `Closes #24` únicamente cuando el PR complete T-23 y su revisión permita cerrarla al integrar en `main`.
- No utilizar `Closes #1` en un PR técnico individual: HU-01 requiere pruebas completas y validación funcional de Rafael.

Si la tarea solo produce una revisión en GitHub, enlazar ese registro desde el issue. Cuando exista un documento de revisión o resultados, versionarlo como parte del entregable correspondiente.

## 5. Solicitar y atender la revisión

Mover la tarea a **En revisión** cuando el entregable esté disponible. Avisar dentro del issue o PR con este formato:

```text
Entregable: [enlace al PR o documento]
Realizado: [cambios concretos]
Comprobación: [pasos y resultados]
Revisión solicitada a: [integrante o usuario]
Pendientes: [si existen]
```

| Aspecto | Revisión |
|---|---|
| Alcance, criterios y funcionamiento esperado | Rafael — Product Owner. |
| Estructura técnica, integración y patrones | Daniel — Arquitectura. |
| Contrato de API y comunicación entre pantallas y servicios | Fernando Gerson y José Manuel. |
| Entornos y automatización | Romina — DevOps, con quien utiliza el entorno. |
| Casos, resultados y correcciones | Flor — QA; Rafael valida los criterios funcionales. |
| Documentación de colaboración y seguimiento | Integrante disponible designado en el issue; Hatches atiende observaciones. |

Cada issue indica el revisor concreto al iniciar la tarea. El Product Owner valida el producto; las revisiones técnicas corresponden al rol pertinente. Atender observaciones en la misma rama, agregar los commits necesarios y solicitar otra revisión cuando corresponda.

## 6. Estados y cierre

| Estado | Cuándo utilizarlo |
|---|---|
| Pendiente / Todo | Aún no se inicia el trabajo. |
| En proceso / In progress | El responsable trabaja en el entregable. |
| Bloqueado | Existe un impedimento: registrar causa, dependencia y siguiente acción. |
| En revisión | El entregable está listo y se solicitó revisión. |
| Terminado / Done | La entrega está revisada y su evidencia está enlazada. |

Los estados se mantienen en el Project, sin duplicarlos en la tabla de planificación. Revisar las automatizaciones del tablero para que no den por terminada una tarea antes de cumplir sus condiciones de cierre.

Una tarea se cierra cuando su entregable y comprobación están completos. Si incluye cambios en archivos, el PR debe estar integrado. HU-01 se cierra después de las pruebas de Flor, la aceptación de Rafael y la documentación de la entrega. Las tareas continuas de seguimiento concluyen al cerrar el incremento.
