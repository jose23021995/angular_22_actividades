Armando, este es el plan detallado de los **13 módulos**. Los primeros 12 serán prácticas independientes; el 13 será el proyecto final conectado a tu backend .NET.

Usaremos **[DummyJSON](https://dummyjson.com/docs)** para las prácticas. Sus escrituras son simuladas: cuando necesitemos conservar cambios, lo haremos explícitamente en el estado local de la aplicación.

**Módulo 1 · Administrador de tareas**

**Objetivo:** manejar componentes, formularios sencillos y estado compartido.

1. **Definir el modelo:** crear una interfaz para identificar la tarea, su descripción, estado y usuario.
2. **Consultar tareas:** obtener un listado desde `/todos` mediante un servicio con `HttpClient`.
3. **Mostrar el listado:** separar la página, el formulario y el elemento de tarea en componentes.
4. **Agregar tareas:** capturar una descripción, rechazar texto vacío o compuesto únicamente de espacios y agregarla al estado local.
5. **Editar y completar:** modificar la descripción y alternar el estado sin mutar directamente los objetos.
6. **Eliminar tareas:** permitir eliminación individual con confirmación.
7. **Filtrar:** mostrar todas, pendientes o completadas.
8. **Calcular indicadores:** usar Signals y `computed` para contar tareas por estado.
9. **Persistir:** conservar los cambios localmente y restaurarlos al recargar; consultar la API cuando no haya datos guardados.
10. **Manejar estados:** mostrar carga, error y ausencia de tareas.

**Se completa cuando:** puedes administrar tareas, recargar sin perder los cambios locales y explicar cómo se comunican los componentes.

**Módulo 2 · Directorio de usuarios**

**Objetivo:** construir una tabla y navegar entre listado y detalle.

1. **Definir contratos:** representar los campos necesarios de usuarios y de la respuesta paginada.
2. **Consultar usuarios:** consumir `/users` desde un servicio.
3. **Construir la tabla:** mostrar nombre, correo, teléfono e imagen usando HTML semántico.
4. **Separar componentes:** pasar datos a la tabla mediante inputs y emitir la selección mediante outputs.
5. **Buscar usuarios:** permitir búsquedas y presentar el estado sin coincidencias.
6. **Paginar:** controlar tamaño de página, anterior, siguiente y total.
7. **Crear rutas:** configurar listado y detalle mediante un parámetro de ID.
8. **Consultar detalle:** obtener un usuario desde `/users/{id}`.
9. **Manejar errores:** diferenciar un usuario inexistente de un fallo de conexión.
10. **Adaptar la presentación:** permitir consultar tabla y detalle desde celular.

**Se completa cuando:** puedes buscar un usuario, abrir su detalle y regresar al listado sin perder el contexto de navegación.

**Módulo 3 · Cotizador de productos**

**Objetivo:** combinar formularios dinámicos, validaciones y cálculos.

1. **Consultar productos:** obtener opciones desde `/products`.
2. **Crear el formulario:** capturar nombre del cliente y datos generales de la cotización.
3. **Agregar renglones:** utilizar `FormArray` para seleccionar varios productos.
4. **Editar cantidades:** validar números enteros positivos y límites de stock.
5. **Controlar duplicados:** impedir productos repetidos o unificar sus cantidades.
6. **Calcular importes:** obtener subtotal por renglón y subtotal general.
7. **Aplicar descuento e impuesto:** definir reglas explícitas y validar sus límites.
8. **Derivar el total:** conectar los cambios del formulario con los cálculos, sin duplicar estado innecesariamente.
9. **Presentar valores:** usar pipes de moneda y porcentaje con una moneda de práctica claramente definida.
10. **Mostrar resumen:** generar una vista de la cotización válida y permitir restablecerla.

**Se completa cuando:** agregar, quitar o modificar un renglón actualiza todos los importes correctamente.

**Módulo 4 · Catálogo con detalle**

**Objetivo:** practicar presentación reutilizable, pipes y directivas.

1. **Crear tarjetas:** mostrar imagen, nombre, precio y disponibilidad.
2. **Reutilizar componentes:** proporcionar el producto mediante un input y emitir acciones mediante outputs.
3. **Consultar categorías:** cargar las categorías disponibles.
4. **Filtrar por categoría:** actualizar el catálogo y manejar categorías vacías.
5. **Crear un pipe:** truncar descripciones con longitud configurable sin modificar los datos originales.
6. **Crear una directiva:** resaltar productos con stock bajo mediante un umbral configurable.
7. **Configurar detalle:** navegar a `/productos/:id` y consultar `/products/{id}`.
8. **Mostrar información ampliada:** presentar descripción, imágenes, categoría y stock.
9. **Manejar rutas inválidas:** mostrar una alternativa ante un ID inexistente.
10. **Aplicar carga diferida:** cargar las páginas del catálogo y detalle mediante rutas lazy.

**Se completa cuando:** el catálogo reutiliza componentes y el detalle funciona también al entrar directamente por URL.

**Módulo 5 · Buscador reactivo**

**Objetivo:** controlar solicitudes mientras el usuario escribe.

1. **Crear el campo:** utilizar un `FormControl` para la búsqueda.
2. **Normalizar texto:** recortar espacios y definir el comportamiento de la búsqueda vacía.
3. **Aplicar espera:** usar `debounceTime` para agrupar pulsaciones.
4. **Evitar duplicados:** aplicar `distinctUntilChanged` sobre el texto normalizado.
5. **Consultar resultados:** consumir la búsqueda de productos de DummyJSON mediante `switchMap`.
6. **Evitar respuestas antiguas:** comprobar que una búsqueda anterior no sobrescribe la más reciente.
7. **Representar estados:** mostrar búsqueda en curso, resultados, vacío y error.
8. **Mantener vivo el flujo:** permitir nuevas búsquedas después de un error.
9. **Sincronizar la URL:** guardar y restaurar el término mediante query params sin provocar ciclos.
10. **Liberar recursos:** utilizar `async` pipe o una estrategia de limpieza adecuada.

**Se completa cuando:** escribir rápidamente produce resultados de la última búsqueda y un error no inutiliza el buscador.

**Módulo 6 · Carrito de compras**

**Objetivo:** compartir estado entre pantallas.

1. **Consultar catálogo:** obtener productos de DummyJSON.
2. **Crear el servicio:** centralizar productos y cantidades del carrito.
3. **Agregar artículos:** incrementar la cantidad si el producto ya existe.
4. **Modificar cantidades:** permitir aumentar y disminuir sin superar stock ni aceptar valores inválidos.
5. **Eliminar artículos:** retirar una línea o vaciar el carrito.
6. **Calcular totales:** usar `computed` para artículos, unidades y total.
7. **Actualizar encabezado:** mostrar el contador desde un componente distinto del catálogo.
8. **Construir el resumen:** presentar productos, cantidades, precios e importes.
9. **Persistir:** guardar y restaurar el carrito localmente con validación básica de los datos almacenados.
10. **Comprobar coherencia:** mantener sincronizados catálogo, encabezado y resumen.

**Se completa cuando:** todas las pantallas reflejan los mismos cambios y los totales se derivan de una única fuente de estado.

**Módulo 7 · Administrador de productos**

**Objetivo:** practicar CRUD, formularios y modales.

1. **Consultar productos:** mostrar el listado inicial desde la API.
2. **Crear formulario tipado:** incluir nombre, descripción, precio, stock y categoría.
3. **Validar entradas:** aplicar campos obligatorios, longitudes, mínimos y rechazo de espacios.
4. **Crear producto:** practicar el POST simulado y agregar el resultado al estado local.
5. **Editar producto:** precargar valores y practicar la actualización de un producto existente.
6. **Eliminar producto:** confirmar y practicar DELETE sobre un registro existente.
7. **Mantener cambios locales:** conservar la representación de las operaciones sin esperar persistencia del servidor de prueba.
8. **Controlar registros recién creados:** identificar que sus IDs simulados pueden no existir en posteriores solicitudes al servidor.
9. **Bloquear doble envío:** deshabilitar acciones mientras hay una operación pendiente.
10. **Manejar errores:** conservar el formulario y mostrar mensajes comprensibles.
11. **Construir un modal accesible:** gestionar apertura, cierre y foco.

**Se completa cuando:** puedes demostrar el flujo CRUD y explicar qué operaciones fueron simuladas y qué cambios viven únicamente en el cliente.

**Módulo 8 · Panel con Tailwind CSS**

**Objetivo:** construir una interfaz consistente y accesible.

1. **Preparar Tailwind:** configurarlo de acuerdo con la versión del proyecto.
2. **Crear el layout:** incluir encabezado, menú, contenido y `router-outlet`.
3. **Configurar rutas hijas:** organizar las secciones del panel.
4. **Diseñar indicadores:** mostrar tarjetas con datos obtenidos de una práctica anterior.
5. **Estilizar tablas:** definir encabezados, filas, acciones y presentación en pantallas pequeñas.
6. **Estilizar formularios:** representar foco, error, deshabilitado y envío.
7. **Crear menú móvil:** permitir abrirlo y cerrarlo mediante controles accesibles.
8. **Unificar componentes:** reutilizar botones, alertas y estados de carga cuando tenga sentido.
9. **Comprobar teclado:** revisar orden del foco, nombres de botones y cierre de menús.
10. **Comprobar tamaños:** revisar celular, tableta y escritorio.

**Se completa cuando:** el panel mantiene sus funcionalidades y resulta usable con teclado y en celular.

**Módulo 9 · Autenticación de prueba**

**Objetivo:** comprender el flujo completo de una sesión.

1. **Revisar el contrato:** identificar los campos de login y respuesta de DummyJSON.
2. **Crear login reactivo:** validar los datos antes de enviarlos.
3. **Consumir autenticación:** utilizar exclusivamente credenciales de prueba.
4. **Crear servicio de sesión:** representar usuario, token y estado de autenticación.
5. **Definir persistencia:** explicar dónde se conservará la sesión y las implicaciones de la decisión.
6. **Consultar identidad:** consumir el endpoint del usuario autenticado.
7. **Crear interceptor:** adjuntar Bearer únicamente al destino autorizado.
8. **Crear guard:** proteger una página privada y conservar una ruta interna de retorno.
9. **Manejar expiración:** cerrar sesión y regresar al login ante una sesión vencida.
10. **Implementar logout:** limpiar sesión y datos privados.
11. **Restaurar sesión:** resolver el estado inicial antes de decidir la navegación.
12. **Comprobar errores:** diferenciar credenciales incorrectas de errores en solicitudes protegidas.

**Se completa cuando:** puedes iniciar sesión, entrar a una ruta privada, recargar y cerrar sesión sin estados inconsistentes.

**Módulo 10 · Editor de perfil**

**Objetivo:** combinar edición, archivos y protección de cambios.

1. **Consultar usuario:** cargar un perfil de prueba.
2. **Precargar formulario:** presentar sus datos en controles tipados.
3. **Validar campos:** comprobar nombre, correo y los campos adicionales definidos.
4. **Mostrar errores:** asociar mensajes con los controles correspondientes.
5. **Seleccionar imagen:** aceptar un archivo desde el navegador.
6. **Validar archivo:** comprobar tamaño y formatos permitidos.
7. **Previsualizar:** mostrar la imagen seleccionada sin subirla todavía.
8. **Liberar recursos:** retirar las referencias temporales utilizadas para la previsualización.
9. **Guardar localmente:** actualizar el perfil de práctica dejando explícita su persistencia local.
10. **Restablecer:** regresar a los últimos valores guardados.
11. **Proteger navegación:** advertir mediante `CanDeactivate` cuando existan cambios pendientes.

**Se completa cuando:** puedes editar y cancelar sin perder el control de los datos ni dejar recursos de imagen pendientes.

**Módulo 11 · Tabla avanzada**

**Objetivo:** coordinar tabla, URL y consultas al servidor.

1. **Definir estado de consulta:** búsqueda, campo de orden, dirección, página y tamaño.
2. **Construir parámetros:** utilizar `HttpParams`.
3. **Consultar páginas:** transformar la página visual en los parámetros `limit` y `skip`.
4. **Mostrar total:** distinguir cantidad global y registros de la página.
5. **Implementar orden:** solicitar ordenamiento en los campos admitidos por la API.
6. **Agregar búsqueda:** combinarla con paginación y orden según las capacidades reales del endpoint.
7. **Reiniciar página:** volver a la primera al cambiar búsqueda o tamaño.
8. **Sincronizar query params:** restaurar la tabla al recargar o compartir una URL.
9. **Cancelar solicitudes:** impedir que respuestas anteriores sustituyan el estado vigente.
10. **Manejar errores y reintentos:** conservar los controles seleccionados.
11. **Separar responsabilidades:** mantener la consulta en el servicio y la presentación en componentes.

**Se completa cuando:** la URL permite reconstruir el listado y los controles producen consultas coherentes.

**Módulo 12 · Pruebas y depuración**

**Objetivo:** comprobar comportamientos y encontrar fallos.

1. **Probar cálculos:** verificar cantidades y totales del carrito.
2. **Probar validadores:** cubrir datos válidos, inválidos y límites.
3. **Probar servicios HTTP:** comprobar método, URL, parámetros y cuerpo.
4. **Simular errores:** verificar respuestas HTTP y estados de interfaz.
5. **Probar componentes:** comprobar acciones visibles del usuario y eventos emitidos.
6. **Probar guards:** verificar acceso y redirecciones.
7. **Probar integración:** comprobar colaboración entre formulario, servicio y navegación.
8. **Depurar solicitudes duplicadas:** localizar su origen y justificar la corrección.
9. **Depurar suscripciones:** detectar recursos que continúan activos al abandonar una pantalla.
10. **Interpretar cobertura:** identificar caminos sin ejercitar sin confundir porcentaje con calidad.
11. **Realizar una práctica de entrevista:** resolver una modificación y explicar el diagnóstico.

**Se completa cuando:** puedes reproducir un fallo, corregirlo y demostrar mediante una prueba que el comportamiento esperado se mantiene.

**Módulo 13 · Proyecto final con tu backend .NET**

**Objetivo:** construir una aplicación Angular completa de administración de usuarios y productos.

Backend:

```text
C:\Users\mtjam\OneDrive\Documentos\netcore\PruebaTecnica.Api
```

1. **Verificar contratos:** revisar endpoints, DTOs, permisos y errores contra el backend actual.
2. **Configurar conexión:** establecer URL base o proxy y comprobar comunicación con la API.
3. **Crear modelos:** representar login, usuario, producto, paginación y errores.
4. **Construir login:** consumir `POST /api/auth/login` mediante un formulario reactivo.
5. **Administrar sesión:** utilizar token, expiración y usuario; resolver restauración y logout.
6. **Configurar interceptor JWT:** enviar credenciales únicamente a tu API.
7. **Proteger navegación:** crear guards de autenticación y acceso administrativo.
8. **Construir layout:** organizar rutas hijas, carga diferida, menú y pantallas con Tailwind.
9. **Listar productos:** consumir `GET /api/productos` con búsqueda y paginación.
10. **Mostrar detalle:** consumir `GET /api/productos/{id}` y manejar productos inexistentes.
11. **Crear productos:** enviar datos e imagen opcional mediante `FormData`.
12. **Editar productos:** precargar datos y permitir conservar o sustituir la imagen según el contrato.
13. **Eliminar productos:** confirmar la acción y actualizar el listado.
14. **Aplicar propiedad y roles:** habilitar acciones según propietario o `Admin` y comprobar las restricciones del servidor.
15. **Listar usuarios:** construir una tabla administrativa con búsqueda y paginación.
16. **Administrar usuarios:** implementar alta, detalle, edición y eliminación según las reglas de la API.
17. **Presentar errores:** distribuir validaciones por campo y diferenciar `401`, `403`, `404` y conflictos.
18. **Reutilizar componentes:** integrar tabla, paginador, modal, mensajes y estados de carga donde resulte útil.
19. **Aplicar pipes y estado reactivo:** presentar fechas e importes y derivar indicadores sin duplicar datos.
20. **Comprobar accesibilidad:** revisar formularios, modales, teclado y responsive.
21. **Agregar pruebas:** cubrir servicios, validadores, guards y flujos principales.
22. **Ejecutar el recorrido final:** probar con un administrador y dos usuarios distintos para comprobar acceso, propiedad y persistencia.

**Se completa cuando:** puedes iniciar sesión, administrar productos con imágenes, comprobar permisos con distintas identidades y gestionar usuarios como administrador, con cambios persistidos realmente en tu backend.