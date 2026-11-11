# 18. Métricas y validación comercial

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Producto / operaciones / analítica  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** Este documento sigue en borrador salvo la dirección de analítica mínima agregada y recomendaciones contextuales ratificada por el equipo en `21_politica_ranking_destacados_analitica.md`; parámetros de medición y privacidad siguen pendientes.

## Objetivo
Aprender si PorAquí resuelve búsquedas reales y crea valor para comercios; **no confundir registros o visitas con éxito del negocio**.

## Árbol de medición
1. **Oferta:** negocios verificados y publicados, catálogos con información suficiente, actualización reciente.
2. **Descubrimiento:** búsquedas, búsquedas útiles, búsquedas sin resultados, navegación entre negocios.
3. **Acción:** clics de WhatsApp/llamada/ruta, generación/uso de enlaces compartidos.
4. **Retención:** usuarios que vuelven de forma agregada según medición lícita y adecuada.
5. **Operación:** horas por alta, solicitudes pendientes, reportes resueltos, errores de datos.
6. **Monetización futura:** anunciantes pagadores, renovación, impresiones, clics y resultado de campañas; no aplicar antes de vender publicidad.

## Definiciones operativas propuestas
- **Negocio activo verificado:** publicado, representante autorizado y datos comerciales revisados dentro del periodo definido (aún por decidir).
- **Búsqueda útil:** consulta para la que la persona puede identificar al menos una opción pertinente y contactable; validar mediante muestra y pruebas, no solo contar resultados técnicamente coincidentes.
- **Contacto atribuible:** clic en canal de contacto originado en PorAquí. *No equivale a venta.*
- **Catálogo vigente:** confirmado o editado dentro del período acordado; no implica stock garantizado.
- **Visitante recurrente:** medir solo de forma agregada y compatible con privacidad; no asignar perfiles persistentes ni usar identidad individual para recomendaciones. El método requiere aprobación de privacidad antes de activarse.

## Esquema mínimo de eventos
| Evento | Datos mínimos sugeridos | Precauciones |
|---|---|---|
| `search_performed` | categoría/término normalizado cuando sea seguro, resultados_count, período | Evitar guardar texto libre sensible sin necesidad. |
| `business_viewed` | negocio_id, fuente/campaña no personal | Evitar perfilado innecesario. |
| `item_viewed` | item_id, fuente general | Agregar por período. |
| `contact_clicked` | negocio_id, canal, contexto agregado | Diferenciar clic de compra; no perfilar persistentemente a la persona. |
| `featured_impression_aggregated` | candidato_id, periodo, total de impresiones | Agregar antes de conservar; no guardar historial individual de exposición. Ventana y granularidad por definir con el piloto. |
| `catalog_shared` | negocio_id, tipo de enlace | No registrar mensajes privados de Facebook/WhatsApp. |
| `catalog_confirmed` | negocio_id, momento | Medir revisión, no inventario real. |
| `report_resolved` | motivo y duración de resolución | Proteger datos del reportante. |

## Recomendaciones y ranking
En el MVP, dar recomendaciones contextuales solo a partir de la consulta/categoría actual; no crear perfiles persistentes ni inferir probabilidad individual de compra. La señal de calificación es secundaria. Calibrar pesos, sinónimos, normalización y rotación únicamente tras contar con línea base del piloto; no fijar metas numéricas por adelantado. Las mediciones son mínimas y agregadas, sujetas a los requisitos de privacidad antes de activarse.

## Experimentos iniciales
- Observar búsquedas de productos/servicios en grupos accesibles legítimamente y clasificar necesidades sin recopilar datos personales.
- Pedir a consumidores reales tareas concretas en un prototipo y observar si encuentran establecimientos pertinentes.
- Mostrar a negocios el enlace compartible, registrar quién publica por iniciativa propia y si recibe contactos.
- Medir esfuerzo de alta y mantenimiento de catálogo, sin inventar una tasa semanal de captación.

## Tablero de decisión
| Señal | Interpretación | Acción a evaluar |
|---|---|---|
| Hay búsquedas útiles y contactos | Evidencia inicial de valor | Mejorar cobertura y usabilidad. |
| Los catálogos se comparten, pero nadie usa el buscador | Catálogo valioso, descubrimiento débil | Replantear buscador, no asumir éxito publicitario. |
| Muchas búsquedas vacías | Cobertura/calidad insuficiente | Concentrar categorías/zona antes de escalar. |
| Datos desactualizados | Riesgo de confianza | Simplificar actualizaciones y revisión. |
| No existen señales de valor tras pilotos razonables | Riesgo de producto no deseado | Detener expansión o cancelar directorio. |

## Ritmo de revisión
En el piloto: revisión frecuente del equipo de producto, con notas de evidencia cualitativa y cuantitativa. No establecer umbrales de éxito sin datos base. Registrar decisiones de continuar/cambiar/detener con fecha y motivo.

## Pendientes
Consentimiento/analítica, metodología de retorno, forma de verificar contactos/ventas con comerciantes y criterios cuantitativos cuando existan primeras observaciones.
