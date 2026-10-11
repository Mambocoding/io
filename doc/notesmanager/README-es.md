# NotesManager — guía de uso

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · Español · [Nederlands](README-nl.md)*

Escrita para NotesManager 0.1.34 (octubre de 2026). Si esta guía y la aplicación no dicen lo mismo,
la aplicación tiene razón.

---

## 1. Qué es NotesManager

NotesManager guarda tres tipos de notas en tu teléfono:

- **notas** — texto libre, en Markdown si quieres;
- **listas de comprobación** — elementos que vas marcando;
- **listas de tareas** — elementos con fecha límite y, si quieres, un recordatorio.

Tus notas viven en el teléfono. Si tienes un **SyncHub** en casa, también viajan a tus otros
dispositivos a través de él ([sección 7](#7-sincronizar-con-tu-synchub)); sin hub, la aplicación
funciona exactamente igual.

---

## 2. Escribir una nota

- Toca **+**: se abre una nota nueva, lista para escribir. No hay tipo que elegir ni botón Guardar.
- Lo que escribes **se guarda sobre la marcha**, y otra vez en el momento en que sales de la
  aplicación. La barra de título dice cuándo se guardó la nota.
- El título es opcional: sin título se muestra la primera línea de la nota.
- Un texto compartido desde otra aplicación (*Compartir → NotesManager*) se convierte en una nota
  nueva.

### 2.1 Listas de comprobación y listas de tareas

- En el menú ⋮ de una nota, **Convertir** la transforma en **Lista de comprobación** o en **Lista de
  tareas**, y al revés. Cada línea de una nota se convierte en un elemento; los elementos vuelven a
  ser líneas. Convertir una lista de tareas en otra cosa elimina sus fechas y recordatorios, y la
  aplicación pregunta antes.
- Añade un elemento en la última fila y pulsa intro; el campo queda abierto para el siguiente.
- Arrastra un elemento por su asa para moverlo; deslízalo para quitarlo (con *Deshacer*).
- El menú ⋮ puede ocultar los elementos marcados o desmarcarlos todos.
- En una lista de tareas, un elemento recibe una ficha de **fecha límite** y luego una de
  **recordatorio**: a la hora del recordatorio, una notificación muestra el elemento; al tocarla se
  abre la nota. El primer recordatorio pide permiso para mostrar notificaciones.

---

## 3. Encontrar notas

- **Todas las notas** muestra tus notas como tarjetas o como lista (el menú ⋮ cambia). Las notas
  **fijadas** van primero.
- **Desliza** una tarjeta a la derecha para fijarla, a la izquierda para archivarla. Deslizar nunca
  elimina.
- **Ordena** por última modificación, creación, título, o tu propio orden dentro de una etiqueta.
- **Buscar** (la lupa) recorre títulos, textos y elementos mientras escribes — notas archivadas
  incluidas. Los acentos no importan: *ete* encuentra *été*. Limita a **Cuerpo** o **Elementos**.

### 3.1 Etiquetas

Una nota puede llevar varias **etiquetas**. Añade una desde la nota (la ficha *+* bajo el título) o
crea etiquetas en la sección **Etiquetas** del menú. Tocar una etiqueta en el menú muestra solo sus
notas; una pulsación larga la renombra o la elimina. Eliminar una etiqueta conserva sus notas.

---

## 4. Seleccionar, archivar, eliminar

- Una **pulsación larga** inicia una selección; toca más notas para añadirlas. La barra de acciones
  ofrece entonces fijar, archivar, etiquetas, compartir y eliminar para todas a la vez.
- **Archivar** saca una nota de *Todas las notas* y de las etiquetas sin eliminarla; sigue
  localizable y editable en **Archivo**.
- **Eliminar** envía las notas a la **Papelera**. Una nota de la Papelera se puede **restaurar**, o
  eliminar para siempre.
- La Papelera guarda las notas **30 días** y luego las elimina. El plazo es el del hub: una nota
  guardada más tiempo podría volver a la vida en tus otros dispositivos.

---

## 5. Cuando dos dispositivos editan la misma nota

NotesManager **nunca fusiona en silencio dos versiones del texto de una nota**.

- Si el texto de una nota cambió en dos dispositivos antes de que se sincronizaran, **se conservan
  los dos textos**: el segundo se convierte en una **Copia en conflicto**, mostrada justo después del
  original. Lee las dos, quédate con lo que quieras, elimina la otra.
- Si una nota cambia en otro dispositivo **mientras escribes**, tu texto se guarda como copia en
  conflicto y la nota muestra el texto del otro dispositivo, con una línea que dice adónde fue lo que
  escribiste.
- En una lista, los elementos se fusionan uno a uno: marcas, orden y fechas siguen el último cambio;
  dos ediciones distintas del texto de un mismo elemento dan dos elementos.

---

## 6. Tus datos: exportar, importar, borrarlo todo

En [Ajustes](app:settings) → *Datos*:

- **Exportar notas** guarda tus notas como un paquete de archivos Markdown (y las listas de tareas en
  el formato habitual de tareas de calendario) que otras aplicaciones pueden abrir.
- **Importar notas** lee la exportación de otra aplicación de notas: un zip con un archivo JSON por
  nota. La aplicación muestra lo que encontró antes de importar nada; etiquetas, notas fijadas y
  archivadas se conservan.
- **Eliminar todas las notas** borra cada nota, etiqueta y elemento de este teléfono, después de que
  escribas una frase de confirmación. Tus ajustes, el bloqueo y el emparejamiento con el hub se quedan. Si el
  teléfono está emparejado, el hub conserva su copia y la devuelve en la próxima sincronización: para
  que el borrado se mantenga, desempareja primero el hub, o elimina las notas en el propio hub.

---

## 7. Sincronizar con tu SyncHub

1. Abre **SyncHub** al pie del menú. La aplicación busca el hub en tu red doméstica; si no lo
   encuentra, escribe su dirección.
2. En la interfaz web del hub, abre **Ajustes → Dispositivos → Emparejar un dispositivo** y **escanea**
   el código QR con la aplicación (el botón *Escanear*). El escaneo comprueba con exactitud el
   certificado del hub.
3. Tus notas se envían al hub y, desde entonces, viajan en los dos sentidos.

- **Modo de sincronización:** *Automático* se sincroniza solo, poco después de cada cambio y en
  segundo plano; *Manual* espera a **Sincronizar ahora**.
- La pantalla de sincronización muestra cuándo fue el último intercambio y, por tipo de datos,
  cuántos cambios pasaron en cada sentido.
- Si el hub no se puede alcanzar durante mucho tiempo, la aplicación puede avisarte con una
  notificación.
- La interfaz web del hub muestra y edita las mismas notas.

---

## 8. Privacidad y bloqueo

- Las notas se guardan solo en el teléfono, y en tu propio hub si emparejas uno. La aplicación no se
  conecta a nada más.
- **Bloqueo de la aplicación** (*Ajustes*): NotesManager pide tu huella, tu cara o el bloqueo de
  pantalla al abrirse, y tras el plazo que elijas. El bloqueo oculta la aplicación; **no cifra** tus
  notas.

---

## 9. Cuando algo falla

- **«Tus ajustes estaban dañados y se han restablecido»:** la aplicación no pudo leer sus ajustes y
  empezó de cero. **Tus notas están a salvo.** Hay que volver a emparejar el hub; el hub recibe
  entonces de nuevo tus notas.
- **Una nota está marcada como *Copia en conflicto*:** dos versiones de su texto se cruzaron; ver la
  [sección 5](#5-cuando-dos-dispositivos-editan-la-misma-nota).
- **Un recordatorio no sonó:** comprueba que las notificaciones estén permitidas para NotesManager y
  que el teléfono le deje programar alarmas exactas.
- Preguntas e ideas: *Ajustes → Acerca de → Enviar comentarios*.
