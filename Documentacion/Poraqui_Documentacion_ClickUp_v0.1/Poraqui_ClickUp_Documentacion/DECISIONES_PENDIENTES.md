# Decisiones pendientes por aprobar

Este registro mantiene abiertas las decisiones no ratificadas. Un estado **Parcial** indica que solo una parte del tema tiene acuerdo y que el resto sigue pendiente. La aprobación de una decisión no demuestra implementación.

Los códigos DP-01–DP-28 de `REVISION_06_modelo_datos.md` v0.3 son referencias históricas y no se equiparan por número a los DP-01–DP-20 de este registro; conciliar por tema y evidencia, preservando los responsables y referencias de la tabla.

| Código | Estado | Decisión pendiente | Responsable propuesto | Documentos afectados |
|---|---|---|---|---|
| DP-01 | Pendiente | Elegir hosting comercial compatible con Next.js + NestJS después de acordar volumen y presupuesto; comparar cuotas, runtime SSR, límites y costo total | Líder técnico + fundadores | 05, 07, 08, 10, 14 |
| DP-02 | Pendiente | Proveedor de BD, autenticación y política de invitaciones; verificar exportación, RLS y responsabilidades operativas antes de elegir | Líder técnico | 03, 05, 06, 07 |
| DP-03 | Pendiente | Proveedor de mapas y proceso de captura/verificación de coordenadas | Equipo técnico | 01, 04, 05 |
| DP-04 | Abierta — dirección acordada; calibración pendiente | La jerarquía cualitativa está acordada: coincidencia directa/relevancia primero, después cobertura/calidad; ubicación confirmada solo para distancia/ruta y no como desempate local por defecto; calificaciones visibles secundarias. Calibrar normalización, sinónimos, pesos y desempates técnicos tras obtener datos del piloto; no fijar valores antes. | Producto + backend | 01, 02, 05, 06, 07, 21 |
| DP-05 | Pendiente | Múltiples sucursales en MVP o solo después | Producto | 01, 02, 06 |
| DP-06 | Pendiente | Frecuencia de recordatorios, canales y permisos | Producto + comerciante | 02, 04, 16 |
| DP-07 | Pendiente | Reportes anónimos o autenticados y antiabuso | Producto + seguridad | 02, 03, 17 |
| DP-08 | Pendiente | Plazos de retención de evidencias y datos | Responsable de privacidad | 10, 16, 17 |
| DP-09 | Pendiente | Política de disponibilidad/desactualización | Producto | 02, 18 |
| DP-10 | Abierta — principio inicial acordado; automatización futura pendiente | No hay pausas ni ocultamiento automáticos por volumen en la política inicial. Observar tráfico del piloto; cualquier propuesta futura de automatización requiere evidencia, umbrales/ventana aprobados, controles contra abuso y prueba/aceptación explícita. No ocultar una calificación individual sin revisión humana. | Producto + seguridad | 02, 06, 10, 17, 20 |
| DP-11 | Pendiente | Mensajería/WhatsApp oficial e incorporación | Operaciones | 04, 16 |
| DP-12 | Abierta — dirección documentada como acordada; detalles pendientes | La dirección acordada es analítica mínima y agregada, sin perfiles persistentes, con recomendaciones contextuales a consulta/categoría. Acordar línea base, eventos/granularidad, aviso/base aplicable, finalidad, retención/eliminación y límites presupuestales antes de activar medición o personalización; metas numéricas solo después de observaciones del piloto. | Fundadores + Producto + responsable de privacidad | 15, 17, 18, 21 |
| DP-13 | Pendiente | Propiedad de dominio, repositorios y credenciales | Fundadores | 10, 13 |
| DP-14 | Pendiente | Convenio de estadía, propiedad intelectual y documentos legales de operación | Fundadores + asesor legal | 00, 13, 17 |
| DP-15 | Abierta — plazo inicial ratificado por el líder; legal/operación/retención pendientes | Validar legal y operativamente el aviso privado, el plazo inicial de apelación de 30 días ratificado por el líder del proyecto, las medidas finales de moderación y los plazos de retención/eliminación/anonimización (la propuesta de 12 meses no está ratificada) | Producto + seguridad + responsable de privacidad | 02, 06, 10, 17, 20 |
| DP-16 | Abierta — política inicial contra pausas automáticas; condiciones futuras pendientes | La política inicial descarta límites temporales automáticos por picos. Si el piloto justifica proponerlos en el futuro, decidir evidencia, ventana/umbrales, duración, responsables, revisión y apelación antes de habilitarlos; hoy la respuesta a señales es revisión humana y el ocultamiento provisional de una calificación individual exige revisión previa. | Producto + seguridad | 04, 06, 10, 18, 20 |
| DP-17 | Abierta — base acordada; elegibilidad/calibración/operación pendientes | El equipo aprobó curación manual entre candidatos elegibles/pertinentes, con motivo/origen/periodo y separación del ranking orgánico; también rotación con impresiones agregadas entre candidatos comparables. Definir reglas de elegibilidad operativa, responsables y revisión; calibrar ventana, frecuencia, límites, pesos y fórmula con datos del piloto. Publicidad pagada fuera del MVP; futuras ubicaciones deben marcarse Patrocinado y mantenerse separadas de orgánicos. | Producto | 01, 02, 05, 06, 15, 18, 21 |
| DP-18 | Abierta — implementación/verificación y parámetros operativos pendientes | Usuario coordina implementación/verificación de RPO máximo de 24 horas con respaldos al menos diarios; Adrian Gallardo (Chimi) es suplente designado; habilitar/verificar accesos, acordar retención, RTO y periodicidad de restauración aislada | Usuario + Adrian Gallardo (Chimi) + líder técnico | 05, 10 |
| DP-19 | Pendiente | Criterios y responsable para autorizar pruebas funcionales comparativas tras cerrar la evaluación documental | Fundadores + líder técnico | 05, 14 |
| DP-20 | Abierta — inclusión en alcance mantenida; capacidad/fase/fechas pendientes | Confirmar capacidad y fase/fechas del roadmap para calificaciones públicas autenticadas/moderadas del MVP, sin alterar su inclusión en el alcance | Producto + fundadores | 01, 02, 05, 12, 14 |

**Estado de cierre:** ninguna fila completa queda marcada como **Resuelta** en esta actualización: las entradas que contienen acuerdos ratificados conservan decisiones, tareas o validaciones abiertas; sus partes ratificadas se delimitan en la columna Estado.

**Regla:** ninguna decisión abierta debe transformarse silenciosamente en requisito durante la implementación. Solo se marca **Resuelta** cuando el alcance completo de esa decisión está explícitamente ratificado; un acuerdo parcial mantiene abierto el resto. La aprobación documental no prueba implementación.
