# 🪵 Estrategia de Ramas

## Repos de **código**
- `main`: estable (deployable)
- `develop`: integración
- `release/CRES<n>HU-<n>`: **una rama por historia** (p. ej. `release/CRES<n>HU-<n>`)
- `hotfix/<slug>`: parches urgentes

**Flujo por HU**
1. Crear `release/release/CRES<n>HU-<n>` desde `develop`.
2. Commits pequeños y trazables (ver convención).
3. PR hacia `develop` con checklist de aceptación.
4. Merge a `develop` al cerrar la HU.
5. Cierre de **semana (épica)**: `develop` → `main` y tag `semana-<n>`.

## Repo **credi-docs**
- `main`: documentación publicada.
- `release/CRES<n>-<tema>`: rama de trabajo de la épica.
  - Ejemplo inicial: `release/CRES0-documentacion`
