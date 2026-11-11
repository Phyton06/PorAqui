# 01. Alcance y requisitos del MVP

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Liderazgo de producto / técnico  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** Salvo los acuerdos de equipo expresamente ratificados, este documento conserva requisitos en borrador. Las políticas de calificaciones y ranking están en `20_politica_calificaciones_moderacion.md` y `21_politica_ranking_destacados_analitica.md`; los detalles legales/operativos siguen pendientes.

## Objetivo de esta versión
Entregar una **primera versión pública utilizable** de PorAquí para validar, en Santiago Ixcuintla, si comercios y consumidores encuentran valor en un catálogo centralizado y una búsqueda local. El calendario de estadía propuesto es enero–abril de 2027; alcance y fechas son **propuesta**, sujetos a revisión del equipo y universidad.

## Definición de terminado del MVP
La versión estará lista para piloto cuando un negocio validado pueda publicar su perfil y catálogo y un visitante pueda localizarlo por nombre, producto o servicio, consultar su ficha y contactarlo; el equipo debe poder moderar registros y reportes básicos. Se exige seguridad y trazabilidad mínimas, no solo una demostración visual.

## Requisitos funcionales de prioridad P0
| ID | Requisito | Criterio mínimo de aceptación |
|---|---|---|
| RF-001 | Buscar por texto | Coincidencias por negocio, categoría, producto y servicio; mensaje útil sin resultados. |
| RF-002 | Mostrar lista y mapa | Misma oferta relevante en ambas vistas; ubicación solo cuando se cuenta con coordenadas confirmadas. |
| RF-003 | Ficha pública de negocio | Nombre, giro, ubicación, contacto, horarios cuando existan, galería y catálogo. |
| RF-004 | Catálogo gratuito | Alta/edición/baja lógica de productos/servicios, sin tope comercial de artículos; imágenes opcionales y precio opcional. |
| RF-005 | Enlaces compartibles | URL estable de negocio y de producto/servicio, con metadatos de vista previa. |
| RF-006 | Solicitar alta por WhatsApp | Botón abre conversación con cuenta oficial y texto prellenado; no aprueba automáticamente. |
| RF-007 | Validación administrativa | Admin registra solicitudes, evidencia, verificación, aprobación/rechazo motivado y trazabilidad. |
| RF-008 | Invitación de cuenta | Activación segura por enlace temporal y de un solo uso; nunca enviar contraseñas compartidas. |
| RF-009 | Panel de comerciante | Solo puede gestionar sus negocios y catálogos autorizados. |
| RF-010 | Contacto | Botones de WhatsApp, llamada y navegación cuando estén configurados. |
| RF-011 | Reporte básico | Cliente informa posible cierre, agotado, ya no se vende o información incorrecta; queda pendiente de revisión. |
| RF-012 | Moderación de reportes | Admin puede contactar al propietario, resolver y dejar historial. Ningún reporte aislado despublica automáticamente. |
| RF-013 | Confirmar vigencia | Comerciante confirma «todo sigue igual» o edita su información; queda fecha de revisión. |
| RF-014 | Analítica mínima del MVP | Medir de forma mínima y agregada búsquedas, resultados, vistas, impresiones y clics de contacto, minimizando datos personales. Las recomendaciones usan solo la consulta/categoría actual; no crear perfiles persistentes ni inferir compras individuales. Definir finalidad, aviso/base aplicable y retención antes de activar analítica; véase `21_politica_ranking_destacados_analitica.md`. |
| RF-019 | Portada, ranking orgánico y destacados | Priorizar coincidencia directa, después cobertura/calidad del dato; ubicación confirmada solo para distancia/ruta, no como desempate local por defecto; calificaciones visibles como señal secundaria. Permitir rotación por impresiones agregadas entre candidatos comparables y selección manual elegible, con motivo/origen/periodo registrados y separación de orgánicos. Pesos y ventanas se calibran en el piloto; véase `21_politica_ranking_destacados_analitica.md`. |
| RF-020 | Calificaciones públicas | **Elegibilidad ratificada por el líder del proyecto:** solo una cuenta con contacto verificado puede calificar. El borrador propone 1–5 estrellas, una calificación vigente por cuenta y negocio, editable, sin comentarios ni respuestas públicas; confirmar esos detalles en equipo antes de implementarlos. Mostrar promedio y cantidad de calificaciones visibles. Véase `20_politica_calificaciones_moderacion.md`. |
| RF-021 | Protección contra review bombing | Los reportes/señales pasan a revisión humana; no se pausan nuevas calificaciones automáticamente por volumen ni se borran reseñas o despublica el negocio. Tras revisión humana, un moderador autorizado puede ocultar provisionalmente una calificación individual, avisar al autor en privado y admitir apelación dentro de 30 días; plazo sujeto a revisión legal. Véase `20_politica_calificaciones_moderacion.md`. |

