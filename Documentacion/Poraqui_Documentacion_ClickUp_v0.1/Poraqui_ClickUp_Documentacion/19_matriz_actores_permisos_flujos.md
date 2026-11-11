# 19 — Matriz de actores, permisos y flujos

**Estado:** borrador para revisión; no representa una política aprobada ni evidencia de implementación.

## Propósito y convenciones

Este documento consolida los roles, acciones, recursos y flujos descritos en los documentos 03, 04, 10 y 17. Las expresiones **documentado en borrador** y **pendiente de acuerdo** distinguen lo que las fuentes describen de las decisiones que el equipo aún debe ratificar. No se infieren permisos nuevos ni se fijan umbrales, plazos legales o controles no acordados.

La matriz orienta la revisión de autorización por negocio. Antes de implementar permisos, cada operación debe comprobar la membresía y el alcance sobre el negocio o recurso solicitado; conocer o proporcionar un ID no debe otorgar acceso a otro negocio. Los detalles de respuestas HTTP, almacenamiento o políticas de plataforma quedan fuera de este mapa.

## Actores y matriz de acceso

| Actor | Acciones y recursos descritos | Límite de acceso documentado | Estado / preguntas abiertas |
|---|---|---|---|
| Visitante anónimo | Buscar y consultar fichas, catálogo y mapa; usar canales públicos de contacto; enviar reportes según el flujo descrito. | Lectura de contenido público; no administra negocios ni accede a datos internos. La navegación y el contacto no requieren cuenta. | El requisito de autenticación para enviar reportes está pendiente. |
| Cuenta de usuario con contacto verificado | Crear o editar una calificación según las reglas del MVP. | Solo cuentas con contacto verificado pueden calificar (elegibilidad ratificada por el líder del proyecto); la identidad del autor no se publica. | El borrador propone una calificación vigente por cuenta y negocio, editable; confirmar edición y duplicados con el equipo. Véase `20_politica_calificaciones_moderacion.md`. |
| Propietario/administrador de negocio | Gestionar el perfil y el catálogo del negocio al que pertenece. | La gestión se limita al negocio autorizado por su membresía; una persona puede pertenecer a más de un negocio. | Deben concretarse el alcance por sucursal y las acciones de cada nivel de membresía. |
| Colaborador de negocio | Rol opcional propuesto para gestionar contenido con alcance limitado. | No se atribuyen permisos adicionales en este documento. | Está pendiente decidir si existe en el MVP y qué acciones puede realizar. |
| Moderador de NextWare | Revisar reportes y contenido, registrar el resultado y dar seguimiento a la moderación; puede ocultar provisionalmente una calificación individual después de revisión humana. | Acceso limitado a lo necesario; ocultamiento con motivo/responsable/fecha auditados; aviso privado y apelación dentro de 30 días. | El plazo de apelación requiere validación legal; categorías de infracción, medidas finales, permisos detallados y retención siguen pendientes. |
| Administrador designado de NextWare | Verificar negocios, aprobar o rechazar altas, emitir invitaciones y gestionar permisos/configuración según las fuentes. | Funciones administrativas separadas de las funciones del comerciante; las aprobaciones corresponden a administradores designados. | Faltan los permisos detallados, evidencia exigible, separación de funciones y acciones que requieren una segunda aprobación. |
| Superadministrador | Acceso excepcional descrito para incidentes. | Restringido a pocas personas; no se atribuyen acciones ordinarias. | Alcance, activación, auditoría y revisión posterior están sin especificar. |

## Clasificación preliminar de recursos

Esta clasificación recopila categorías mencionadas en el modelo y en privacidad; no reemplaza una revisión campo por campo antes de implementar.

