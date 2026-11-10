# PorAquí — Vistas e interacciones v0.2

**Alcance:** especificación del prototipo visual de búsqueda, ficha de negocio, acceso, panel de catálogo y calificaciones. La interfaz no está conectada a servicios. Los negocios, precios, ubicaciones y cantidades son datos ficticios.

**Archivos:** `PorAqui_DesignBoard_v02.fig` es el tablero editable canónico de OpenPencil; `PorAqui_DesignBoard_v02.html` es la fuente de importación; `PorAqui_DesignBoard_v02.png` y las imágenes `PorAqui_*_v02.png` son vistas previas. Después de importar, se normalizaron 27 capas como componentes de OpenPencil y se ajustaron coordenadas a píxeles enteros; volver a importar el HTML recrea la estructura inicial y requiere repetir esas normalizaciones.

**Comprobación:** OpenPencil v0.16.0, preset `strict`: 0 errores y 0 advertencias tras normalizar el tablero.

## Navegación y búsqueda — escritorio 01 / móvil 06

**Qué resuelve esta pantalla:** permite descubrir negocios por texto o categoría en Santiago Ixcuintla. Escritorio prioriza la búsqueda y varias fichas a la vez; móvil conserva búsqueda, filtros y resultados en una sola columna cómoda para desplazarse.

| ID | Control | Al pulsarlo / cambiarlo |
|---|---|---|
| S-01 | Explorar | Abre la búsqueda local. Si ya está ahí, no cambia la pantalla. |
| S-02 | Cómo funciona | Muestra una explicación breve de la plataforma y de la verificación de negocios. |
| C-01 | Para comercios | Abre el acceso al panel de comerciante; sin sesión, muestra la pantalla A-01. |
| A-01 | Iniciar sesión / Cuenta | Abre acceso. Después de autenticarse, vuelve a la acción que originó el acceso. |
| S-04 | Campo de búsqueda | Permite escribir negocio, producto o servicio; conserva la localidad seleccionada. |
| S-05 | Buscar | Actualiza resultados con texto y localidad. Mientras carga, muestra progreso; sin coincidencias, muestra un estado vacío con opción de cambiar búsqueda o categoría. |
| S-06 | Categorías | Selecciona una categoría y filtra resultados; «Todo» limpia el filtro. La selección activa queda visible. |
| S-09 | Ver todas | Despliega el resto de las categorías disponibles sin borrar la búsqueda actual. |
| S-07 | Ver en el mapa / Ver mapa | Cambia a mapa con la misma oferta relevante; la lista conserva sus filtros al volver. Solo ubica negocios con coordenadas confirmadas. |
| S-08 | Ficha de resultado | Abre la ficha pública de ese negocio. El resultado incluye categoría, localidad, estado verificado y promedio/conteo de calificaciones visibles. |
| A-01 | Cuenta móvil | Abre el acceso/perfil contextual. No hay una función de guardados en este alcance del MVP. |

## Ficha del negocio — escritorio 02 / móvil 07

**Qué resuelve esta pantalla:** presenta información pública y autorizada de un negocio, su calificación visible, productos, ubicación y acciones de contacto. La versión móvil prioriza nombre, confianza, contacto y catálogo sin esconder las acciones principales.

| ID | Control | Al pulsarlo / cambiarlo |
|---|---|---|
| P-01 | Contactar por WhatsApp | Abre WhatsApp al canal comercial configurado con un mensaje inicial preparado; no lo envía automáticamente. Si el canal no existe, muestra «Contacto no disponible». |
| P-02 | Cómo llegar | Abre la aplicación de mapas con la ubicación confirmada. Si faltan coordenadas verificadas, muestra la dirección textual y no inventa una ruta. |
| P-03 | Llamar al negocio | Inicia la llamada al teléfono comercial publicado; si no está configurado, muestra «Teléfono no disponible». |
| P-04 | Calificar negocio | Con sesión y contacto verificado, abre R-01. En otro caso, abre A-01 y luego continúa a R-01. Si ya calificó, R-01 carga su calificación vigente para editarla. |
| P-05 | Producto del catálogo | Abre el detalle compartible del producto. La disponibilidad no confirmada se muestra como «Consultar existencia»; nunca se infiere que hay stock. |
| P-06 | Volver en móvil | Regresa a los resultados y conserva la búsqueda, localidad y categoría anteriores. |
| P-07 | Menú de la ficha | Abre opciones secundarias para compartir o reportar información del negocio; reportar inicia una solicitud de revisión, no lo despublica. |
| — | Promedio y cantidad | Muestra únicamente calificaciones visibles. Las ocultas durante revisión se excluyen; con cero calificaciones no se presenta un promedio ficticio. |

## Acceso y verificación — móvil 03

