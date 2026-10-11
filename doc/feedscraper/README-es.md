# FeedScraper — guía de uso

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · Español · [Nederlands](README-nl.md)*

Escrita para FeedScraper 0.1.252 (octubre de 2026). Si esta guía y la aplicación no dicen lo mismo,
la aplicación tiene razón.

---

## 1. Qué es FeedScraper

FeedScraper es un **lector de feeds**: te suscribes a los feeds de los sitios que sigues (RSS, Atom,
RDF o JSON Feed), y sus artículos nuevos llegan a tu teléfono.

- Todo se descarga y se guarda en el teléfono: sin cuenta, sin servidor nuestro.
- Lee, marca con estrella, guarda para leer sin conexión, busca y recibe las novedades en segundo
  plano.
- Si tienes un **SyncHub** en casa, tus feeds y lo que lees pueden seguirte a otros teléfonos y a la
  interfaz web del hub ([sección 8](#8-sincronizar-con-tu-synchub)). Sin hub, la aplicación es un
  lector sencillo.

---

## 2. Añadir feeds

- **Añadir una fuente** (en el menú): pega la dirección de un feed, o simplemente del sitio — si la
  página ofrece varios feeds, eliges uno. El título se toma del feed; cámbialo si quieres y elige una
  categoría.
- **Importar desde un archivo** (OPML, la lista de suscripciones estándar, en *Ajustes*): trae los
  feeds de otro lector. Importar solo añade; nunca quita ni reordena tus feeds. **Exportar a un
  archivo** hace lo contrario.
- **Extraer una fuente de una página** (*Herramientas*): para un sitio sin feed, la aplicación
  propone una regla que saca los artículos de la página, y la aplica en cada actualización. Es
  experimental.

---

## 3. Leer

- **Vistas** en el menú: **Todas las fuentes**, **Favoritos** (artículos con estrella), **Guardados
  (sin conexión)** y un resumen de **Feeds** con un botón por feed. Cada feed y cada categoría es
  también una vista.
- La lista no se mueve mientras lees: los artículos que llegan durante la visita esperan tras una
  píldora de *artículos nuevos* arriba. Desplázate hasta el final para cargar los más antiguos.
- **Desliza** una fila para marcarla leída o no leída, o para ponerle estrella. Una **pulsación larga**
  selecciona un artículo y la barra de acciones muestra lo que puedes hacer con él.
- **Marcar todo como leído** vacía una vista de una vez.
- Abre un artículo para leerlo; desliza o usa las flechas para el anterior y el siguiente. La barra de
  acciones ofrece estrella, compartir, guardar sin conexión y abrir en el navegador. El tamaño del
  texto y el interlineado se pueden ajustar.
- La lupa **busca** en la vista actual; un toque la amplía a todos los feeds.
- En una pantalla ancha, la lista y el artículo abierto están lado a lado.

---

## 4. Leer sin conexión

**Guardar sin conexión** conserva un artículo con su texto e imágenes, legible sin red; **Guardar
fuente sin conexión** lo hace con todos los no leídos de un feed. Los artículos guardados están en
**Guardados (sin conexión)**. *Ajustes* muestra cuánto espacio ocupan, puede quitarlos una vez leídos
tras un plazo, y puede dejar las imágenes para la Wi-Fi.

---

## 5. Organizar tus feeds

- **Editar canales y categorías** (en el menú) reordena feeds y categorías, mueve feeds entre
  categorías, fusiona o elimina categorías.
- Editar un feed cambia su dirección, título y categoría, lo desactiva, o **cancela la suscripción**.
  *Ocultar los artículos cuyo título contiene* oculta artículos por palabra clave (un término por
  línea); no se borran, y quitar el término los devuelve.
- Un **corazón** en un feed lo marca como favorito; con un hub, el hub lo usa para decir qué hay de
  nuevo.
- Un feed que falla una y otra vez se señala en el menú, con un enlace a su **registro de descargas**.
  Si la dirección de un feed ya no existe, la aplicación propone los feeds que el sitio anuncia ahora.

---

## 6. Actualización y notificaciones

- Los feeds se actualizan en segundo plano, descargando solo lo que cambió y espaciando los feeds que
  fallan. *Ajustes* fija cada cuánto, si se pueden usar datos móviles y si se actualizan todos los
  feeds al abrir la aplicación.
- Desliza hacia abajo en una vista para actualizarla ya.
- Las **notificaciones de artículos nuevos** están desactivadas por defecto y se eligen feed por feed.
- **Eliminar los artículos leídos con más de** (desactivado por defecto) mantiene ligera la base de
  datos.

---

## 7. Ajustes y privacidad

En [Ajustes](app:settings): **Abrir al iniciar** (donde lo dejaste, el resumen de feeds o tus
favoritos), visualización, actualización, notificaciones, almacenamiento sin conexión, copias de
seguridad y el bloqueo.

- Los artículos se limpian antes de mostrarse: ningún script de un artículo se ejecuta nunca.
- El **bloqueo** (desactivado por defecto) pide tu huella o el bloqueo de pantalla; oculta, no cifra.
- *Copia de seguridad y restauración* guarda tus feeds, categorías, estado de lectura y ajustes en un
  archivo, y los restaura.

---

## 8. Sincronizar con tu SyncHub

La sincronización con un hub es lo que desbloquea una compra única; todo lo demás es gratis.

1. Abre **SyncHub** en el menú. La aplicación busca el hub en tu red, o escribes su dirección.
2. En la interfaz web del hub, abre **Ajustes → Dispositivos → Emparejar un dispositivo** y escanea el
   código QR con la aplicación.
3. Compara la huella del certificado cuando se te pida: la aplicación solo confía en el hub cuando la
   confirmas.

- Feeds, categorías, corazones, estado de leído y de estrella, y ajustes viajan entonces en los dos
  sentidos; el hub sigue descargando tus feeds mientras tu teléfono duerme.
- Si cambia el certificado del hub, la sincronización se detiene hasta que decidas. Nada se vuelve a
  aprobar en silencio.
- Si el hub no se puede alcanzar durante mucho tiempo, la aplicación te lo dice. El punto del menú
  muestra el estado de la sincronización de un vistazo.

---

## 9. Cuando algo falla

- **«… no se actualizó — diagnosticar»:** abre el registro de descargas del feed; dice qué respondió
  el sitio.
- **«… sigue rechazándonos»:** el sitio bloquea los lectores automáticos; la aplicación no puede hacer
  nada de forma educada.
- **Un artículo no muestra imagen:** algunos sitios niegan las imágenes a las aplicaciones; el
  artículo se lee igual.
- **La sincronización se detuvo tras un cambio en el hub:** compara la nueva huella en las páginas del
  hub antes de volver a confiar en él.
- Preguntas e ideas: *Ajustes → Acerca de → Enviar comentarios*.
