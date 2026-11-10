# PorAquí — Wiki para ClickUp

**Empresa:** NextWare  
**Producto:** PorAquí  
**Versión de documentación:** 0.1 (borradores)  
**Fecha:** 31 de octubre de 2026

## Cómo utilizar este paquete
1. Crear una sección de **Docs/Wiki** dentro de la carpeta de proyecto PorAquí en ClickUp.
2. Copiar cada archivo Markdown a un documento ClickUp, respetando el prefijo numérico.
3. Asignar una persona responsable y revisar en equipo; marcar **Aprobado** solo cuando realmente exista acuerdo.
4. Para cada funcionalidad, vincular tareas con el requisito (RF-001, etc.) y reglas (RN-001, etc.).
5. Conservar esta documentación versionada junto al repositorio (opcional), actualizando ambos si se decide mantener dos copias.

**Importante:** Esto es documentación y decisiones arquitectónicas, no evidencia de que PorAquí ya esté implementado. ADR-006 selecciona Next.js + NestJS para frontend/API; no se han elegido proveedores gestionados, comprado dominio ni concluido un estudio comercial.

## Tabla de contenidos

### Producto (lectura obligatoria)
- [00 Visión general](00_vision_general.md)
- [01 Alcance y requisitos del MVP](01_alcance_requisitos_mvp.md)
- [02 Reglas de negocio](02_reglas_negocio.md)
- [03 Roles y permisos](03_roles_permisos.md)
- [04 Flujos de usuario](04_flujos_usuario.md)
- [19 Matriz de actores, permisos y flujos](19_matriz_actores_permisos_flujos.md)

### Técnica
- [05 Arquitectura](05_arquitectura.md)
- [06 Modelo de datos](06_modelo_datos.md)
- [07 API](07_contratos_api.md)
- [08 Instalación](08_guia_instalacion.md)
- [09 Estándares](09_estandares_desarrollo.md)
- [10 Seguridad y despliegue](10_seguridad_despliegue.md)
- [11 Pruebas y calidad](11_pruebas_calidad.md)

### Equipo y negocio
- [12 Roadmap](12_roadmap.md)
- [13 Colaboración](13_colaboracion.md)
- [14 ADR](14_registro_decisiones_adr.md)
- [15 Plan de negocio](15_plan_negocio_monetizacion.md)
- [16 Operación de comerciantes](16_operacion_comerciantes.md)
- [17 Datos y privacidad](17_datos_privacidad.md)
- [18 Métricas y validación](18_metricas_validacion.md)

## Orden recomendado de revisión
**Primera reunión:** 00 → 01 → 02 → 03 → 04.  
**Segunda reunión:** 05 → 06 → 07 → 08 → 09.  
**Antes del primer despliegue:** 10 → 11.  
**Seguimiento continuo:** 12–18.

## Notas importantes
- «Catálogos gratuitos e ilimitados» se refiere al **modelo comercial**: no se cobra por cantidad de productos. La infraestructura requiere validaciones y controles de abuso.
- PorAquí permite buscar sin registro. El alta del comercio **no es automática**: contacto por WhatsApp o visita presencial, verificación por NextWare e invitación.
- Las calificaciones, anuncios automatizados, POS, mandaditos y SSO multiplataforma **no pertenecen al MVP**.
- Los ejemplos de APIs y diagramas son conceptuales hasta ratificar arquitectura.
- La evaluación documental de ADR-006 seleccionó arquitectura frontend/API, pero no equivale a elegir proveedores ni a implementar prototipos; asuntos abiertos están en 05, 14 y `DECISIONES_PENDIENTES.md`.
- Los datos legales deben validarse con profesional competente antes de publicar el servicio.
