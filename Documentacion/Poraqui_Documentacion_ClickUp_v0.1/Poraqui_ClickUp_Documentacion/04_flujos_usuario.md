# 04. Flujos de usuario

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Liderazgo de producto / técnico  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** Salvo lo marcado expresamente como ratificado por el líder del proyecto, este documento conserva flujos en borrador; los aspectos legales/operativos siguen sujetos a validación.

## Propósito
Describir recorridos principales de extremo a extremo para que producto, diseño, desarrollo y pruebas tengan la misma interpretación.

## FU-01. Buscar y contactar a un negocio
1. Una persona abre PorAquí desde navegador, buscador o enlace externo.
2. Escribe un producto, servicio o nombre de establecimiento.
3. El sistema muestra coincidencias relevantes, con etiqueta del tipo de resultado y zona cuando está disponible.
4. Puede alternar entre resultados y mapa, y entrar al perfil del negocio.
5. Consulta catálogo, horario, ubicación y contacto.
6. Pulsa WhatsApp, llamada o cómo llegar; se registra un evento mínimo de interacción.

**Alternativas:** búsqueda vacía; resultados irrelevantes; comercio sin coordenadas; sin WhatsApp; artículo descontinuado. **Criterio:** siempre dar salida comprensible y no inventar disponibilidad.

## FU-02. Compartir catálogo desde Facebook
1. Comerciante abre su panel.
2. Selecciona página o producto.
3. Copia enlace o genera publicación desde plantilla básica si está habilitada.
4. Publica manualmente en Facebook/WhatsApp.
5. Visitante entra directamente a ficha/producto; no es obligado a crear una cuenta.
6. Puede navegar a otros productos o contactar al comercio.

**Alternativas:** ficha no publicada; fotografía pendiente de procesamiento; vista previa social en caché; producto eliminado. **Criterio:** la URL entrega información consistente o redirección informativa.

## FU-03. Solicitud de alta por WhatsApp
1. Interesado pulsa «Registrar mi negocio».
2. Se abre WhatsApp hacia el contacto oficial de NextWare con mensaje prellenado.
3. El equipo conversa, verifica existencia y autorización de la persona.
4. Un administrador captura información y aprueba o solicita documentación adicional.
5. Al aprobar, se envía invitación segura para activar la cuenta.
6. El comerciante entra al panel y publica su ficha/catalogo.

**Alternativas:** sin WhatsApp; contacto no responde; duplicado; solicitante sin autorización; solicitud rechazada. **Criterio:** nadie administra un negocio sin verificar autorización.

## FU-04. Editar producto
1. Comerciante autenticado elige uno de sus negocios.
2. Abre catálogo y edita nombre, categoría, descripción, foto, precio opcional y estado.
3. Valida campos y publica; el sistema mantiene registro de modificación.
4. La ficha pública y la búsqueda se actualizan según el mecanismo técnico definido.

**Alternativas:** carga fallida; imagen insegura; internet inestable; edición simultánea; producto sin stock confirmado. **Criterio:** no perder datos silenciosamente.

## FU-05. Reportar información incorrecta
1. Visitante selecciona «Reportar un problema» en negocio/producto.
2. Elige motivo: posible cierre, agotado temporal, ya no se vende o datos incorrectos.
3. Envía detalle opcional; se aplican controles contra abuso.
4. El reporte queda pendiente, sin modificar automáticamente la disponibilidad.
5. Comerciante/admin recibe notificación o tarea.
6. Se confirma, corrige o rechaza con explicación y trazabilidad.

## FU-06. Recordatorio de vigencia
1. Transcurre el periodo configurado o llega un reporte relevante.
2. Se envía un aviso al comerciante por canal autorizado.
3. El comerciante elige «Todo sigue igual» o «Revisar catálogo».
4. Se guarda fecha de confirmación o correcciones.
5. El sistema evita enviar notificaciones redundantes.

## FU-07. Explorar portada y destacados
1. El visitante ve categorías, negocios y productos/servicios destacados, además de espacios promocionales identificados.
2. Los destacados consideran categoría, ubicación, rotación, búsquedas y calificaciones; el equipo puede seleccionar manualmente.
3. La publicidad pagada queda para una etapa posterior y deberá identificarse claramente.

## FU-08. Calificar un negocio y proteger reseñas
1. Una persona consulta las calificaciones públicas; para enviar una debe iniciar sesión con una cuenta cuyo contacto esté verificado (elegibilidad ratificada por el líder del proyecto).
2. El borrador del MVP propone una calificación de 1 a 5 estrellas por cuenta y negocio, editable, sin comentarios ni respuestas públicas; confirmar edición y duplicados en equipo antes de implementarlos.
3. Un reporte o señal de anomalía genera una tarea en la cola interna; no pausa automáticamente nuevas calificaciones ni oculta una reseña por volumen solamente.
4. Un moderador autorizado revisa el caso. Después de revisión humana puede ocultar provisionalmente la calificación individual y registra motivo, evidencia pertinente, responsable y fecha/hora.
5. Si la oculta, avisa al autor en privado y permite apelación privada dentro de 30 días del aviso. El plazo está sujeto a revisión legal/documental.
6. La apelación recibe revisión humana y una resolución registrada. Si no se documenta infracción, se restaura la calificación; toda medida que la mantenga oculta requiere infracción y motivo documentados. Las categorías de infracción y medidas finales siguen pendientes.
7. La identidad del autor y los detalles de moderación no se publican. Una calificación oculta no se cuenta en promedio/conteo públicos; ninguna anomalía despublica el negocio ni elimina automáticamente reseñas.

**Criterio:** el reporte o pico no produce efecto público automático; solo un moderador autorizado puede ocultar provisionalmente una calificación tras revisión humana. Véase `20_politica_calificaciones_moderacion.md`.

## Flujos futuros — no implementarlos todavía
Reserva desde PorAquí hacia SaaS de barbería con SSO; compra integrada; inventario conectado; publicidad pagada/automatizada; mandaditos.

## Evidencia de diseño pendiente
Wireframes de móvil, estados vacíos/errores, diseño del panel, navegación de catálogo y prototipos accesibles.
