# 03. Roles y permisos

> **Producto:** PorAquí · **Empresa:** NextWare  
> **Estado:** Borrador para revisión · **Responsable propuesto:** Liderazgo de producto / técnico  
> **Versión:** 0.1 · **Actualizado:** 2026-10-24 · **Cobertura:** Santiago Ixcuintla, Nayarit  
> **Nota:** No es una decisión aprobada hasta que el equipo la valide y actualice el estado.

## Criterio general
Aplicar **mínimo privilegio**: cada identidad puede acceder exclusivamente a los recursos para los que tiene autorización. Los roles globales y los permisos de un negocio son distintos.

## Roles conceptuales
- **Visitante anónimo:** consulta página pública, busca, abre mapa y usa contacto.
- **Usuario autenticado (futuro o cuando sea requerido):** conserva funciones públicas y puede realizar acciones con identidad verificada si se habilitan.
- **Propietario/administrador de negocio:** mantiene su perfil comercial, catálogo, medios y enlaces, y atiende reportes pertinentes.
- **Colaborador de negocio (fase opcional):** permiso limitado para administrar contenido, no acceso a datos de otros negocios.
- **Moderador NextWare:** revisa reportes y contenido, con alcance auditado.
- **Administrador NextWare:** autoriza negocios, invitaciones, permisos y configuraciones operativas.
- **Superadministrador:** acceso excepcional para incidentes, asignado a muy pocas personas.

## Matriz inicial de permisos
| Acción | Visitante | Comerciante propio | Moderador | Administrador |
|---|:---:|:---:|:---:|:---:|
| Buscar / ver fichas públicas | Sí | Sí | Sí | Sí |
| Compartir enlaces | Sí | Sí | Sí | Sí |
| Solicitar registro por WhatsApp | Sí | Sí | Sí | Sí |
| Editar perfil y catálogo | No | Solo asignados | No* | Sí con trazabilidad |
| Revisar reporte de su negocio | No | Solo propios | Sí | Sí |
| Resolver reporte con efecto público | No | Corregir datos propios | Sí | Sí |
| Aprobar negocio / emitir invitación | No | No | No | Sí |
| Ver datos privados de otros negocios | No | No | Solo mínimo necesario | Según función |
| Configurar publicidad futura | No | Solicitar | No | Sí |

\* Un moderador puede gestionar correcciones solo mediante proceso explícito aprobado, no mediante permisos implícitos.

## Reglas de asignación
1. Un usuario no obtiene permisos sobre un negocio por conocer o adivinar su ID.
2. Una identidad puede pertenecer a varios negocios mediante tabla de membresías con rol y estado.
3. Cambios de roles, revocaciones e invitaciones deben auditarse.
4. No compartir cuentas entre empleados; cada persona usa su identidad.
5. Ningún permiso se concede por datos enviados únicamente desde el navegador; validación obligatoria en servidor o políticas de base de datos.

## Flujos de acceso
**Invitación:** administrador verifica negocio → crea invitación temporal → comerciante verifica su contacto → configura acceso → se registra aceptación de términos → membresía activada.

**Revocación:** solicitud verificada → se retira membresía → se invalidan sesiones/credenciales cuando sea técnicamente posible → se conserva evidencia administrativa.

## SSO futuro
Los SaaS independientes de NextWare podrán compartir un proveedor de identidad, pero no sus datos ni autorización automáticamente. PorAquí no necesita SSO multiaplicación para el MVP.

## Pendientes
¿Se permitirá administrar por teléfono sin correo? ¿Existirá el rol de colaborador desde el inicio? ¿Qué acciones administrativas requieren doble aprobación? ¿Se permitirán reportes anónimos con controles antiabuso?