| Clase | Recursos o datos identificados | Regla de acceso que debe verificarse |
|---|---|---|
| Públicos | Ficha del negocio, catálogo publicado, ubicación y canales públicos de contacto. | Visitantes pueden consultar solo los datos que el producto haya definido como públicos. No exponer en la respuesta campos internos por estar junto a datos públicos. |
| Privados de usuario o comerciante | Datos de cuenta y contacto verificado; membresías; invitaciones; evidencia de verificación; identidad vinculada a calificaciones. | Acceso solo al titular o a la función autorizada que lo necesite, de acuerdo con una política pendiente de ratificación. No publicar identidad ni evidencia de verificación. |
| Internos de moderación/administración | Reportes, datos de revisión e historial de moderación; decisiones de aprobación; registros de acceso y auditoría; configuración administrativa. | Acceso por función y necesidad. Las fuentes no fijan el detalle de campos visibles por moderador y administrador; mantenerlo como decisión abierta. |

**Pendiente:** validar la clasificación exacta de cada campo con `06_modelo_datos.md` y `17_datos_privacidad.md`. No inferir plazos de conservación ni afirmar cumplimiento legal; la documentación remite su validación a una persona competente.

## Flujo de alta, verificación e invitación de comercio

```text
Comerciante solicita alta (WhatsApp o visita)
        ↓
Administrador designado verifica existencia del negocio y autorización de quien solicita
        ↓
        ├── No aprobado → registrar/revisar el resultado según el procedimiento pendiente
        └── Aprobado → crear o habilitar el negocio y emitir invitación temporal de un solo uso
                              ↓
                    Comerciante acepta la invitación y activa su acceso
                              ↓
                    Membresía limita la gestión al negocio autorizado
                              ↓
                    Comerciante actualiza perfil y catálogo; registrar cambios
```

El flujo está consolidado de los borradores de reglas, roles y flujos. No se especifican aquí la evidencia mínima, el tratamiento detallado de rechazos, la recuperación de invitaciones vencidas ni la revocación de membresías; son preguntas abiertas, no pasos ya aprobados.

## Flujos de uso, reportes y calificaciones

- **Búsqueda y contacto:** el visitante consulta resultados, mapa o ficha y puede utilizar los canales públicos configurados. No requiere cuenta para buscar. Minimizar la información registrada sobre búsqueda y contacto, según las fuentes.
- **Edición de catálogo:** el comerciante autenticado selecciona un negocio al que pertenece y edita el contenido permitido; no debe poder modificar otro negocio cambiando el identificador del recurso. El alcance exacto del rol colaborador sigue pendiente.
- **Reportes de negocio/catálogo:** el reporte entra en revisión y no debe ocultar ni cambiar automáticamente la disponibilidad del negocio; el acceso a datos del reportante sigue pendiente. Para reportes de calificaciones, aplicar el flujo específico de `20_politica_calificaciones_moderacion.md`.
- **Calificaciones:** solo una cuenta con contacto verificado puede calificar (elegibilidad ratificada por el líder del proyecto). Una señal o reporte genera revisión humana, no una pausa automática ni ocultamiento automático por volumen. Tras revisión, el moderador autorizado puede ocultar provisionalmente una calificación individual, avisar al autor en privado y permitir apelación dentro de 30 días; restaurar si no se documenta infracción. Un pico no prueba abuso ni autoriza borrar reseñas o despublicar el negocio. Umbrales futuros, detalles de edición/duplicados, categorías de infracción y validación legal del plazo permanecen pendientes; véase `20_politica_calificaciones_moderacion.md`.

### Ruta de revisión de reportes o anomalías

```text
Reporte o señal de anomalía
        ↓
Cola interna de revisión (sin efecto público automático)
        ↓
Moderador autorizado revisa la información necesaria y registra la decisión
        ↓
Confirmar/corregir, rechazar o escalar según reglas que el equipo ratifique
        ↓
Notificar/apelar cuando corresponda (mecanismo y alcance pendientes)
```

La enumeración de resultados es una guía de revisión derivada de las fuentes, no una política operativa aprobada. No automatizar suspensión, eliminación o cambio de visibilidad a partir de volumen solamente.

## Casos de prueba de aislamiento entre negocios

Estos son escenarios propuestos para validar autorización horizontal; no afirman que exista una implementación ni fijan una respuesta HTTP concreta.