**Qué resuelve esta pantalla:** solicita una cuenta con contacto verificado solo cuando la persona intenta calificar. Explica por qué se necesita la cuenta y que el contacto no será público; cerrar devuelve a la ficha sin bloquear la navegación pública.

| ID | Control | Al pulsarlo / cambiarlo |
|---|---|---|
| A-01 | Iniciar sesión / Cuenta | Abre la pantalla de acceso contextual a la acción pendiente. La búsqueda y las fichas públicas siguen disponibles sin cuenta. |
| A-02 | Continuar | Valida el correo o teléfono y avanza al paso de verificación del contacto. El medio exacto (código o enlace) depende del proveedor de autenticación, que sigue pendiente de elección en ADR-006. Un error aparece junto al campo y conserva lo escrito. |
| A-03 | Crear una cuenta | Inicia el registro y la verificación de contacto; al terminar, retorna a la calificación que se intentaba publicar. |
| A-04 | Cerrar | Cierra el acceso y vuelve a la ficha sin iniciar sesión. |

## Panel y catálogo — escritorio 04 / móvil 08

**Qué resuelve esta pantalla:** permite a una persona autorizada mantener el catálogo del negocio. Escritorio muestra navegación y varias filas de productos; móvil convierte cada fila en una ficha compacta con edición accesible.

| ID | Control | Al pulsarlo / cambiarlo |
|---|---|---|
| M-01 | Resumen | Muestra estado del negocio y accesos a tareas pendientes. |
| M-02 | Mi catálogo | Abre productos y servicios administrables por la membresía activa. |
| M-03 | Reportes | Abre reportes del negocio que el comerciante tiene permiso de atender; no otorga acceso a otros negocios. |
| M-04 | Vigencia | Muestra la fecha de última confirmación y permite confirmar «todo sigue igual» o editar información. |
| M-05 | Agregar producto | Abre un formulario con nombre requerido; tipo, descripción, precio y fotografía opcionales; disponibilidad explícita. No solicita ni inventa inventario no confirmado. |
| M-06 | Editar | Abre el mismo formulario precargado para ese producto. Guardar actualiza solo si el servidor valida la membresía y los permisos; cancelar descarta cambios locales. |
| M-07 | Disponibilidad | Permite elegir «Consultar existencia», «Disponible confirmado», «Agotado temporalmente» o «Ya no comercializado». Guardar actualiza la etiqueta pública; agotado no borra el producto. |
| M-08 | Menú móvil | Abre Resumen, Reportes, Vigencia, selección de negocio, Ayuda y Cerrar sesión. |
| — | Guardar formulario | Muestra estado de guardado. En éxito cierra el formulario, actualiza la fila y la ficha pública; en error conserva los datos y presenta el motivo junto al campo o formulario. |
| — | Navegación móvil | Catálogo, Reportes y Negocio abren sus secciones; el encabezado «Menú» muestra las demás rutas del panel. Cuenta abre el perfil de la sesión activa. |

## Calificación — móvil 05

**Qué resuelve esta pantalla:** permite seleccionar una calificación de 1–5 estrellas, revisarla y publicarla desde una cuenta verificada. No solicita comentario público; cancelación vuelve a la ficha y el estado exitoso actualiza su promedio y cantidad visibles.

| ID | Control | Al pulsarlo / cambiarlo |
|---|---|---|
| R-01 | Selector de estrellas | Selecciona de 1 a 5 estrellas y anuncia el valor elegido. Una cuenta conserva una calificación vigente por negocio; si ya existe, el formulario permite editarla. |
| R-02 | Publicar calificación | Valida sesión/contacto verificado y guarda la puntuación. En éxito muestra confirmación y regresa a la ficha con promedio y conteo recalculados. En error conserva la selección y ofrece corregir o reintentar. No hay comentario ni respuesta pública en el MVP. |
| R-03 | Cancelar / Volver | Regresa a la ficha sin guardar cambios pendientes. |

## Estados, seguridad y accesibilidad

- Los flujos de carga, vacío y error deben explicar qué ocurre y cómo continuar; no se atribuyen permisos solo por conocer un identificador.
- Una cuenta solo puede editar su propia calificación. Una acción de comerciante se valida en servidor contra la membresía del negocio.
- Una calificación reportada puede ocultarse provisionalmente para revisión humana. No se fija un umbral automático antes del piloto; su apelación es privada dentro de 30 días.
- Los botones deben tener foco visible, etiquetas legibles y áreas táctiles de al menos 44 × 44 px en móvil. El color nunca será el único indicador de estado.
- El proveedor de autenticación, los nombres/datos reales, el mapa y el canal oficial de WhatsApp siguen sin decidirse; esta propuesta no selecciona ninguno.
