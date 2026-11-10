# 11. Plan de pruebas y calidad

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Equipo de desarrollo / QA  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** No es una decisión aprobada hasta que el equipo la valide y actualice el estado.

## Objetivo
Verificar que los flujos centrales funcionan con seguridad y que los datos públicos sean confiables; registrar defectos en ClickUp con pasos reproducibles.

## Estrategia por nivel
- **Unitarias:** reglas de disponibilidad, validación, roles, slugs, expiración de invitaciones.
- **Integración:** API + BD; permisos de membresía; subida de fotos; búsqueda indexada; resolución de reportes.
- **End-to-end:** visitante busca → abre negocio → contacta; alta admin → invitación → comerciante publica; usuario reporta → admin verifica.
- **Exploratorias:** móvil real, red lenta, navegadores, accesibilidad, errores y contenidos extensos.
- **Seguridad:** controles de autorización, inyección, archivos sospechosos, rate limits, credenciales e invitaciones vencidas.

## Casos de prueba prioritarios
| ID | Escenario | Resultado esperado |
|---|---|---|
| QA-001 | Buscar producto existente | Resultados correspondientes, sin negocios ajenos. |
| QA-002 | Buscar sin coincidencias | Estado vacío con orientación útil. |
| QA-003 | Visitar URL de negocio | Ficha pública accesible y metadatos correctos. |
| QA-004 | Visitante intenta editar catálogo | Acceso denegado. |
| QA-005 | Comerciante A edita negocio B | Acceso denegado y evento auditado. |
| QA-006 | Reportar «agotado» | Se crea reporte; artículo permanece hasta verificación. |
| QA-007 | Reportar «ya no se vende» | No se confunde con falta temporal de stock. |
| QA-008 | Invitación caducada o usada | No permite activar otra vez. |
| QA-009 | Fotografía demasiado grande o inválida | Rechazo comprensible, sin ejecución peligrosa. |
| QA-010 | Comercios sin coordenadas | Listado funcional; mapa no coloca punto inventado. |
| QA-011 | Precio ausente | Mostrar «Consultar precio» o equivalente. |
| QA-012 | Producto despublicado con link compartido | Mensaje/redirect previsto, no filtración de datos. |
| QA-013 | Cambiar slug | Enlace anterior conserva redirección según política. |
| QA-014 | Confirmar catálogo sin cambios | Se registra revisión, sin inventar existencias. |

## Criterios de salida al piloto
Sin vulnerabilidades críticas abiertas; flujos P0 completos; restauración de backup ensayada; registros coherentes; accesos multi-negocio revisados; correos de invitación operativos; mecanismos de reporte y moderación funcionando.

## Plantilla para bug
**ID / entorno / severidad / descripción / precondiciones / pasos / resultado esperado / resultado real / evidencias / impacto / responsable / resolución**.

## Métricas de calidad
Tasa de fallos de búsqueda, errores por 1,000 solicitudes, tiempos de carga reales, incidencias por negocio, reportes falsos, restauraciones fallidas y errores de autorización detectados.

## Pendientes
Framework de pruebas, matriz navegadores/dispositivos disponible, umbrales de rendimiento, criterios de severidad y estrategia de pruebas automatizadas en CI.