| Actor / contexto | Acción y recurso | Resultado esperado |
|---|---|---|
| Miembro autorizado del negocio A | Leer o actualizar un campo privado/editable de A. | Permitir solo las operaciones autorizadas para su rol y dejar la actividad trazable donde aplique. |
| Miembro autorizado del negocio A | Repetir la operación usando el ID de un recurso privado de B. | Denegar el acceso; no devolver datos de B ni aplicar cambios a B. |
| Miembro autorizado de A | Enviar un ID de negocio B en una operación de catálogo o perfil. | Denegar; la autorización debe comprobar la relación entre actor, acción y negocio, no solo que el ID exista. |
| Visitante anónimo | Consultar ficha/catálogo público y después intentar acceder a membresías, invitaciones o datos internos. | Permitir la parte pública; denegar datos privados y administrativos. |
| Moderador | Consultar un reporte asignado/revisable y solicitar datos ajenos no necesarios para la revisión. | Permitir solo el acceso de moderación ratificado; denegar o excluir datos ajenos al alcance autorizado. El alcance exacto debe definirse antes de convertirlo en prueba de aceptación. |
| Cuenta con contacto verificado | Registrar o editar una calificación de un negocio diferente. | Aplicar la regla de una calificación por cuenta y negocio cuando el equipo ratifique la política; no inferir límite de volumen ni ocultamiento automático. |

Para cada caso de autorización, comprobar por la interfaz pública que una solicitud denegada no revela datos ni modifica el recurso. Los casos finales, códigos de respuesta y datos de prueba deben definirse junto con la tarea de escenarios de prueba; este documento no los inventa.

## Decisiones abiertas para ratificación

1. ¿Se permite enviar reportes sin iniciar sesión? ¿Qué controles antiabuso se aplican y qué información del reportante necesita el moderador? (DP-07; RN-030.)
2. La elegibilidad está ratificada por el líder del proyecto: solo cuentas con contacto verificado pueden calificar. Confirmar con el equipo los detalles de duplicados, edición y reportes de reseñas (FU-08; DP-15/DP-16).

   **Conflicto resuelto:** FU-08 se actualizó para retirar la propuesta de «cualquier visitante» y la limitación automática ante picos. La política inicial requiere cuenta con contacto verificado y revisión humana; no se pausa la calificación por volumen solamente. Véase `20_politica_calificaciones_moderacion.md`.
3. No hay umbrales ni ventanas numéricas aprobados ni límites automáticos en la política inicial. Si se considera automatización futura, decidirla con evidencia del piloto, controles contra abuso, responsables y apelación. El ocultamiento provisional individual requiere revisión humana; se permite apelación privada dentro de 30 días, pendiente de validación legal. La propuesta de retención por 12 meses no está ratificada. (RN-032–034; DP-10, DP-15 y DP-16.)
4. ¿Se habilita el rol colaborador en el MVP y qué permisos puede tener? ¿Cómo se modela el alcance por negocio y sucursal? (Pendientes de `03_roles_permisos.md`; DP-05.)
5. ¿Qué evidencia verifica un negocio y la autoridad de quien solicita? ¿Qué ocurre con rechazo, invitación expirada y recuperación? (RN-004–006; DP-02/DP-08.)
6. ¿Qué datos privados puede ver cada rol de moderación y administración? ¿Qué operaciones requieren doble aprobación, y cómo se habilita y audita el superadministrador?
7. ¿Qué campos exactos son públicos, privados de usuario/comerciante o internos? ¿Cuáles son sus plazos aprobados de conservación y eliminación/anonimización? Validar con el equipo y asesoría competente; no asumir valores legales.

## Fuentes relacionadas

- `03_roles_permisos.md` — roles, permisos, asignación, flujos de acceso y pendientes.
- `04_flujos_usuario.md` — búsqueda, alta, edición, reportes y calificaciones.
- `10_seguridad_despliegue.md` — controles de autorización, aislamiento y abuso.
- `17_datos_privacidad.md` — clasificación, moderación, calificaciones y privacidad.
- `02_reglas_negocio.md` — reglas de alta, reportes, moderación y reseñas.
- `06_modelo_datos.md` — entidades y relaciones que deben validarse campo por campo.
- `DECISIONES_PENDIENTES.md` — fuente de decisiones aún no ratificadas.
