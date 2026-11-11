# 21. Política inicial de ranking, destacados y analítica

> **Estado:** acuerdos del equipo ratificados para orientar el MVP; las calibraciones del piloto y requisitos legales/privacidad siguen pendientes. **No demuestra que estas funciones estén implementadas.**

## Acuerdos del equipo

### Resultados orgánicos

- Priorizar coincidencia con la consulta/categoría. Una coincidencia directa precede a otra más amplia; entre resultados con relevancia comparable, considerar cobertura y calidad/vigencia de la información pública.
- Usar ubicación confirmada para mostrar distancia o ruta. No utilizarla como desempate local por defecto dentro de la cobertura inicial de Santiago Ixcuintla.
- Las calificaciones son una señal secundaria, nunca un multiplicador dominante. Solo se consideran calificaciones visibles conforme a la política 20.
- No se han ratificado pesos, umbrales, normalización, sinónimos, antigüedad límite ni fórmula de orden. Calibrarlos después de observar el piloto; no inferir existencias.

### Rotación de exposición

- En candidatos comparables, se permite distribuir exposición usando impresiones **agregadas** para dar oportunidad a opciones con menor exposición reciente.
- No se ha ratificado una ventana, frecuencia, límite, fórmula ni objetivo numérico. Definirlos con datos del piloto antes de automatizar o evaluar resultados.
- No crear perfiles persistentes de visitantes ni usar exposición para inferir propensión individual de compra. La definición de impresión y sus periodos de agregación se deben documentar antes de medir.

### Selección manual de destacados

- El equipo puede seleccionar manualmente candidatos elegibles y pertinentes.
- Registrar el motivo, el origen de la selección y su periodo de vigencia; mantener los destacados visual y lógicamente separados del orden orgánico.
- Los criterios detallados de elegibilidad, frecuencia, responsables operativos y revisión de selección quedan para definir por Producto conforme a DP-17. La selección manual no es publicidad pagada.

### Recomendaciones y analítica

- Las recomendaciones del MVP son contextuales a la consulta o categoría actual; no crear perfiles persistentes por usuario ni inferir probabilidades individuales de compra.
- Medir lo mínimo necesario y en forma agregada, como búsquedas, categoría/término normalizado cuando sea seguro, resultados, vistas, impresiones y clics de contacto. Un clic no representa una venta.
- Antes de activar medición, definir finalidad, responsable, aviso/base aplicable, agregación, retención y eliminación/anonimización con la persona responsable de privacidad y asesoría competente. La aprobación de esta dirección de producto no equivale a aprobación legal ni autoriza seguimiento individual.

### Publicidad

- La publicidad pagada queda fuera del MVP y solo se considera en una fase posterior, tras revisión de resultados del piloto y decisión de producto.
- Si se aprueba después, cada ubicación patrocinada debe identificarse claramente como **Patrocinado** y mantenerse separada del ranking orgánico; pagar no compra mejores reseñas ni altera disponibilidad.
- Precios, segmentación, medición, condiciones y avisos legales quedan pendientes antes de vender o activar campañas.

## Criterios de aceptación para implementación

1. Entre candidatos elegibles, los resultados siguen la prioridad cualitativa acordada; ninguna ponderación no aprobada se introduce como regla fija.
2. Distancia/ruta solo se presenta con coordenadas confirmadas; ubicación local no funciona como desempate por defecto.
3. Las calificaciones visibles son secundarias y no se usan pesos ni umbrales sin acuerdo y evidencia del piloto.
4. La rotación, cuando se implemente, compara impresiones agregadas de candidatos comparables y no crea identificadores o perfiles persistentes de visitantes.
5. La curación manual se limita a candidatos elegibles y pertinentes; guarda motivo, origen y periodo, y no se mezcla con orgánicos.
6. Las recomendaciones solo usan la consulta/categoría actual. La analítica usa eventos mínimos y agregados, con finalidad, aviso/base, retención y eliminación documentados antes de activarse.
7. No se venden ni muestran ubicaciones pagadas en el MVP. Una fase futura exige etiqueta **Patrocinado** visible y separación del ranking orgánico.

## Calibración y decisiones pendientes

- DP-04: normalización, sinónimos, desempates técnicos y eventual fórmula de relevancia.
- DP-17: unidad/ventana de exposición, frecuencia y límites de rotación; criterios operativos, responsables y revisión de destacados manuales.
- DP-09: definición y tratamiento de vigencia/desactualización de fichas.
- DP-12: línea base, métricas mínimas y límites presupuestales; no fijar metas numéricas antes de contar con datos.
- Privacidad/legal: finalidad, aviso/base aplicable, retención y eliminación/anonimización de analítica; confirmar asesoría competente antes de activar seguimiento.
- Monetización: precios, segmentación, condiciones, medición y obligaciones para publicidad futura.

## Fuentes relacionadas

- `01_alcance_requisitos_mvp.md` — RF-014 y RF-019.
- `02_reglas_negocio.md` — RN-023–026.
- `05_arquitectura.md` — componentes, límite MVP y evolución.
- `06_modelo_datos.md` — destacados y eventos agregados.
- `15_plan_negocio_monetizacion.md` — publicidad futura.
- `17_datos_privacidad.md` — privacidad por diseño y analítica.
- `18_metricas_validacion.md` — medición agregada y datos del piloto.
- `DECISIONES_PENDIENTES.md` — DP-04, DP-09, DP-12 y DP-17.
