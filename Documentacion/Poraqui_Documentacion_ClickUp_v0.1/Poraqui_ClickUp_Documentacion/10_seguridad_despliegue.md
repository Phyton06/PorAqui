# 10. Seguridad, respaldos y despliegue

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Responsable técnico / operaciones  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** Salvo las reglas de calificaciones expresamente ratificadas por el líder del proyecto y detalladas en `20_politica_calificaciones_moderacion.md`, este documento conserva controles en borrador y requiere validación antes de producción.

## Objetivo
Proteger cuentas, catálogos, negocios y reputación desde el piloto, sin depender de que el proveedor gratuito resuelva todas las obligaciones de seguridad.

## Controles mínimos de seguridad
1. **Identidad:** autenticación gestionada o propia bien probada; invitaciones firmadas/aleatorias, temporales, de un solo uso; revocación de acceso.
2. **Autorización:** verificar en servidor cada edición y lectura privada por membresía; probar acceso horizontal entre dos negocios distintos.
3. **Entradas:** validar texto, URL, teléfono, coordenadas y tipos de archivo; evitar inyección, XSS, SSRF y abuso de subidas.
4. **Fotos:** límite técnico razonable de tamaño por archivo, mime real validado, conversión segura, metadatos privados eliminados cuando corresponda, bloqueo de contenido malicioso.
5. **Datos privados:** HTTPS, credenciales fuera del repositorio, permisos de cloud mínimos, backups protegidos y acceso restringido.
6. **Abuso:** rate limits para reportes, contacto, invitaciones, login y búsqueda; registro suficiente para investigar incidentes.
7. **Dependencias:** actualizaciones y revisión de alertas; control de cambios con PR.
8. **Calificaciones:** una señal de volumen activa revisión humana, pero no pausa nuevas calificaciones ni oculta automáticamente una calificación. Solo después de revisión humana puede un moderador autorizado ocultar provisionalmente una calificación individual, con motivo y auditoría; no borrar por volumen ni despublicar automáticamente el negocio. No hay umbrales ni ventanas numéricas aprobados para automatización; cualquier propuesta futura requiere evidencia del piloto, aprobación explícita y controles contra abuso. Proteger identificadores de cuenta y validar antes de producción los plazos de apelación y retención.

## Entornos y publicación
- **Development:** datos ficticios o anonimizados.
- **Staging:** flujos completos con prueba controlada, URL no indexada, claves separadas.
- **Production:** dominio real, monitoreo, recuperación y permisos mínimos.

## Checklist de release
- Tests críticos verdes.
- Migraciones compatibles y reversibles cuando sea viable.
- Backup verificado antes de cambios de esquema riesgosos.
- Protección SEO: bloquear indexación de staging y pantallas privadas.
- Verificar flujos: invitación, editor de catálogo, búsqueda, compartir y reportar.
- Revisar métricas de error y consumo tras publicación.
- Plan de rollback y responsable de atención.

## Estrategia de respaldos
Exportar datos estructurados regularmente, almacenar copia en ubicación separada del proveedor principal, documentar responsable y frecuencia (por definir), cifrar si contiene información privada y **probar restauración** en entorno aislado. Considerar respaldos de imágenes y de configuraciones necesarias para reconstruir el servicio.

**Responsable asignado y evidencia para ADR-006:** el usuario queda a cargo de coordinar las tareas de seguridad y recuperación: validar reglas de autorización con el líder técnico, asegurar pruebas de aislamiento entre negocios, exportaciones/cifrado/alertas y simulacros de restauración. **Adrian Gallardo (Chimi) es el suplente designado por el usuario**; los fundadores conservan la titularidad de las cuentas institucionales. Antes de producción, habilitar y comprobar el acceso institucional de emergencia del titular y su suplente, con MFA, permisos mínimos y procedimiento de relevo; esta designación no concede acceso por sí misma. El usuario fija un **RPO máximo de 24 horas**, por lo que se requiere programar respaldos al menos diarios y comprobar el intervalo efectivo mediante restauración. Antes de producción, registrar prueba de acceso cruzado rechazada, fecha/operador/resultado e integridad de restauración aislada, frecuencia, retención y RTO aprobados. El responsable y suplente están asignados; el acceso, parámetros operativos y pruebas todavía no están completados. El costo total debe incluir almacenamiento, operaciones de lectura/escritura, transferencia, cómputo de restauración, retención y copias externas; no evaluar solo el precio de la base o el egreso de objetos.

## Riesgos de planes gratuitos
Suspensiones por inactividad, cambios de cuota/precio, límites de CPU, ancho de banda, almacenamiento, correos y operaciones. Mantener alertas y un plan de migración a pago cuando el uso real lo justifique. No prometer SLA que ningún proveedor ofrezca.

## Respuesta a incidentes
**Detectar** → **contener** → **investigar** → **recuperar** → **comunicar cuando corresponda** → **documentar aprendizaje**. Clasificar por pérdida de datos, exposición de información, compromiso de credenciales y disponibilidad. Consultar obligaciones legales de notificación aplicables con especialista.

## Gestión de acceso a proveedores
Crear cuentas institucionales bajo control de NextWare; activar MFA; al menos dos personas autorizadas con procesos de recuperación; documentar propiedad de dominio, facturación, repositorios y cuentas técnicas; revocar accesos al salir integrantes.

## Pendientes
Proveedor final, calendario de backups, objetivo RPO/RTO, canales de alertas, inventario de secretos, política de retención y procedimiento de incidentes aprobado.
