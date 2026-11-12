# Revisión del modelo de datos y ciclo de vida del catálogo

# Revisión del modelo de datos y ciclo de vida del catálogo

> **Producto:** PorAquí · **Empresa:** NextWare
> **Tarea de origen:** [Revisar modelo de datos y ciclo de vida del catálogo](https://app.clickup.com/t/86bcqtu76)
> **Tarea de sincronización:** [Alinear revisión del modelo y registro de decisiones](https://app.clickup.com/t/86bcwrwj6)
> **Estado:** Alineada con acuerdos ratificados específicos; **el modelo no está aprobado en conjunto**.
> **Versión:** 0.4 · **Sincronizada:** 2026-11-12
> **Base:** `06_modelo_datos.md` v0.1 y documentos `01`, `02`, `03`, `04`, `05`, `07`, `10`, `16`, `17`, `README_Indice` y `DECISIONES_PENDIENTES.md`.
> **Modelo de referencia:** `06_modelo_datos_v0.4.md` (commit `fd88c3e`).
> **Fuente:** `REVISION_06_modelo_datos.md` adjunto a `86bcqtu76`; el adjunto original permanece intacto.
> **Alcance:** Modelo conceptual y reglas. Sin migraciones, sin código ni edición de adjuntos fuente de ClickUp.

## 1. Resumen ejecutivo

La revisión de `06` documenta brechas y resoluciones propuestas. La referencia vigente para esta sincronización es `06_modelo_datos_v0.4.md`. Esta revisión **no aprueba el modelo en conjunto ni acredita implementación**; únicamente los acuerdos explícitos enumerados abajo tienen estado de ratificados.

### Acuerdos ratificados vigentes

- **Equipo, tarea 86bcwrwhg:** para calificar se requiere una cuenta autenticada asociada a un contacto verificado; una señal de volumen no pausa automáticamente las calificaciones; ocultar provisionalmente una calificación individual requiere revisión humana, motivo y auditoría; el aviso y la apelación son privados y el plazo inicial es de 30 días (validación legal pendiente); restaurar si no hay infracción documentada.
- **Líder del proyecto, política 20:** mostrar promedio y cantidad de calificaciones visibles, excluyendo las ocultas provisionalmente; no exponer la identidad del autor ni detalles internos de moderación; un pico o reporte aislado no borra calificaciones ni despublica el negocio.
- **Equipo, política 21 y tarea 86bcwrwhm:** jerarquía cualitativa de ranking; ubicación confirmada solo para distancia/ruta y calificaciones como señal secundaria; curación manual de destacados con motivo/origen/periodo, separada del ranking orgánico; rotación por impresiones agregadas entre candidatos comparables.

**Pendiente de ratificación:** el formato y escala de calificación, comentarios, edición/duplicados, proveedor y canal de identidad, método de alta/invitación, taxonomía de categorías/subcategorías, umbrales y retención. También siguen abiertos la elegibilidad operativa, responsables/revisión y calibración de ventanas, frecuencias, límites, pesos y fórmulas de ranking/destacados. Las demás resoluciones de esta revisión continúan como propuestas, no como acuerdos aprobados.

**Direcciones registradas como acordadas, sin afirmar implementación:** el registro vigente describe como acordada la analítica mínima/agregada, sin perfiles persistentes, con recomendaciones contextuales; definición de eventos/granularidad, aviso/base aplicable, finalidad, retención/eliminación y presupuesto siguen abiertos. DP-20 conserva la inclusión de calificaciones autenticadas/moderadas en el alcance, pero deja capacidad y fase/fechas pendientes; esto no ratifica el formato de las calificaciones.

| Problema detectado | Resolución propuesta en la revisión | Estado vigente |
|---|---|---|
| Mezcla captación, publicación y verificación | Tres ciclos separados: `business_applications.stage`, `businesses.publication_status` y `business_verifications.status` | Propuesta detallada; no ratificada |
| No resolvía producto/servicio ↔ sucursal ↔ precio/disponibilidad | Varias sucursales para ubicación/contacto; catálogo, precio y disponibilidad globales del negocio; sin oferta por sucursal en MVP | Propuesta detallada; no ratificada |
| Faltan relaciones ítem-categoría, consentimiento, contactos, slugs y auditoría | Se incorporan `catalog_item_categories`, `business_consents`, `contacts`, `slug_redirects` y `audit_log` | Propuesta detallada; no ratificada |
| Calificaciones y estados del negocio contradictorios | La revisión propuso puntuación + comentario para usuarios registrados y estados del negocio separados/mapeados desde `16` | Parcial: solo los acuerdos base enumerados arriba están ratificados; formato y comentarios siguen pendientes |
| Cobertura y promesa de catálogo ambiguas | MVP en Santiago Ixcuintla; sin promesa de “catálogo completo”; límites técnicos, no comerciales | Propuesta detallada; no ratificada |
| Contacto público sin regla de consentimiento | Solo WhatsApp/teléfono comercial autorizado; datos personales privados; retiro al revocar | Propuesta detallada; no ratificada |
| Registro de comerciantes y visitantes sin definir | Comerciantes por invitación; visitantes con correo + contraseña y correo verificado para calificar | Propuesta detallada; método de alta e identidad siguen pendientes |
| Retención y vigencia sin umbrales concretos | Retención ajustada con validación legal previa a producción; vigencia 30/60/90 sin despublicar automáticamente | Plazos y umbrales no ratificados; validación legal/de privacidad pendiente |

Las recomendaciones de precio/disponibilidad global, sucursales y catálogo de esta revisión siguen siendo propuestas. No se introducen cantidades de stock ni `catalog_offers` por decisión de esta revisión; esos detalles no se consideran aprobados por su inclusión aquí. El registro vigente `DECISIONES_PENDIENTES.md` conserva abiertos los asuntos no ratificados y sus responsables/referencias.

## 2. Fuentes y método

Se revisaron los documentos de ClickUp:

| Documento | Uso en esta revisión |
|---|---|
| `01_alcance_requisitos_mvp.md` | Requisitos P0/P1, exclusiones y criterios de aceptación |
| `02_reglas_negocio.md` | Reglas RN-001 a RN-030 y casos límite |
| `03_roles_permisos.md` | Roles, mínimo privilegio, membresías e invitaciones |
| `04_flujos_usuario.md` | Flujos de alta, edición, reportes, vigencia y calificaciones |
| `05_arquitectura.md` | Límites entre componentes, RLS, almacenamiento y observabilidad |
| `06_modelo_datos.md` | Modelo base revisado |
| `07_contratos_api.md` | Rutas públicas/privadas y exposición de datos |
| `10_seguridad_despliegue.md` | Controles, respaldos y entornos |
| `16_operacion_comerciantes.md` | Onboarding real, evidencia y estados de solicitud |
| `17_datos_privacidad.md` | Clasificación de datos, retención y moderación |
| `DECISIONES_PENDIENTES.md` | Registro local vigente DP-01 a DP-20; los códigos DP-01 a DP-28 de esta revisión son referencias históricas y no se equiparan por número |
| `20_politica_calificaciones_moderacion.md` | Acuerdos base ratificados por el líder; escala, edición/duplicados y retención siguen pendientes |
| `21_politica_ranking_destacados_analitica.md` | Dirección cualitativa de ranking y curación/rotación de destacados; calibración operativa sigue pendiente |

Método: contraste entidad por entidad, revisión de ciclos de vida, identificación de invariantes, datos privados, índices e integridad. Las resoluciones detalladas en esta revisión son propuestas salvo los acuerdos explícitos enumerados en §1; los asuntos abiertos permanecen en `DECISIONES_PENDIENTES.md`. Los códigos DP heredados de esta revisión v0.3 no equivalen por número a los del registro local vigente.

## 3. Propuestas de resolución por entidad y relación (no ratificadas salvo acuerdos explícitos en §1)

### 3.1 Negocio: tres ciclos separados

`businesses.estado_publicacion` mezclaba captación, publicación y verificación. Además, `16` usaba otra lista de estados y `06` tenía `business_verifications` con su propio estado.

**Propuesta de resolución no ratificada:**

- `business_applications.stage`: `contacted`, `interested`, `pending_evidence`, `approved`, `rejected`, `invited`, `activated`, `inactive`, `follow_up`.
- `businesses.publication_status`: `draft`, `pending_review`, `published`, `suspended`, `closed_confirmed`.
- `business_verifications.status`: `pending`, `verified`, `rejected`, `expired`.

**Equivalencias con `16`:**

| Estado en `16` | Dónde vive |
|---|---|
| `contacted`, `interested`, `pending_evidence` | `business_applications.stage` |
| `approved`, `rejected`, `invited`, `activated`, `inactive`, `follow_up` | `business_applications.stage` |
| `published` | `businesses.publication_status`; la solicitud sigue `activated` |

**Reglas:**

- `approved` no publica automáticamente.
- `published` exige solicitud `activated`, verificación `verified`, consentimiento `publish_profile` vigente, al menos un contacto público autorizado y al menos una sucursal `active` o `service_area`.
- `suspended` oculta ficha y catálogo; conserva datos y puede volver a `published`.
- `closed_confirmed` retira de búsquedas y no borra; es terminal.
- La verificación `expired` mueve la publicación a `suspended` con motivo `verification_expired`.
- `inactive` y `follow_up` son operativos; no son estados de publicación.

### 3.2 Producto/servicio vs disponibilidad vs stock

`catalog_items` incluye `tipo`, `precio`, `moneda`, `estado_publicacion`, `estado_disponibilidad` y `confirmado_en`. La propuesta de resolución no ratificada mantiene esa base y elimina las ambigüedades:

- **Producto/servicio:** qué se ofrece (`tipo`).
- **Publicación:** si el ítem es visible (`estado_publicacion`).
- **Moderación:** si un administrador lo bloqueó (`estado_moderacion`).
- **Disponibilidad:** qué se afirma (`estado_disponibilidad`).
- **Stock:** cantidad real, **fuera del MVP**.

**Reglas:**

- `confirmado_en` confirma **solo disponibilidad** del ítem; no confirma la ficha del negocio.
- `businesses.ultima_confirmacion` confirma la ficha del negocio; no cambia la disponibilidad de los ítems.
- `available_confirmed` exige `confirmado_en` y `fuente_disponibilidad`.
- `fuente_disponibilidad`: `comerciante`, `admin`, `reporte`, `importacion`.
- `tipo_precio`: `fijo`, `desde`, `rango`, `cotizar`.
- Dinero: `numeric(12,2)`, moneda ISO 4217 y `precio >= 0`; nunca `float`.
- No hay stock, reservas, SKU ni variantes en el MVP.
- No hay `catalog_offers` ni precio/disponibilidad por sucursal en el MVP.

### 3.3 Sucursales: varias, pero catálogo global

`branches` existe y la documentación reconoce casos con varias sucursales. La propuesta de resolución no ratificada es explícita:

- Un negocio puede tener **varias sucursales** para ubicación, horario y contacto.
- Como máximo una sucursal principal por negocio.
- Un negocio publicado debe tener al menos una sucursal `active` o un `service_area`.
- `catalog_items` **no tiene `branch_id`**: precio y disponibilidad son globales.
- La UI no debe prometer precio, stock ni disponibilidad por sucursal.
- El precio por sucursal queda como evolución futura (DP-28), no como requisito del MVP.

**Campos añadidos:** `name`, `slug`, `status`, `is_primary`, `service_area`, `locality_id`, `created_at`, `updated_at`. El contacto se estructura en `contacts`.

### 3.4 Categorías: propuesta de relación ítem-categoría

`categories` tiene `parent_id` y `tipo`, pero no existía relación con `catalog_items`. Sin ella, `RF-001` y `RF-017` no podían funcionar correctamente.

**Propuesta de resolución no ratificada:**

- `categories.kind`: `business`, `item`, `both`; `status`: `active`, `deprecated`.
- `catalog_item_categories` con PK compuesta, `is_primary` y una categoría principal por ítem.
- Todo ítem publicado debe tener al menos una categoría activa.
- El árbol de categorías no puede tener ciclos.
- Una categoría usada no se elimina: se deprecia o fusiona con redirección.

### 3.5 Medios: negocio, sucursal e ítem

`catalog_media` solo cubría ítems; `RF-003` y `16` piden fotos del negocio.

**Propuesta de resolución no ratificada:** tablas explícitas `catalog_media`, `business_media` y `branch_media`, sin propietario polimórfico. Cada una tiene:

- `status` (`pending`, `ready`, `rejected`);
- `is_primary` y `sort_order` únicos por propietario;
- `object_key` privado, `mime`, tamaño, checksum y `alt_text`;
- `deleted_at` para limpieza controlada;
- eliminación de EXIF privado y de originales expuestos.

### 3.6 Membresías e invitaciones

**Propuesta de resolución no ratificada:** completar `business_memberships` con `id`, `invited_by`, `accepted_at`, `revoked_at`, `created_at` y `updated_at`; unique parcial para una membresía activa por usuario/negocio; invariante de al menos un owner activo y prohibición de revocar al último sin transferencia o intervención administrativa auditada.

`invitations` deja de usar `uso` y pasa a `status` (`pending`, `accepted`, `expired`, `revoked`), `role`, `token_hash`, `expires_at`, `sent_at`, `accepted_at`, `used_at`, `used_by` y `attempts`.

### 3.7 Verificación y consentimiento

`business_verifications` tenía evidencia y estado, pero no una entidad de consentimiento. `16` y `17` exigen autorización para publicar ficha, fotos y contacto.

**Propuesta de resolución no ratificada:**

- `verification_evidence` privada, con `object_key`, checksum, `uploaded_by`, `retention_until` y `deleted_at`.
- `business_consents` con `type` (`publish_profile`, `publish_photos`, `publish_contact`, `terms`, `privacy`), `granted_by`, `granted_at`, `expires_at`, `revoked_at`, `evidence_id` y `version`.
- Sin `publish_profile` vigente no se publica la ficha.
- Sin `publish_photos` vigente no se publican fotos.
- Sin `publish_contact` vigente no se publican contactos comerciales.
- La revocación oculta los campos afectados de inmediato y se audita.

Verificar existencia no equivale a autorizar publicación; son actos separados.

### 3.8 Reportes

**Propuesta de resolución no ratificada:** `data_reports` incorpora `branch_id`, `reporter_ref` seudónimo, `resolution_note`, `duplicate_of_id` y trazabilidad de estados. La pertenencia se garantiza con FK compuesta `(business_id, catalog_item_id)`; un reporte no cambia por sí solo disponibilidad ni publicación (`RN-017`).

### 3.9 Calificaciones: propuesta de formato (no ratificada) y acuerdos base vigentes

La contradicción documental era:

- `01` RF-020 las incluye en P0 y dice que “cualquier visitante” puede calificar.
- `02` RN-027 no habilita reseñas públicas.
- `README_Indice` dice que no son MVP.
- `17` las deja para fase posterior.

**Propuesta de v0.3, no ratificada:** el borrador propone un MVP con **puntuación + comentario**. El modelo v0.4 mantiene el formato, los comentarios, la escala y la edición/duplicados como pendientes; véase §1 para los acuerdos base vigentes.

- Navegar, buscar y contactar no requiere cuenta.
- Calificar y comentar exige una **cuenta de visitante registrada** con correo + contraseña y correo verificado; una cuenta por correo.
- `score` obligatorio, entero 1–5.
- `comment` habilitado y opcional, máximo 1.000 caracteres.
- Una calificación activa por usuario/negocio.
- Solo un negocio `published` recibe calificaciones nuevas.
- Un usuario no puede calificar su propio negocio ni uno del que es miembro activo.
- Solo `published` es pública; `pending`, `hidden` y `rejected` no.
- El autor se muestra con alias o “Usuario de PorAquí”; nunca email, teléfono ni `user_id`.
- El negocio no puede editar ni borrar; puede reportar.
- El autor puede editar o borrar; el borrado se conserva para auditoría.
- Al suspender o cerrar el negocio, las calificaciones se ocultan de la vista pública, no se borran.

**Acuerdos ratificados aplicables (equipo y política 20):** los reportes y señales reciben revisión humana; un pico o reporte no pausa automáticamente nuevas calificaciones ni cambia su visibilidad. El ocultamiento provisional solo puede ser individual, tras revisión humana, con motivo y auditoría. El aviso y la apelación son privados, con plazo inicial de 30 días sujeto a validación legal; restaurar si no hay infracción documentada. No borrar calificaciones ni despublicar el negocio por una señal aislada.

**Detalles operativos propuestos en v0.3, no ratificados:**

- Los filtros automáticos por frecuencia/IP, duplicados, enlaces o longitud, y los umbrales numéricos (por ejemplo, 5 calificaciones en 60 minutos o 10 en 24 horas) son propuestas, no reglas aprobadas.
- Limitar temporalmente la entrada, generar alertas automáticas, o fijar responsabilidades/plazos operativos requiere decisión y validación antes de implementar.
- El derecho del negocio a reportar y los detalles de impugnación, medidas finales y auditoría deben seguir las políticas ratificadas; los mecanismos no definidos aquí continúan pendientes.
- Ningún umbral o volumen convierte automáticamente una señal en prueba de abuso.

**Impacto en fuentes:** `01` RF-020, `02` RN-027/RN-030, `17` y `README_Indice` deben actualizarse en ClickUp después de la ratificación. No se modifican ahora.

### 3.10 Cobertura y promesa de catálogo: propuesta no ratificada

**DP-01:** el MVP se limita a **Santiago Ixcuintla, Nayarit**. No hay multi-ciudad ni multi-país. `localities` se limita a las localidades necesarias para esa cobertura; `zones` queda para P1/P2.

**DP-02:** no se promete “catálogo completo”. La promesa pública es:

- catálogo **publicado por negocios verificados**;
- búsqueda por negocio, categoría, producto o servicio;
- cobertura gradual y límites técnicos razonables;
- disponibilidad sujeta a confirmación y a la regla “Consultar existencia”.

No se usa “todo el catálogo”, “catálogo completo” ni “todos los negocios” como promesa comercial o de producto.

### 3.11 Contacto público y consentimiento: propuesta no ratificada

**DP-03:** solo se publica el **contacto comercial autorizado** por el representante:

- WhatsApp, teléfono, correo o red social de atención comercial.
- El consentimiento `publish_contact` debe estar vigente.
- Teléfonos y correos personales del representante quedan privados por defecto.
- La revocación retira el contacto de la vista pública de inmediato.
- No se extraen contactos de Facebook ni de fuentes no autorizadas.

### 3.12 Registro de comerciantes y visitantes: propuesta no ratificada

**Propuesta de v0.3 (DP-07 histórico, no ratificada):** que los comerciantes no tengan autoservicio de alta y que el flujo sea presencial/WhatsApp con aprobación administrativa e invitación segura; que visitantes puedan crear cuenta con correo + contraseña, verificación de correo antes de calificar, navegación anónima para consultar/contactar, sin permisos sobre negocios, y autenticación gestionada por un proveedor.

**Aclaración vigente del modelo v0.4:** para calificar se requiere una cuenta autenticada asociada a un contacto verificado. No se ratifican por esa regla el proveedor, el canal de verificación, la invitación de comerciantes, el correo + contraseña ni el flujo detallado de alta; esos puntos siguen pendientes.

### 3.13 Destacados y zonas: propuesta no ratificada

`featured_placements` usaba `recurso_tipo`/`recurso_id` polimórficos y `zona_id` sin tabla. **Propuesta de resolución no ratificada:** columnas explícitas `business_id`/`catalog_item_id` con exactamente un objetivo; `locality_id`/`zone_id` con como máximo una; `localities` para MVP y `zones` para P1/P2 (DP-26).

### 3.14 Recordatorios: propuesta no ratificada

**Propuesta de resolución no ratificada:** `business_reminders` incorpora `type` (`validity_review`, `report_followup`, `onboarding`), `idempotency_key`, `attempts` y `last_error`; las preferencias se separan en `notification_preferences`.

### 3.15 Eventos agregados

**Propuesta de modelado no ratificada:** `events_aggregated` declara clave única por tipo/período/dimensiones y evita datos personales crudos. La dirección de analítica mínima/agregada está documentada como acordada en DP-12, pero el esquema, eventos y granularidad siguen pendientes.

### 3.16 Slugs y URL: propuesta no ratificada

**Propuesta de resolución no ratificada:** `slug_redirects` con `entity_type`, `entity_id`, `old_slug` único por tipo y fecha. El slug actual vive en la entidad; los antiguos redirigen 301/equivalente; no se reutilizan; no hay cadenas ni ciclos.

### 3.17 Historial y auditoría: propuesta no ratificada

**Propuesta de resolución no ratificada:** `audit_log` append-only con actor, acción, entidad, `before/after` redactado, motivo, `request_id` y fecha. Cubre al menos:

- transiciones de negocio e ítem;
- membresías, roles, invitaciones y revocaciones;
- verificación y consentimiento;
- publicación/despublicación;
- precio y disponibilidad;
- resolución de reportes y moderación de calificaciones.

No guarda secretos ni PII innecesaria.

## 4. Ciclos de vida

### 4.1 Negocio

```text
Captación / onboarding (business_applications.stage)
contacted → interested → pending_evidence → approved → invited → activated
                                      ↘ rejected
                     inactive ↔ follow_up
Publicación (businesses.publication_status)
draft → pending_review → published → suspended → closed_confirmed
Verificación (business_verifications.status)
pending → verified → expired
        ↘ rejected
```

**Reglas:**

- Solo un negocio `published` es visible públicamente.
- `suspended` conserva datos y oculta ficha/catálogo.
- `closed_confirmed` no borra; muestra cierre y retira de búsquedas.
- La verificación aprobada es requisito para publicar, salvo excepción administrativa auditada.
- `inactive` y `follow_up` son estados operativos, no de publicación.
- La verificación `expired` implica `suspended`; no elimina el negocio.

### 4.2 Ítem

```text
Publicación
draft → published → unpublished → archived
Disponibilidad
unknown → available_confirmed → temporarily_out → discontinued
```

**Reglas:**

- `unknown` se muestra como “Consultar existencia”, nunca como “Disponible” (`RN-026`).
- `available_confirmed` requiere fecha y fuente de confirmación.
- `temporarily_out` sigue publicado; se oculta por defecto en filtros, pero el enlace directo informa (`RN-013`).
- `discontinued` se retira de búsquedas activas y conserva historial (`RN-014`).
- Un ítem solo es visible si el negocio está publicado, el ítem está publicado, la moderación es `clear` y tiene al menos una categoría.
- **No hay cantidades de stock en el MVP.** El stock real es futuro y proviene de POS (`RN-015`).
- La confirmación de vigencia del negocio **no** cambia la disponibilidad de los ítems (`RN-020`, `RN-022`).

### 4.3 Vigencia

| Campo | Qué significa |
|---|---|
| `ultima_confirmacion` | Última confirmación de la ficha del negocio |
| `confirmado_en` | Última confirmación de disponibilidad de un ítem |
| `valid_until` | Vigencia explícita opcional; no sustituye `confirmado_en` |
| `freshness` | Derivado por umbral: `fresh`, `stale` o `unknown`; no es estado almacenado |

“Todo sigue igual” actualiza `ultima_confirmacion` del negocio, no `confirmado_en` de los ítems.

**Propuesta de vigencia 30/60/90 no ratificada (DP-09 histórico de esta revisión):**

| Antigüedad de `confirmado_en` | `freshness` | Presentación pública |
|---|---|---|
| 0–30 días | `fresh` | Estado confirmado; si es `available_confirmed`, “Disponible” |
| 31–60 días | `stale` | Estado visible con advertencia de actualización |
| Más de 60 días | `unknown` | “Consultar existencia”; nunca “Disponible” |

- La ficha del negocio se marca para revisión a los **90 días** desde `ultima_confirmacion`.
- La antigüedad **no despublica** el negocio ni el ítem.
- La verificación vencida sí mueve la publicación a `suspended`.
- El cálculo es derivado; no se reescribe `estado_disponibilidad` solo por el paso del tiempo.
- Si el negocio confirma de nuevo, se actualiza `confirmado_en` o `ultima_confirmacion` según corresponda y se audita.

## 5. Relaciones e invariantes principales

1. Todo ítem pertenece a un solo negocio.
2. Todo ítem publicado requiere negocio publicado, moderación `clear` y al menos una categoría.
3. Todo reporte con `item_id` debe referirse a un ítem del mismo negocio (FK compuesta).
4. Toda membresía activa es única por usuario/negocio.
5. Todo negocio debe tener al menos un owner activo; el último no puede revocarse sin transferencia o intervención administrativa.
6. Todo negocio publicado debe tener solicitud `activated`, verificación `verified`, consentimiento `publish_profile` vigente, al menos un contacto público autorizado y al menos una sucursal `active` o `service_area`.
7. `available_confirmed` sin fecha/fuente es inválido.
8. `discontinued` no se borra; se archiva y conserva historial.
9. `temporarily_out` no elimina el ítem.
10. Un reporte no cambia automáticamente disponibilidad ni publicación.
11. Confirmar vigencia del negocio no cambia disponibilidad de ítems.
12. Slug único por ámbito, case-insensitive y sin reutilización; slugs antiguos redirigen sin cadenas.
13. Cada medio pertenece a un propietario explícito (negocio, sucursal o ítem) y tiene una imagen principal.
14. Datos privados no aparecen en vistas/endpoints públicos; IDs no otorgan permisos.
15. Toda transición de estado relevante se audita.
16. Una categoría referenciada no se elimina; se fusiona/deprecia con redirección; no hay ciclos.
17. Un precio con importe exige moneda.
18. No hay cantidades de stock en el MVP.
19. No hay `catalog_offers` en esta versión.
20. `featured_placements` tiene exactamente un objetivo.
21. Un ítem con `estado_moderacion = blocked` no es visible aunque esté `published`.
22. Todo ítem publicado tiene exactamente una categoría principal.
23. Un negocio puede tener varias sucursales; como máximo una principal; precio y disponibilidad no varían por sucursal.
24. Un contacto público exige consentimiento `publish_contact` vigente; los privados no salen en API pública.
25. La revocación de consentimiento oculta los campos afectados de inmediato.
26. Solo un negocio publicado recibe calificaciones nuevas.
27. Una calificación activa por usuario/negocio; `score` 1–5; solo `published` es pública; el autor no expone PII.
28. `business_applications`, `businesses.publication_status` y `business_verifications.status` son independientes; `published` no es estado de solicitud y `activated` no es estado de publicación.
29. Una verificación `expired` implica publicación `suspended`.
30. `audit_log` es append-only y no guarda secretos ni PII innecesaria.
31. Navegar, buscar y contactar no requiere cuenta; calificar/comentar exige una cuenta activa con correo verificado.
32. El autor no puede calificar su propio negocio ni uno del que es miembro activo.
33. `available_confirmed` con más de 60 días no se presenta como “Disponible”; la frescura es derivada y no reescribe el estado.
34. Los teléfonos y correos personales del representante no se publican; solo el contacto comercial autorizado.
35. El MVP se limita a Santiago Ixcuintla, Nayarit; no hay promesa de catálogo completo ni multi-ciudad.

## 6. Integridad, índices e historial

### 6.1 Integridad

- FKs compuestas para pertenencia entre negocio, ítem, sucursal, medio y reporte.
- Dinero: `numeric(12,2)`, ISO 4217, `precio >= 0`; nunca `float`.
- `CHECK` para enums, `score` 1–5, lat/lon y exactamente-un-propietario.
- Identidad: `identity_provider_id` único; correo de cuenta único y verificado antes de calificar; sin contraseñas en tablas de dominio.
- Fechas `timestamptz` en UTC.
- `created_at`, `updated_at`, `created_by`, `updated_by`, `deleted_at` donde aplique.
- Soft delete/archivo para datos auditables; anonimización para datos personales.
- Coordenadas: lat/lon válidas y ambas o ninguna.
- Enums como texto + `CHECK` o tablas de catálogo.
- RLS o autorización equivalente por membresía; vistas públicas separadas de tablas internas.
- Triggers o transacciones para último-owner, slug, categoría principal y contadores derivados.

### 6.2 Índices mínimos

| Entidad | Índice |
|---|---|
| `users` | identidad de proveedor única; email de cuenta único/normalizado; `email_verified_at`; teléfono normalizado |
| `businesses` | slug único case-insensitive; estado de publicación; localidad; `ultima_confirmacion` |
| `business_applications` | `stage`; `assigned_to`; `created_at`; `business_id` |
| `branches` | `(business_id, slug)` único; sucursal principal; `status` |
| `business_memberships` | único parcial `(user_id, business_id)` activo; índices por negocio/usuario |
| `categories` | único `(kind, parent_id, slug)`; evitar ciclos |
| `business_categories` | PK compuesta; índice inverso por categoría |
| `catalog_item_categories` | PK compuesta; índice inverso por categoría; principal parcial por ítem |
| `catalog_items` | `(negocio_id, estado_publicacion, estado_moderacion, estado_disponibilidad)`; nombre con trigram/full-text; slug único por negocio |
| `catalog_media` | `object_key` único; orden único por ítem; parcial para imagen principal |
| `business_media`, `branch_media` | propietario + `sort_order`; principal parcial |
| `business_verifications` | `business_id`, `status`, `expires_at` |
| `verification_evidence` | `verification_id`; `retention_until` |
| `business_consents` | `(business_id, type)`; vigencia; revocación |
| `contacts` | `(business_id/branch_id, type, is_primary)`; valor normalizado |
| `invitations` | `token_hash` único; expiración/estado |
| `data_reports` | estado/fecha; negocio/ítem/sucursal |
| `business_ratings` | `(business_id, status, created_at)`; único activo por `(user_id, business_id)` |
| `business_reminders` | clave de idempotencia; `due_at`; estado |
| `events_aggregated` | único por tipo/período/dimensiones |
| `slug_redirects` | `(entity_type, old_slug)` único |
| `audit_log` | entidad, actor, fecha; append-only |

Búsqueda: GIN/trigram/PostGIS según DP-04; no cerrar la decisión ahora.

### 6.3 Historial

`audit_log` cubre al menos:

- transiciones de estado de negocio e ítem;
- membresías, roles, invitaciones y revocaciones;
- verificación y consentimiento;
- publicación/despublicación;
- precio y disponibilidad;
- resolución de reportes y moderación de calificaciones.

No guardar PII innecesaria en los snapshots. Para datos personales, usar referencias seudónimas o redacción.

## 7. Datos privados, exposición y retención

### 7.1 No deben exponerse públicamente

- Email/teléfono personal del usuario, identificador de proveedor de identidad y estado de cuenta.
- Membresías, roles y permisos internos.
- Tokens/hashes de invitación.
- Evidencia de verificación y documentos de autorización.
- Identidad del reportante y notas de moderación.
- Contactos privados distintos al canal comercial autorizado.
- Object keys internos de almacenamiento.
- Logs de auditoría y analítica sin agregar.
- `user_id` del autor de una calificación; solo alias o seudónimo.

### 7.2 Matriz de retención

La matriz siguiente es una **propuesta no ratificada** heredada de la revisión v0.3. Los plazos de retención, eliminación y anonimización siguen abiertos en el registro vigente; la validación legal y de privacidad forma parte de la decisión pendiente. No tratar ningún plazo de esta tabla como requisito aprobado.

| Dato | Finalidad | Retención |
|---|---|---|
| Solicitudes rechazadas/abandonadas | Historial de captación | 12 meses |
| Evidencia de verificación | Acreditar existencia/autorización | 12 meses tras fin o rechazo |
| Consentimientos | Prueba de autorización | 5 años tras revocación/fin |
| Invitaciones | Activación de acceso | 30 días tras expirar/revocar |
| Reportes y resoluciones | Moderación e historial | 12 meses tras cierre |
| Calificaciones y moderación | Reputación y antiabuso | Publicada + 12 meses tras baja del negocio |
| Auditoría | Trazabilidad | 24 meses |
| Analítica agregada | Métricas de producto | Indefinida sin PII |
| Contenido despublicado | Historial administrativo | 90 días |
| Contactos | Operación y autorización | Vigencia + 12 meses; públicos se retiran al revocar |
| Respaldos | Recuperación | 30 días |

**Reglas:** no publicar contactos personales; no usar datos de POS de NextWare para publicidad sin base y consentimiento; no extraer datos de Facebook; no guardar identificaciones oficiales sin necesidad y procedimiento seguro.

## 8. Conflictos documentales y propuestas de resolución (no aprobadas en conjunto)

| Tema | Conflicto | Resolución |
|---|---|---|
| Calificaciones | `01` RF-020 en P0 y “cualquier visitante”; `02` RN-027 no habilita reseñas; `README` dice que no son MVP; `17` las deja para fase posterior | La revisión v0.3 propuso puntuación + comentario, pero ese formato no está ratificado. Aplican solo los acuerdos base de elegibilidad/moderación/agregados de §1; los demás detalles siguen pendientes |
| Ranking y destacados | La revisión plantea reglas operativas y fórmulas que aún no estaban ratificadas | La política 21 ratifica solo la dirección cualitativa y la separación/curación/rotación de base; ventanas, pesos, fórmula y elegibilidad operativa permanecen abiertas |
| Registro de visitantes | `01` presupone calificar sin cuenta; `02` RN-030 permite buscar/contactar sin cuenta | La revisión v0.3 propuso correo + contraseña y comerciantes por invitación; el método de alta/proveedor/canal sigue pendiente en v0.4 |
| Cobertura | `01` y `02` ya declaran Santiago Ixcuintla; DP-01 seguía abierta | MVP solo en Santiago Ixcuintla, Nayarit; sin multi-ciudad |
| Contacto público | `01` pide WhatsApp/llamada; `17` exige autorización y separar contacto personal | Solo contacto comercial autorizado; personales privados; retiro al revocar |
| Sucursales | `06` las deja pendientes; `01/02` mencionan casos con varias; no hay decisión | Varias sucursales para ubicación/contacto; catálogo global; precio por sucursal futuro (DP-28) |
| Estados del negocio | `06` usa `pending_review/closed_confirmed`; `16` usa `contacted/approved/activated/inactive` | Tres ciclos separados y tabla de equivalencias |
| Precio | `02` dice opcional; `06` solo tiene precio + moneda; no hay tipo de precio | `numeric(12,2)`, moneda ISO 4217, `tipo_precio` (`fijo/desde/rango/cotizar`) |
| Categorías | `categories.tipo` sin valores; no existe relación ítem-categoría | `categories.kind` y `catalog_item_categories` |
| Zonas | `featured_placements.zona_id` sin tabla | `localities` MVP; `zones` P1/P2; FK explícita |
| “Catálogos ilimitados” | `01/02` lo presentan como modelo comercial; `README` aclara que hay límites técnicos | Documentar límites técnicos, no comerciales |
| Vigencia | `02` deja pendiente la política de negocios no actualizados; `06` no fija umbrales | 30/60/90; frescura derivada; sin despublicación automática |

## 9. Decisiones priorizadas

> Los códigos DP-01–DP-28 de esta revisión v0.3 son referencias históricas de propuesta; no equivalen por número a los códigos DP-01–DP-20 del registro local vigente. Por ejemplo, el DP-04 de esta revisión trata búsqueda/sinónimos mientras el DP-04 vigente describe jerarquía cualitativa de ranking; el DP-17 de esta revisión trata fórmula de destacados mientras el DP-17 vigente describe curación/rotación. Conciliar por decisión y evidencia, nunca por coincidencia numérica.

### 9.1 Propuestas desarrolladas, pendientes de ratificación

| Código | Decisión | Resolución propuesta |
|---|---|---|
| DP-01 | Ciudad y cobertura inicial | Santiago Ixcuintla, Nayarit; sin multi-ciudad |
| DP-02 | Promesa de “catálogo completo” | No prometerlo; catálogo publicado, verificable y cobertura gradual |
| DP-03 | Teléfono/WhatsApp público y consentimiento | Solo contacto comercial autorizado; personales privados |
| DP-05 | Varias sucursales en MVP | Sí, varias; catálogo/precio global; sin oferta por sucursal |
| DP-07 | Registro de comerciantes | Solo por invitación; visitantes con cuenta propia para calificar |
| DP-08 | Retención de evidencias y datos personales | Matriz 12/24 meses; validación legal previa a producción |
| DP-09 | Vigencia y desactualización | 30/60/90; frescura derivada; sin despublicación automática |
| DP-15 | Calificaciones en MVP | Puntuación + comentario para usuarios registrados |
| DP-16 | Antiabuso y moderación de calificaciones | Post-moderación reactiva, filtros, límites y auditoría |
| DP-18 | Separar onboarding, publicación y verificación | Tres ciclos y campos independientes |
| DP-19 | Relación ítem-categoría y taxonomía | `catalog_item_categories`; `kind`; principal; sin ciclos |
| DP-20 | Medios de negocio, sucursal e ítem | Tablas explícitas, sin polimorfismo |
| DP-21 | Consentimiento y evidencia | `business_consents` + evidencia privada |
| DP-22 | Contactos públicos/privados | `contacts` con visibilidad, tipo y consentimiento |
| DP-23 | Slugs, unicidad y redirecciones | `slug_redirects`; sin reutilización ni cadenas |
| DP-24 | Representación de dinero y tipos de precio | `numeric(12,2)`; ISO 4217; `tipo_precio` |
| DP-25 | Alcance de historial/auditoría | `audit_log` append-only con redacción |
| DP-26 | Localidades/zonas y geografía | `localities` MVP; `zones` P1/P2 |
| DP-27 | Moderación de ítems y visibilidad | `estado_moderacion` separado |

### 9.2 Pendientes P1/P2

| Código | Decisión | Prioridad |
|---|---|---|
| DP-04 | Búsqueda: sinónimos, tolerancia, ranking | P1 |
| DP-06 | Fotos: cantidad, almacenamiento, moderación | P1 |
| DP-10 | Negocio cerrado: despublicar o marcar | P1 |
| DP-13 | Léxico local y sinónimos | P1 |
| DP-11 | Fórmula de banderas de confianza | P2 |
| DP-12 | Variantes/SKU en MVP | P2 |
| DP-14 | Catálogo por sucursal para productor/tienda | P2 |
| DP-17 | Fórmula de destacados | P2 |
| DP-28 | Precio/disponibilidad por sucursal | Futuro |

Esta revisión no cierra decisiones P0 por sí misma. Las propuestas que requieran ratificación permanecen abiertas en el registro vigente; ninguna migración ni implementación queda autorizada por este documento.

## 10. Cobertura de los criterios de aceptación

> Esta tabla describe cobertura de la propuesta; no constituye aprobación del modelo ni prueba de implementación.

| Criterio | Cómo se cubre |
|---|---|
| Diferencia clara entre producto/servicio y disponibilidad/stock | `tipo`, `estado_publicacion`, `estado_moderacion`, `estado_disponibilidad`; `confirmado_en` solo disponibilidad; sin stock numérico |
| Se documentan relaciones e invariantes principales | Sección 5 y `06_modelo_datos_v0.4.md` |
| Datos privados y retención quedan señalados | Sección 7 y matriz de retención con plazos definidos y validación legal previa a producción |
| Revisar negocio, sucursales, membresías, categorías, productos/servicios e imágenes | Secciones 3.1 a 3.7 y modelo v0.4; los detalles propuestos no se consideran aprobados en conjunto |
| Aclarar estados de publicación, disponibilidad y confirmación de vigencia | Secciones 3.1, 3.2 y 4.3; umbrales 30/60/90 y frescura derivada |
| Identificar integridad, historial, índices y datos que no deben exponerse | Secciones 5, 6 y 7 |
| Registrar dudas de sucursales MVP y precios por sucursal | Sección 3.3 y DP-28 |
| Modelo conceptual revisado y decisiones priorizadas | `06_modelo_datos_v0.4.md` y sección 9; aprobación integral no afirmada |
| Cobertura, catálogo, contacto y registro coherentes | Secciones 3.10 a 3.12 y modelo v0.4; los detalles propuestos siguen sujetos a ratificación |
| Calificaciones: acuerdos base ratificados; formato y operación pendientes | Sección 1, sección 3.9, política 20 y modelo v0.4 |

## 11. Próximos pasos locales

1. Revisar `06_modelo_datos_v0.4.md` junto con el registro vigente `DECISIONES_PENDIENTES.md`.
2. Ratificar explícitamente las propuestas todavía abiertas; no inferir cierres a partir de las resoluciones de esta revisión ni del modelo v0.4.
3. Mantener pendientes los plazos de retención, eliminación/anonimización y demás validaciones legales/de privacidad.
4. No modificar los adjuntos originales de ClickUp ni otros documentos fuente como parte de esta revisión.
5. No crear migraciones ni código hasta que el modelo completo reciba aprobación explícita.

## 12. Impacto en documentos fuente

Esta sincronización actualiza la revisión local v0.4 y el registro local `DECISIONES_PENDIENTES.md`; no modifica las copias de `01`, `02`, `17`, `README_Indice`, `16` ni `10`, ni los adjuntos originales de ClickUp. Los cambios siguientes son propuestas para revisar tras las ratificaciones correspondientes; no implican aprobación ni implementación:

- `01`: cambiar RF-020 de “cualquier visitante” a usuario registrado con correo verificado; agregar requisito de registro de visitante; confirmar RF-021.
- `02`: reemplazar RN-027 por la política de puntuación + comentario; aclarar en RN-030 que calificar/comentar requiere cuenta.
- `17`: mover calificaciones al MVP, documentar alias, retención, reportes y moderación reactiva.
- `README_Indice`: mover calificaciones a la lista de funcionalidades MVP.
- `16`: retirar `published` del ciclo de onboarding; la publicación vive en `businesses.publication_status`.
- `10`: reflejar post-moderación reactiva y los límites de calificaciones.
