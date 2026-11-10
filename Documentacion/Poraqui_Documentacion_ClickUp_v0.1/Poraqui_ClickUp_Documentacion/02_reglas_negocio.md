# 02. Reglas de negocio

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Responsable de producto + administración comercial  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** No es una decisión aprobada hasta que el equipo la valide y actualice el estado.

## Propósito
Definir comportamientos que deben cumplirse con independencia de la tecnología empleada. Cada regla identificada puede convertirse en casos de prueba.

## Negocios y altas
- **RN-001:** El registro, la ficha pública y el catálogo básico son gratuitos de manera permanente según el modelo actual.
- **RN-002:** Al inicio, NextWare invita negocios mediante visitas presenciales o recibe solicitudes por WhatsApp. **No existe alta automática pública**.
- **RN-003:** Solo administradores designados pueden aprobar un establecimiento y habilitar su administración.
- **RN-004:** Antes de aprobar, se comprueba la existencia del establecimiento y la autorización del solicitante; la evidencia requerida se define en el procedimiento operativo.
- **RN-005:** Un negocio puede tener varios administradores autorizados y una persona puede gestionar varios negocios; todos los permisos deben ser explícitos.
- **RN-006:** El rechazo de un alta debe quedar documentado y admitir revisión si existen datos adicionales.
- **RN-007:** No pueden publicarse establecimientos ficticios ni información presentada como verificada cuando no lo está.

## Catálogo y publicación
- **RN-008:** Los comerciantes no pagan por publicar más productos o servicios; se aplican límites técnicos razonables por formato, tamaño y abuso.
- **RN-009:** Precio, fotografía y disponibilidad precisa son opcionales. No inferir que hay existencias si no se dispone de datos.
- **RN-010:** Todo producto/servicio publicado pertenece a un negocio autorizado. Las URL compartidas deben ser estables o redirigirse tras cambios de nombre.
- **RN-011:** El propietario puede editar y despublicar sus artículos, sujeto a trazabilidad administrativa.
- **RN-012:** Distinguir entre **ofrecido sin stock confirmado**, **disponible confirmado**, **agotado temporalmente** y **ya no comercializado**.
- **RN-013:** El artículo agotado temporalmente no se elimina definitivamente; los filtros por disponibilidad pueden ocultarlo por defecto si está confirmado agotado.
- **RN-014:** Un artículo descontinuado confirmado se despublica de las búsquedas activas, conservando historial administrativo el tiempo autorizado.
- **RN-015:** Si hay integración futura con un SaaS POS, el sistema de inventario correspondiente será fuente de verdad del stock; PorAquí conserva solo la vista pública autorizada.

## Reportes ciudadanos
- **RN-016:** Se podrán reportar cierres aparentes, agotados, artículos ya no vendidos e información incorrecta.
- **RN-017:** Un reporte no elimina ni suspende automáticamente negocio/producto; exige verificación proporcional al riesgo.
- **RN-018:** El propietario debe contar con un canal para responder, corregir o impugnar el reporte.
- **RN-019:** Limitar abuso, reportes repetidos y suplantación; moderación y motivos de resolución auditables.

## Actualización y recordatorios
- **RN-020:** La ficha conserva fecha de última confirmación de vigencia, que no equivale a existencia garantizada de cada producto.
- **RN-021:** Los recordatorios se envían con frecuencia configurable y canales permitidos; no saturar al comerciante.
- **RN-022:** «Todo sigue igual» actualiza la fecha de revisión, sin crear inventarios ficticios.

## Búsquedas, confianza y publicidad
- **RN-023:** Una coincidencia patrocinada futura debe indicar **Patrocinado** de manera visible.
- **RN-024:** Pagar publicidad no equivale a comprar mejores reseñas o falsear disponibilidad.
- **RN-025:** Los resultados orgánicos se ordenan por criterios documentados de relevancia, cobertura y calidad del dato; no prometer distancia precisa sin ubicación confirmada.
- **RN-026:** La falta de disponibilidad verificada debe comunicarse como «Consultar existencia» o equivalente, no como «Disponible».
- **RN-027:** Las calificaciones públicas forman parte del MVP. Solo cuentas con contacto verificado pueden calificar; cada cuenta mantiene una calificación vigente de 1 a 5 estrellas por negocio y puede editarla. No se permiten comentarios ni respuestas públicas en el MVP.
- **RN-031:** El perfil muestra promedio y cantidad de calificaciones visibles desde que exista al menos una; las calificaciones ocultas durante revisión no se incluyen.
- **RN-032:** Una calificación reportada puede ocultarse provisionalmente para revisión humana. No habrá ocultamiento automático por volumen hasta observar tráfico del piloto y acordar/documentar sus umbrales y ventana; una señal activada será indicio para revisar, no prueba de abuso. La revisión no suspende el negocio ni elimina definitivamente la calificación por sí sola; toda decisión queda auditada.
- **RN-033:** El usuario puede apelar privadamente el ocultamiento dentro de los 30 días posteriores al aviso. La apelación recibe revisión humana y resolución documentada.
- **RN-034:** Las calificaciones ocultas y su historial de moderación se conservan por 12 meses desde la resolución del caso; después se eliminan o anonimizan conforme a la política de privacidad y obligaciones aplicables.

## Acceso y datos
- **RN-028:** Las fichas son públicas; datos internos, incidencias y métricas personales requieren permisos.
- **RN-029:** Compartir datos con otros SaaS es optativo y regido por permisos y finalidades; el inicio de sesión único es una fase posterior.
- **RN-030:** El usuario puede buscar y contactar sin crear cuenta. Si se requiere cuenta para reportar, se deberá justificar y documentar antes de implementar.

## Casos límite obligatorios
Negocio dupicado; comerciante que pierde acceso; negocio con varias sucursales; artículos con el mismo nombre; ubicación sin coordenadas; enlace compartido a producto despublicado; usuario que reporta maliciosamente a un competidor; negocio sin actualización durante meses.

## Pendientes
Calendario de recordatorios; criterios de aprobación con evidencia; política de visibilidad de negocios no actualizados; límites antiabuso; reglas detalladas de autenticidad, duplicados, moderación, reclamación y retención de calificaciones; política de publicidad de futuras fases.
