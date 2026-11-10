# 07. Contratos de API

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Backend / arquitectura  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** No es una decisión aprobada hasta que el equipo la valide y actualice el estado.

## Estado
**Borrador de contrato, no endpoints desplegados.** Ajustar rutas, payloads y seguridad después de aprobar arquitectura y modelo de datos. Publicar una especificación OpenAPI como fuente técnica de verdad cuando comience la implementación.

## Convenciones propuestas
Base lógica `/api/v1`; JSON UTF-8; fechas ISO 8601; identificadores opacos; paginación con cursor o equivalente; filtros tipados; errores consistentes; idempotencia para operaciones sensibles. Versionar contratos y documentar cambios incompatibles.

## Rutas públicas sugeridas
| Método | Ruta | Función | Autenticación |
|---|---|---|---|
| GET | `/search?q=&category=&locality=` | Buscar establecimientos, productos y servicios | No |
| GET | `/businesses/{slug}` | Consultar perfil público | No |
| GET | `/businesses/{slug}/items` | Catálogo público paginado | No |
| GET | `/items/{id}` | Consultar ítem publicado | No |
| POST | `/reports` | Crear reporte; con controles antiabuso | Por definir |
| POST | `/events/contact` | Registrar interacción mínima de contacto | No, antiabuso |

## Rutas privadas de comerciante sugeridas
| Método | Ruta | Acción |
|---|---|---|
| GET | `/me/businesses` | Mis comercios autorizados |
| PATCH | `/merchant/businesses/{id}` | Editar datos propios |
| POST | `/merchant/businesses/{id}/items` | Crear artículo/servicio |
| PATCH | `/merchant/items/{id}` | Editar artículo/servicio |
| POST | `/merchant/items/{id}/media` | Solicitar subida autorizada |
| POST | `/merchant/businesses/{id}/confirm` | Confirmar vigencia |
| GET | `/merchant/businesses/{id}/reports` | Ver reportes propios permitidos |

## Rutas administrativas sugeridas
| Método | Ruta | Acción |
|---|---|---|
| POST | `/admin/businesses` | Crear borrador desde contacto/visita |
| POST | `/admin/businesses/{id}/verify` | Aprobar/rechazar con motivo |
| POST | `/admin/invitations` | Emitir invitación de un solo uso |
| GET | `/admin/reports` | Cola de reportes |
| POST | `/admin/reports/{id}/resolve` | Resolver y auditar |

## Ejemplo orientativo de respuesta de búsqueda
```json
{
  "query": "bateria para moto",
  "results": [
    {
      "type": "catalog_item",
      "id": "item_example",
      "name": "Batería para motocicleta",
      "business": {"id": "biz_example", "name": "Negocio de ejemplo"},
      "availability": "unknown",
      "location": null
    }
  ],
  "next_cursor": null
}
```
*Ejemplo sintético; ningún comercio real está representado.*

## Respuestas de error sugeridas
```json
{
  "error": {
    "code": "FORBIDDEN_RESOURCE",
    "message": "No tienes permiso para modificar este recurso.",
    "request_id": "req_example"
  }
}
```
No devolver trazas internas, tokens ni detalles de otros negocios.

## Reglas transversales
Autorización servidor/RLS; límites de tasa; sanitización y validación; protección CSRF según arquitectura; uploads firmados y caducidad; evitar N+1; auditoría administrativa; probar paginación y filtros.

## API futura de otros SaaS
Nunca conectar un POS compartiendo credenciales de BD. Diseñar API autorizada, scopes y webhooks idempotentes solo cuando se implemente integración, con consentimiento y contratos independientes.

## Pendientes
Mecanismo auth, formato final de `q` y sinónimos, estrategia de paginación, errores y códigos definitivos, estados reportables y diseño OpenAPI generado.
