# 08. Guía de instalación y desarrollo local

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Responsable de repositorio + DevOps  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** No es una decisión aprobada hasta que el equipo la valide y actualice el estado.

## Estado
Plantilla operacional **pendiente de concretar tras crear/autorizar repositorio e implementación**. La arquitectura frontend/API ya es Next.js + NestJS; los proveedores y comandos aún no están elegidos. Los comandos mostrados son ejemplos, no instrucciones verificadas para un repositorio existente.

## Requisitos previos
- Git y editor de código.
- Runtime y gestor de paquetes según decisión técnica (por ejemplo Node.js y npm/pnpm).
- Acceso a repositorios de NextWare mediante cuentas individuales.
- Credenciales para entorno de desarrollo entregadas por canal seguro, nunca en el chat de ClickUp ni en el repositorio.
- Si se usa PostgreSQL local, definir versión compatible y migraciones.

## Arranque esperado (pseudoguía)
```bash
# 1. Clonar el repositorio (sustituir por URL real)
git clone <URL_REPOSITORIO>
cd <CARPETA_PROYECTO>

# 2. Instalar dependencias (comando por confirmar)
<COMANDO_INSTALACION>

# 3. Crear configuración local
cp .env.example .env.local

# 4. Preparar la base de datos / migraciones
<COMANDO_MIGRACIONES>

# 5. Iniciar desarrollo
<COMANDO_DEV>
```
**No inventar ni publicar tokens reales** en esta documentación.

## Variables de entorno — categorías esperadas
`PUBLIC_SITE_URL`, conexión a base de datos, credenciales servidor de objetos, proveedor de auth, claves de correo, configuración de mapa y mecanismos de rate limit. La lista exacta dependerá del stack; separar variables públicas de secretos y definir permisos mínimos.

## Datos de prueba
Usar negocios **ficticios** claramente marcados en entorno de desarrollo; no copiar datos personales de comerciantes reales ni subir respaldos de producción a equipos sin autorización.

## Procedimiento de trabajo
1. Consultar [01 alcance](01_alcance_requisitos_mvp.md), la decisión de arquitectura Next.js + NestJS en [14 ADR](14_registro_decisiones_adr.md) y la tarea de ClickUp asignada.
2. Revisar [02 reglas](02_reglas_negocio.md), [05 arquitectura](05_arquitectura.md) y [09 estándares](09_estandares_desarrollo.md); seleccionar proveedores según `DECISIONES_PENDIENTES.md` antes de implementar.
3. Crear rama breve, desarrollar con pruebas y abrir PR.
4. Ejecutar checks automáticos; pedir revisión; fusionar tras aprobación.
5. Verificar entorno de staging antes de producción.

## Diagnóstico de errores comunes
- **No conecta DB:** comprobar URL, red, certificados, credenciales y estado del servicio.
- **No aparecen fotos:** revisar firmas, CORS, permisos de objeto, ruta y caché.
- **No cargan mapas:** validar proveedor, atribución y límites.
- **No llega invitación:** revisar proveedor SMTP, cuota y estado del dominio.
- **Error de autorización:** comprobar membresía de negocio, rol y políticas RLS.

## Hallazgos de evaluación arquitectónica

Esta guía sigue siendo una plantilla, no un procedimiento ejecutable: depende de que el equipo autorice repositorio e implementación y seleccione proveedores. La arquitectura acordada es Next.js + NestJS. Antes de una implementación futura, el responsable de repositorio/DevOps debe documentar versiones, comandos, variables, entornos, migraciones, seed ficticio y responsables de credenciales; el responsable operativo debe verificar que el entorno local no use datos ni secretos de producción.

## Pendientes para convertir en guía ejecutable
URL real del repositorio, stack y versiones, `README` técnico, comandos confirmados, seed, variables exactas, ambientes dev/staging/production y responsables de credenciales.
