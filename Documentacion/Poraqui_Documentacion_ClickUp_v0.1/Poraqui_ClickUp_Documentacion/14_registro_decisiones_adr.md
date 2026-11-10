# 14. Registro de decisiones arquitectónicas y de producto

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Líder técnico  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** No es una decisión aprobada hasta que el equipo la valide y actualice el estado.

## Propósito
Conservar **por qué** se eligió una solución y qué consecuencias trae. Una decisión puede estar: `Propuesta`, `Aceptada`, `Reemplazada`, `Descartada`.

## Plantilla ADR
```markdown
# ADR-XXX — Título
- Fecha:
- Estado:
- Responsables:
- Contexto:
- Opciones consideradas:
- Decisión:
- Justificación:
- Consecuencias positivas:
- Riesgos y compensaciones:
- Plan de reversión:
- Documentos/tareas afectados:
```

## Decisiones de negocio ya expresadas por los fundadores (requieren formalización)
### ADR-001 — Registro manual y verificado
**Estado:** Aceptada como política inicial de producto.  
**Decisión:** el equipo visita negocios o atiende por WhatsApp, verifica, autoriza y crea invitaciones.  
**Motivo:** confianza y control de calidad.  
**Consecuencia:** crecimiento dependiente de atención humana; reconsiderar al escalar.

### ADR-002 — Catálogo gratuito sin límite comercial de artículos
**Estado:** Aceptada como modelo de producto.  
**Motivo:** captar oferta amplia, permitir enlaces y evitar barrera económica.  
**Consecuencia:** habrá que proteger costos de almacenamiento/abuso sin convertir límites técnicos en un paywall.

### ADR-003 — Publicidad posterior, claramente identificada
**Estado:** Aceptada como orientación comercial.  
**Decisión:** no imponer pago para aparecer; patrocinio opcional futuro identificado.  
**Riesgo:** monetización depende de audiencia y resultados medibles.

### ADR-004 — Productos SaaS independientes
**Estado:** Aceptada como visión corporativa.  
**Decisión:** sistemas de gestión de NextWare se comercializan independientemente y pueden integrarse mediante APIs cuando exista consentimiento y soporte técnico.  
**Consecuencia:** evitar mezclar bases privadas o crear acoplamiento prematuro.

### ADR-005 — Reportes sin baja automática
**Estado:** Aceptada como regla de calidad propuesta.  
**Motivo:** impedir reportes falsos y daños injustificados a establecimientos.  
**Consecuencia:** requiere cola de revisión humana.

## ADR pendientes de crear y aprobar
- ADR-007 Motor de búsqueda, normalización y estrategia de sinónimos.
- ADR-008 Sistema de autenticación, cuentas e invitaciones.
- ADR-009 Mapas, atribuciones y geocodificación.
- ADR-010 Almacenamiento y optimización de fotografías.
- ADR-011 Estrategia de analítica y consentimiento.
- ADR-012 Infraestructura, respaldos y plan de migración.

