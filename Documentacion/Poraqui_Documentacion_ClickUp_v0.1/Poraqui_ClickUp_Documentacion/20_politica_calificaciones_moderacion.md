# 20. Política inicial de calificaciones y moderación

> **Producto:** PorAquí · **Estado:** decisiones de base ratificadas por el líder del proyecto; detalles legales y operativos pendientes. **No demuestra que la función esté implementada.**

## Decisiones de base

- **Elegibilidad:** solo una cuenta con contacto verificado puede enviar una calificación. El visitante puede consultar datos públicos, pero para calificar debe autenticarse y tener el contacto verificado.
- **Formato MVP propuesto en la documentación existente:** puntuación de 1 a 5 estrellas; una calificación vigente por cuenta y negocio; edición permitida; sin comentarios ni respuestas públicas. La elegibilidad fue ratificada por el líder del proyecto; confirmar en equipo los detalles de edición y duplicados antes de implementarlos.
- **Sin pausas automáticas por volumen:** un pico o una señal de anomalía no pausa nuevas calificaciones, no borra reseñas y no despublica el negocio. No se han aprobado umbrales numéricos ni ventanas de detección.
- **Revisión humana:** los reportes y señales ingresan a una cola interna. Un moderador autorizado revisa el caso. El reporte o el volumen, por sí solos, no cambian la visibilidad pública.
- **Ocultamiento provisional individual:** después de una revisión humana, un moderador autorizado puede ocultar provisionalmente la calificación denunciada. Debe registrar la calificación afectada, motivo, evidencia pertinente, responsable y fecha/hora. No ocultar automáticamente por número de reportes o por un pico.
- **Aviso y apelación:** si se oculta una calificación, avisar privadamente al autor y permitir una apelación privada dentro de 30 días desde el aviso. La apelación recibe revisión humana y una resolución registrada. Este plazo es una decisión inicial del líder del proyecto, todavía pendiente de revisión legal y documental.
- **Resultado de revisión:** restaurar la calificación si no se documenta una infracción. Mantener oculta o aplicar otra medida solo con una infracción documentada y una decisión motivada. Las categorías de infracción y las medidas finales permitidas siguen pendientes de ratificación.
- **Agregados públicos:** mostrar promedio y cantidad de calificaciones visibles; excluir del cálculo las ocultas provisionalmente. No mostrar la identidad del autor ni detalles internos de moderación.

## Límite de alcance seleccionado en esta sesión

El usuario seleccionó aplazar los filtros y acciones automáticas de moderación de calificaciones fuera del MVP. Reconsiderarlos únicamente después del piloto, con evidencia y aprobación explícita; no fijar umbrales numéricos ahora. Esta nota registra la selección del usuario en esta sesión, no la atribuye al equipo o al líder y no acredita implementación.

## Flujo operativo

```text
Reporte o señal de anomalía
        ↓
Cola interna sin efecto público automático
        ↓
Moderador autorizado revisa y registra evidencia y decisión
        ↓
Si hace falta, oculta provisionalmente la calificación individual y avisa en privado
        ↓
Autor puede apelar en privado dentro de 30 días del aviso
        ↓
Revisión humana y resolución documentada
        ├── Sin infracción documentada → restaurar y reincorporar a promedio/conteo
        └── Infracción documentada → medida motivada conforme a reglas aún por ratificar
```

Una anomalía no es prueba de abuso. No imponer una limitación automática temporal a nuevas calificaciones basándose solo en volumen. Una medida sobre una calificación no suspende ni despublica automáticamente al negocio.

## Controles y trazabilidad

- Aplicar mínimo privilegio: solo moderadores designados acceden a reportes, identidad del autor y evidencia necesaria para resolver el caso.
- Registrar reporte/señal, calificación afectada, acceso relevante, ocultamiento, aviso, apelación, revisión, resultado y restauración o medida final.
- Mantener fuera de las vistas públicas la identidad, el reportante y el historial de moderación.
- La propuesta existente de conservar calificaciones ocultas y su historial por 12 meses después de la resolución **no queda ratificada por esta política**: validar retención, eliminación/anonimización y obligaciones aplicables con el responsable de privacidad/asesoría competente antes de implementarla.

## Criterios de aceptación para implementación

1. Solo una persona autenticada en una cuenta asociada a un contacto verificado puede crear una calificación; las cuentas sin contacto verificado no pueden calificar.
2. Reportar una calificación o generar una señal de volumen no la oculta automáticamente ni pausa nuevas calificaciones; tampoco borra reseñas ni despublica el negocio.
3. Solo un moderador autorizado, después de revisión humana, puede ocultar provisionalmente una calificación individual; el motivo y la decisión quedan auditados.
4. El autor recibe aviso privado del ocultamiento y puede apelar en privado dentro de los 30 días siguientes; la apelación tiene revisión humana y resultado registrado.
5. Una calificación sin infracción documentada se restaura y vuelve a los agregados públicos. Cualquier medida que la mantenga oculta requiere infracción y motivo documentados.
6. Las vistas públicas no revelan identidad del autor ni datos de moderación; promedio y conteo excluyen las calificaciones ocultas.
7. Probar aislamiento entre dos negocios y que las solicitudes de actores no autorizados no leen ni modifican las calificaciones ajenas.

## Pendientes antes de fijar todos los detalles de implementación

- Definir criterios de duplicados, edición, reportes de reseñas y categorías de infracción.
- Definir las señales y la ventana de observación del piloto; no fijar umbrales numéricos hasta contar con evidencia. Cualquier automatización futura requiere aprobación explícita, pruebas contra abuso y revisión de apelaciones.
- Ratificar acceso por rol, procedimiento de moderación y medidas finales; evitar que un actor pueda forzar la pausa de calificaciones de un negocio mediante reportes coordinados.
- Validar legalmente el plazo de apelación, avisos, retención y eliminación/anonimización. La retención propuesta de 12 meses no está aprobada.
- Confirmar con el equipo los detalles MVP de escala, edición y unicidad que las fuentes actuales proponen.

## Fuentes de decisión

- `01_alcance_requisitos_mvp.md` — RF-020 y RF-021.
- `02_reglas_negocio.md` — RN-027 y RN-031–034.
- `04_flujos_usuario.md` — FU-08.
- `06_modelo_datos.md` — `business_ratings` y `rating_moderation_events`.
- `10_seguridad_despliegue.md` — controles de acceso, abuso y auditoría.
- `17_datos_privacidad.md` — clasificación, minimización y moderación.
- `DECISIONES_PENDIENTES.md` — DP-10, DP-15, DP-16 y DP-20.
