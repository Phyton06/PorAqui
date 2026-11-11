# 17. Gobierno de datos, privacidad y moderación

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Administración + responsable de privacidad  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** Salvo acuerdos de equipo expresamente ratificados, este documento conserva reglas en borrador; los requisitos legales y operativos de privacidad siguen sujetos a validación.

## Objetivo
Diferenciar **información comercial pública** de datos personales, privados o confidenciales, y establecer controles sobre el uso de información recolectada por PorAquí.

## Clasificación de datos
| Tipo | Ejemplos | Tratamiento |
|---|---|---|
| Comercial pública autorizada | Nombre, giro, horarios, dirección, catálogo, WhatsApp comercial | Publicar con autorización del representante; permitir actualización. |
| Privada de acceso | Correo de login, identificadores de cuenta, roles, invitaciones | Acceso limitado y protección técnica. |
| Evidencia de verificación | Documentos o comunicaciones de autorización | Acceso muy restringido, minimización y plazos definidos. |
| Reportes/moderación | Descripciones de incidentes, historial, datos del reportante | Solo para resolver; antiabuso y retención documentada. |
| Analítica | Consultas, aperturas y clics | Minimización y agregación; transparencia. |
| SaaS independientes | Compras, inventario, clientes de comercios | No incorporarlos automáticamente a PorAquí; finalidades y acuerdos separados. |

## Reglas de privacidad por diseño
- Publicar solo el número/canal comercial autorizado, no el personal por defecto.
- No utilizar automáticamente ventas o historial de clientes de los POS de NextWare para anuncios personalizados.
- Minimizar datos y establecer finalidad específica, aviso de privacidad, base jurídica y mecanismos para ejercer derechos.
- No extraer masivamente contenido o datos personales de grupos de Facebook.
- Permitir corrección, despublicación y atención de solicitudes según obligaciones aplicables.
- Separar identificadores individuales de analítica agregada cuando sea viable. Para el MVP, las recomendaciones usan solo la consulta/categoría actual; no crear perfiles persistentes ni inferir compras individuales. Medir búsquedas, vistas, impresiones y clics en forma mínima y agregada. Definir finalidad, aviso/base aplicable, retención y eliminación/anonimización antes de activar analítica. Véase `21_politica_ranking_destacados_analitica.md`.

## Moderación
Reportes de contenido indebido, datos incorrectos, posible negocio cerrado y suplantación. Revisión proporcional, evidencia, historial, respuesta/impugnación y trazabilidad de quién cambia la ficha. No castigar automáticamente un negocio por un reporte aislado.

## Calificaciones — MVP
**Elegibilidad ratificada por el líder del proyecto:** solo una cuenta con contacto verificado puede calificar. La documentación propone 1–5 estrellas, una calificación vigente por cuenta y negocio editable, sin comentarios ni respuestas públicas; confirmar edición y duplicados con el equipo antes de implementar. Mostrar promedio y conteo de calificaciones visibles; no publicar la identidad del autor ni datos de moderación.

Un reporte o señal entra a revisión humana y no produce por sí solo pausa de nuevas calificaciones ni cambio público. Después de revisar, un moderador autorizado puede ocultar provisionalmente una calificación individual y debe registrar motivo, evidencia pertinente, responsable y fecha/hora. El autor recibe aviso privado y puede apelar privadamente dentro de 30 días del aviso; el plazo fue ratificado por el líder del proyecto como decisión inicial, pendiente de revisión legal/documental. La apelación recibe revisión humana y resolución registrada. Restaurar si no se documenta infracción; mantener oculta o aplicar otra medida requiere infracción y motivo documentados. Las categorías de infracción y medidas finales siguen pendientes. No eliminar automáticamente calificaciones ni despublicar el negocio por anomalías.

La propuesta de conservar calificaciones ocultas e historial de moderación durante 12 meses desde la resolución no está ratificada; validar retención, eliminación/anonimización y obligaciones aplicables con la persona responsable de privacidad y asesoría competente antes de implementarla. Véase `20_politica_calificaciones_moderacion.md`.

## Conservación y eliminación
Crear una matriz por dato con finalidad, responsable, ubicación, plazo y eliminación/anonimización. Evitar recopilar identificaciones oficiales si no hay necesidad justificada y un procedimiento seguro.

## Documentación legal pendiente
Aviso de privacidad, términos del servicio, autorización de publicación de fichas/fotos, acuerdo con comerciantes, condiciones de publicidad, proceso de solicitud de derechos y revisión del marco mexicano aplicable por profesional competente. Este documento no sustituye asesoría legal.