### ADR-006 — Frontend y backend independientes con TypeScript
**Estado:** Aceptada por el usuario para frontend/API; proveedores gestionados y parámetros operativos siguen pendientes de decisión.
**Alcance de decisión:** seleccionar arquitectura base y dejar explícitos los proveedores aún abiertos. La tarea no autoriza crear repositorio ni producto funcional; validaciones de implementación y operación requieren autorización/tarea posterior.
**Contexto:** PorAquí requiere una experiencia pública móvil e indexable, portada de marketplace, búsqueda de negocios/productos/servicios, panel privado, mapas, calificaciones públicas con controles contra abuso y moderación. El MVP debe ser la primera fase de un producto completo, con bajo costo inicial y evitando acoplar reglas esenciales a un proveedor. La arquitectura fue elegida por el usuario tras comparación documental; proveedores y operación se decidirán por separado.
**Opciones registradas históricamente:** Astro con backend separado; Next.js con lógica de servidor integrada; Next.js frontend con API independiente en NestJS; frontend separado con API Python/FastAPI. FastAPI no forma parte de la comparación acotada de este corte; se retiene sin prioridad mientras no aparezca una incertidumbre concreta que lo justifique.
**Decisión:** usar **Next.js + TypeScript** para frontend y **NestJS + TypeScript** como API independiente. No adoptar microservicios para el MVP. El usuario descartó Next.js modular con backend integrado y seleccionó esta opción tras comparar con Astro + API. **Recomendación de datos:** PostgreSQL con PostGIS por el modelo relacional y las consultas geográficas; confirmar esta parte con el equipo. Proveedor de Postgres, hosting, identidad, mapas y almacenamiento no seleccionados. Mantener migraciones, esquema y reglas de negocio bajo control del proyecto, con adaptadores que faciliten exportación y salida.
**Alternativas acotadas para esta evaluación:** Next.js + NestJS y Astro + API pequeña. FastAPI se conserva como alternativa futura posible, pero no se compara en este corte porque no hay una necesidad concreta de añadir otra opción ni se ha definido una comparación equivalente.
**Justificación:** las páginas públicas indexables y dinámicas, la experiencia móvil, las membresías multi-negocio y el panel de escritura/moderación son necesidades del MVP. Entre las dos opciones separadas, Next.js + NestJS encaja con SSR para fichas dinámicas y un frontend React/TypeScript junto a una API modular explícita. Astro también admite SSR y endpoints, pero su ventaja de publicar contenido con hidratación mínima es menos decisiva aquí que el ecosistema de UI para un panel móvil central. Esto favorece la opción por ajuste conceptual, no prueba su costo ni superioridad práctica. PostgreSQL encaja con relaciones, membresías, auditoría y transacciones; PostGIS aporta tipos geográficos e índices para búsquedas por proximidad del mapa. La extensión y el proveedor requieren validación de compatibilidad/exportación.
**Consecuencias positivas:** una API Nest explícita ofrece contrato independiente para clientes futuros; el frontend Next.js maneja las páginas dinámicas indexables y la interacción de panel con el mismo ecosistema TypeScript. Los adaptadores y el dominio separado mantienen la portabilidad.
**Riesgos y compensaciones:** una API separada implica mayor configuración y despliegue que una aplicación integrada; cualquier opción requiere autorización en cada operación del servidor, pruebas de aislamiento entre negocios, validación de entradas, gestión de secretos, límites contra abuso y política de caché que excluya datos privados. La separación de procesos no garantiza seguridad.
**Plan de salida/reversión:** exportar esquema y datos PostgreSQL mediante formatos/herramientas estándar; guardar objetos con IDs/rutas neutrales y exportarlos junto con metadatos; documentar versiones, integridad, restauración y configuración sin secretos. Mantener contratos versionables, migraciones SQL portables y adaptadores para sustituir hosting, identidad y objetos. El procedimiento y una restauración real aún deben probarse antes de producción.
**Documentos/tareas afectados:** 00, 01, 02, 05, 06, 07, 08, 10, 14; las calificaciones públicas forman parte del MVP. Antes de producción, resolver proveedores y autorizar validaciones prácticas de términos comerciales/costos, capacidades, backup/restauración y flujo de autenticación. La política de calificaciones está definida en 01, 02, 06 y 17; umbrales automáticos se calibran con datos del piloto.

**Resultado de evaluación documental (31-10-2026):** el usuario aceptó Next.js + NestJS frente a Astro + API por su ajuste razonado a rutas dinámicas indexables y panel con API explícita, reconociendo el costo de operar dos aplicaciones. La comparación no es medición empírica. No se seleccionaron proveedores gestionados ni se validaron costos de piloto, aislamiento funcional o restauración práctica. El diagrama de contexto/componentes, límites de confianza, separación del dominio y controles propuestos están en 05 y 10. La tarea de validación arquitectónica queda cubierta documentalmente; selección de proveedores y pruebas operativas corresponden a decisiones/tareas posteriores. No se autoriza implementación en esta tarea.

## ADR pendientes de crear y aprobar
- ADR-007 Motor de búsqueda, normalización y estrategia de sinónimos.
- ADR-008 Sistema de autenticación, cuentas e invitaciones.
- ADR-009 Mapas, atribuciones y geocodificación.
- ADR-010 Almacenamiento y optimización de fotografías.
- ADR-011 Estrategia de analítica y consentimiento.
- ADR-012 Infraestructura, respaldos y plan de migración.

## Regla
Un ADR documenta una decisión real, no reemplaza requisitos. No marcar `Aceptada` una opción tecnológica únicamente porque fue sugerida en una conversación.
