# 🧾 Convención de Commits

Formato recomendado:
```
[HU-<n>] <tipo>(<scope>): <resumen>
```
**Tipos**: `feat`, `fix`, `docs`, `test`, `refactor`, `chore`  
`scope` (opcional): HU (`CRES1HU-01`, `CRES1HU-02`, `CRES2HU-03`, etc).  
**No es necesario detallar cada cambio** en el cuerpo: mantenemos los commits **breves y descriptivos**.

### Ejemplos
```
[HU-1] feat(CRES1HU-01): exponer POST /api/v1/usuarios
[HU-1] test(CRES1HU-01): agregar tests de validación de email y salario
[HU-2] docs(CRES1HU-02): crear estado inicial PENDIENTE_REVISION
[HU-3] feat(CRES2HU-03): login con JWT y roles
[HU-4] feat(CRES2HU-04): listar solicitudes para revisión (paginación + filtros)
```
