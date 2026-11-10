# 09. Estándares de desarrollo y Git

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Líder técnico + equipo de desarrollo  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** No es una decisión aprobada hasta que el equipo la valide y actualice el estado.

## Principios
Código legible y seguro; cambios pequeños; pruebas vinculadas a reglas de negocio; revisión de pares; documentación de decisiones relevantes; no fusionar funcionalidades incompletas que rompan el MVP.

## Flujo de ramas propuesto
- `main`: versión estable/publicable.
- `feature/<id-clickup>-descripcion`: nueva funcionalidad.
- `fix/<id-clickup>-descripcion`: corrección.
- `docs/<id-clickup>-descripcion`: documentación.
- **Propuesta:** integración continua con ramas breves y PR a `main`; crear `develop` solo si existe una necesidad real y acuerdo del equipo.

## Commits
Convención propuesta: `feat(search): agregar filtro por categoría`, `fix(catalog): corregir permisos`, `docs(adr): registrar proveedor de mapas`, `test(reports): cubrir reporte duplicado`.

## Pull Requests
Cada PR incluirá: tarea de ClickUp, problema, alcance, capturas si hay UI, pruebas ejecutadas, impacto en BD/API, riesgos, notas de despliegue y checklist de seguridad/privacidad.

## Revisión de código
Revisar autorización por recurso, validación de entrada, estados vacíos/errores, accesibilidad, rendimiento, cambios en el esquema, compatibilidad API, pruebas de borde y uso de secretos. El autor no debe aprobarse a sí mismo cambios críticos en seguridad.

## Definición de listo (DoR)
Historia clara; criterios de aceptación; reglas de negocio relacionadas; diseños o flujos si aplican; dependencias identificadas; responsable asignado.

## Definición de terminado (DoD)
Código revisado y fusionado; tests pertinentes verdes; migraciones probadas; no errores críticos conocidos; documentación afectada actualizada; validación manual de flujos clave; tarea vinculada a PR.

## Calidad
Formateador y linter automatizados según stack; análisis estático; pruebas unitarias de reglas; integración en operaciones críticas; no logs con contraseñas ni datos sensibles; dependencias con versiones fijadas y actualizadas periódicamente.

## Seguridad de repositorios
No secretos `.env` en Git, dependencias y acciones con permisos mínimos, revisión de vulnerabilidades, protección de ramas, control de acceso por integrantes, rotación de credenciales comprometidas.

## Documentación y cambios
Si una PR cambia disponibilidad, publicación, permisos, estados, reglas de reporte o flujos, actualizar el documento correspondiente y crear ADR para decisiones estructurales.

## Pendientes
Lenguaje de programación definitivo, test runner, linter, convenciones por paquete y política de releases. Ratificar estas propuestas antes del inicio de sprints.