## Requisitos P1 si el P0 está estable
| ID | Requisito | Criterio mínimo |
|---|---|---|
| RF-015 | Publicaciones por plantilla | Seleccionar elementos del catálogo, generar texto y una imagen promocional sencilla con enlace compartible. |
| RF-016 | Recordatorios básicos | Aviso periódico configurable para confirmar vigencia; evitar mensajes repetitivos. |
| RF-017 | Filtros adicionales | Filtrar por categoría, localidad y negocios con datos verificados. |
| RF-018 | Mejoras SEO | URLs semánticas, sitemap, metadatos sociales y datos estructurados pertinentes. |

## Requisitos no funcionales
- **Móvil primero:** la búsqueda, los catálogos y el panel deben ser utilizables desde teléfono.
- **Accesibilidad:** navegación con teclado, etiquetas, contraste y alternativas textuales para imágenes relevantes.
- **Rendimiento:** imágenes optimizadas, carga diferida, caché y seguimiento de desempeño; los objetivos numéricos se fijarán mediante mediciones.
- **Seguridad:** validación de entradas, autorización por recurso, protección contra spam, registros de auditoría y manejo de secretos.
- **Disponibilidad y recuperación:** backups exportables y restauración ensayada, incluso usando planes gratuitos.
- **SEO:** fichas públicas indexables cuando el comerciante autorice su publicación; evitar indexar paneles o contenido privado.
- **Bajo costo:** elegir infraestructura gratuita solo si permite uso comercial y no pone en riesgo datos o continuidad.

## Exclusiones explícitas
Pasarelas de pago, facturación CFDI, stock en tiempo real, reportes con IA, ranking pagado avanzado, múltiples ciudades, delivery, taxistas y SSO entre SaaS. No implementarlas «aprovechando que ya estamos» sin un cambio de alcance aprobado. Las calificaciones públicas sí forman parte del MVP; la publicidad pagada queda para una etapa posterior.

## Historias de usuario iniciales
- **HU-01:** Como visitante, quiero encontrar dónde venden un producto para contactar opciones locales.
- **HU-02:** Como visitante, quiero abrir un enlace del menú de un restaurante para consultarlo sin iniciar sesión.
- **HU-03:** Como comerciante autorizado, quiero actualizar el catálogo desde el celular para que mi enlace público refleje cambios.
- **HU-04:** Como administrador, quiero verificar la legitimidad de la solicitud para impedir fichas apócrifas.
- **HU-05:** Como visitante, quiero reportar un producto agotado sin que desaparezca automáticamente del catálogo.

## Riesgos para el MVP
Cobertura insuficiente, calidad del catálogo, abuso de reportes, costos de operaciones, necesidad de soporte manual, búsquedas imprecisas y dependencia de plataformas externas.

## Control del alcance
Toda función nueva necesita: problema concreto, beneficiario, criterio de aceptación, costo estimado y decisión explícita del líder técnico/producto. Registrar cambios en [14 ADR](14_registro_decisiones_adr.md) y tareas de ClickUp.

## Pendiente de decidir
Estrategia de autenticación final; proveedor de mapas y licencias; stack final; definición de búsqueda por sinónimos; diseño de aprobaciones; objetivos cuantitativos de rendimiento.
