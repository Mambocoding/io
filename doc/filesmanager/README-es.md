# Gestor de archivos — guía de uso

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · Español · [Nederlands](README-nl.md)*

Escrita para Gestor de archivos 1.2.329 (octubre de 2026). Si esta guía y la aplicación no dicen lo
mismo, la aplicación tiene razón.

---

## 1. Qué es el Gestor de archivos

El Gestor de archivos es un explorador de archivos para tu teléfono y tu televisor. Recorre el
almacenamiento del teléfono, una tarjeta SD o una memoria USB, y los servidores de tu red doméstica;
copia, guarda y sincroniza carpetas entre todos ellos.

- Todo se queda en tus dispositivos: no hay cuenta ni nube nuestra.
- La base es gratuita y sin publicidad. Algunas funciones son de la versión premium; llevan un
  destello dorado (ver la [sección 13](#13-gratis-y-premium)).
- En un televisor, la misma aplicación recorre los mismos lugares con el mando.

---

## 2. Primer inicio

1. Un breve asistente te pide aceptar las condiciones de uso y luego elegir el **modo de la
   aplicación** y un tema. El modo se cambia más tarde en [Ajustes](app:settings) → *Interfaz*:
   - **Explorador de archivos** (por defecto) se abre en tus archivos;
   - **Visor de fotos** se abre en tus fotos, como galería.
2. Después, Android pide acceso a tus archivos. Elige **Conceder acceso** para recorrer todo el
   almacenamiento, o **Elegir una carpeta en su lugar** para dar acceso a una sola carpeta.
3. La primera vez que abres una conexión a tu red doméstica, Android puede pedir **acceso a la red
   local**. Permítelo: sin él, toda conexión a tu red agota el tiempo de espera. Puedes activarlo
   más tarde en los permisos de la aplicación.

---

## 3. Explorar

- La **ruta** de arriba es una fila de fichas: toca una para volver a esa carpeta. La carpeta que
  acabas de dejar queda como ficha atenuada, para poder avanzar de nuevo.
- **Vistas:** lista detallada, cuadrícula o cuadrícula grande, desde el menú ⋮, o pellizcando la
  lista.
- **Orden:** por nombre, fecha, tamaño o tipo, ascendente o descendente; las carpetas pueden ir
  primero.
- **Búsqueda:** toca la lupa; los resultados sustituyen la lista en cuanto escribes. Busca en la
  carpeta actual y sus subcarpetas; un icono de la barra de búsqueda la amplía a todo el dispositivo.
- **Recientes:** el icono de reloj en la fila *Almacenamiento interno* del menú muestra los archivos
  abiertos últimamente (7 o 30 días). *Borrar el historial reciente* olvida la lista propia de la
  aplicación.
- **Recordar última ubicación** (activado por defecto) vuelve a abrir la última carpeta visitada.
- **Pantalla dividida:** en una pantalla ancha (tableta, o teléfono en horizontal) aparecen dos
  paneles lado a lado, para copiar de uno a otro. Se desactiva en *Ajustes → Interfaz*.

### 3.1 Favoritos

Arriba del almacenamiento interno, unos mosaicos llevan a **Fotos**, **Música** y **Descargas**. Toca
**+ Añadir** para fijar cualquier carpeta; una pulsación larga sobre un mosaico lo quita (solo se va
el acceso directo, nunca la carpeta). Cada conexión y cada tarjeta SD tiene sus propios favoritos. El
panel se pliega con su flecha, o desaparece con *Ajustes → Interfaz → Mostrar el panel de
favoritos*.

---

## 4. Trabajar con archivos

- **Selecciona** con una pulsación larga y luego toca más archivos; *Seleccionar todo* está en la
  barra de acciones.
- La **barra de acciones** (la píldora flotante) reúne lo que puedes hacer con la selección: copiar,
  mover, renombrar, eliminar, compartir, comprimir… Su posición (flotante, arriba o abajo) y sus
  botones se ajustan en *Ajustes → Interfaz → Barra de acciones*.
- **Copiar y mover:** tras *Copiar* o *Mover*, ve al destino y pega. Si un nombre ya existe, la
  aplicación pregunta antes de mover nada: **Reemplazar** o **Duplicar** (`nombre (1)`), con *Para
  todos los conflictos* para responder una sola vez.
- Pegar más de tres archivos continúa en segundo plano, con su progreso en una notificación y en
  **Herramientas → Transferencias**.
- **Eliminar:** en el almacenamiento interno, un archivo eliminado va primero a la **Papelera**
  ([sección 10](#10-liberar-espacio-y-la-papelera)). En una carpeta de red o una tarjeta SD abierta
  con el selector de Android, eliminar es definitivo, y la confirmación lo dice.
- Las **propiedades** muestran tamaño, fechas y ubicación; para una selección, el tamaño total.
- **Zip:** abre un `.zip` para explorarlo, extráelo, o comprime una selección en un archivo nuevo.
- **Editor de texto:** los archivos de texto se abren en un editor integrado con buscar y
  reemplazar.

---

## 5. Fotos, documentos y multimedia

- **Visor de imágenes:** desliza a la foto siguiente o anterior, pellizca o toca dos veces para
  ampliar. El título indica cuándo se tomó la foto. Un toque oculta o muestra las barras.
- La píldora del visor reúne **Compartir · Editar · Detalles · Usar como… · Presentación · Imprimir ·
  Eliminar**. Tras eliminar, la foto siguiente ocupa su lugar.
- **Editor de fotos:** recortar, girar, voltear y enderezar son gratis; redimensionar, colores,
  filtros, anotaciones, recorte de sujeto y borrado son premium.
- **PDF:** los archivos PDF se abren en la aplicación, con búsqueda y salto de página. El Gestor de
  archivos también puede ser el lector de PDF del teléfono.
- **Reproductor:** música y vídeos se reproducen en la aplicación, también directamente desde una
  carpeta de red.
- Un archivo de una conexión se abre directamente en la aplicación; otra aplicación recibe una copia
  temporal.

---

## 6. Conexiones de red

El Gestor de archivos llega a los servidores de tu red doméstica como si fueran carpetas del
teléfono.

1. Abre el menú y luego **Conexiones → Añadir conexión**.
2. Elige el tipo: **SMB** (carpetas compartidas de un ordenador y la mayoría de NAS, gratis),
   **FTP/FTPS**, **SFTP**, **WebDAV** o **S3** (premium).
3. Escribe la dirección del servidor, tu usuario y tu contraseña, y si quieres una carpeta de
   inicio. La contraseña se guarda cifrada en el teléfono.
4. La conexión aparece en el menú con su espacio libre. Tócala para explorarla.

La primera vez que un servidor presenta un certificado desconocido, la aplicación te pregunta si
confías en él; después, un certificado distinto se rechaza.

### 6.1 El espacio de archivos de tu SyncHub

Si tienes un SyncHub en casa, su espacio de archivos es una conexión **WebDAV**: la dirección del hub,
el nombre de tu cuenta como usuario y el token de aplicación del hub como contraseña.

---

## 7. Sincronización de carpetas

Las **tareas** copian carpetas de un lugar a otro, una y otra vez, con un toque o según un horario.

1. Abre **Tareas** en el menú y crea una tarea. El asistente pregunta:
   - **¿Qué tipo de sincronización?** **Copia de seguridad** (copia archivos nuevos y modificados;
     no se elimina nada), **Reflejar** (deja el destino idéntico), **Mover**, **Descargar** o
     **Bidireccional**;
   - la carpeta de **origen** y la de **destino**, en el teléfono o en una conexión;
   - las opciones: filtros, qué hacer ante un conflicto, notificaciones y ejecución automática.
2. Ejecútala con el botón de reproducción, en la lista de tareas o en el menú. **Ejecutar todas las
   tareas**, abajo en la lista, las ejecuta una tras otra.
3. La página de una tarea muestra su progreso, su último resultado y su historial; se puede pausar,
   detener, editar o desactivar.

Gratis: una **copia de seguridad** manual al teléfono o a una carpeta SMB — también directamente
desde el explorador con *Copia en remoto…*. Premium: los demás tipos, los horarios, la sincronización
en vivo y las opciones avanzadas.

Una tarea automática se ejecuta cada 1, 3, 6, 12 o 24 horas, solo con Wi-Fi salvo que permitas los
datos móviles, y si quieres solo mientras se carga.

---

## 8. Enviar archivos a un dispositivo cercano

**Enviar a dispositivo** intercambia archivos con teléfonos y ordenadores de la misma Wi-Fi, sin
cable ni nube.

- Para **recibir**, abre *Enviar a dispositivo* y activa **Hacerme visible**. Solo eres visible
  mientras esta pantalla está abierta.
- Una oferta entrante siempre pregunta primero: **Aceptar**, **Rechazar** o **Bloquear**, y dónde
  guardarla. No se recibe nada antes de que aceptes.
- Para **enviar**, elige un dispositivo de la lista y luego los archivos; o usa *Compartir* desde
  otra aplicación y elige *Compartir con dispositivo*.
- Un dispositivo que no aparece se añade por su dirección o escaneando su código QR.

Las transferencias en la misma Wi-Fi no van cifradas: úsalas en casa, no en una red pública.

---

## 9. Compartir este dispositivo (premium)

Un ordenador de la misma Wi-Fi explora y descarga los archivos del teléfono en su navegador web, sin
instalar nada.

1. **Conexiones → Compartir este dispositivo**, elige la carpeta compartida y decide si el navegador
   también puede subir y borrar (*Permitir subir y borrar desde el navegador*, desactivado por
   defecto).
2. **Empezar a compartir:** la pantalla muestra una dirección, un código QR y un PIN de seis cifras.
3. Abre la dirección en el ordenador y escribe el PIN.

Compartir se detiene con *Dejar de compartir*, o solo tras 30 minutos sin uso. Tras cinco PIN
erróneos deja de responder. La conexión no va cifrada, y la pantalla lo dice: úsala solo en casa.

---

## 10. Liberar espacio y la Papelera

- **Herramientas → Liberar espacio** ordena los archivos grandes y antiguos por categorías. No hay
  nada preseleccionado: revisas cada archivo y luego **Mover a la papelera**.
- **Herramientas → Papelera** lista lo que se eliminó del almacenamiento interno. **Restaurar**
  devuelve un archivo a su sitio; **Vaciar papelera** lo borra todo definitivamente.
- En *Ajustes → Papelera*, elige si eliminar pasa por la Papelera o borra directamente, y cuánto
  tiempo guarda la Papelera los archivos (hasta vaciarla, o 5, 15, 30 o 90 días).

---

## 11. Privacidad: bloqueo y caja fuerte

- **Bloqueo de la aplicación** (gratis, *Ajustes → Privacidad*): el Gestor de archivos pide tu huella,
  tu cara o el bloqueo de pantalla al abrirse, y tras el plazo que elijas cuando sales. Su contenido
  se oculta en la pantalla de aplicaciones recientes.
- **Caja fuerte** (premium): un espacio privado y cifrado. Los archivos que llevas allí (*Mover a la
  caja fuerte*) se cifran en el teléfono y se ocultan de la galería y de otras aplicaciones. La caja
  fuerte se abre con el bloqueo de pantalla.
  - Al crearla, la aplicación muestra un **código de recuperación**. Anótalo y guárdalo lejos del
    teléfono: es la única forma de volver a entrar si se quita el bloqueo de pantalla, se restablece
    el teléfono o cambias de teléfono. Nadie puede restablecerlo por ti; sin él, los archivos de la
    caja fuerte se pierden para siempre.
  - *Guardar una copia fuera* escribe una copia descifrada de un archivo fuera de la caja fuerte.

---

## 12. Hacer una copia de la aplicación

*Ajustes → Copia de seguridad y restauración* guarda la propia aplicación — conexiones, tareas,
favoritos, temas y ajustes — en un único archivo cifrado, protegido por una frase de contraseña que
eliges, y la restaura en un teléfono nuevo.

- La **copia automática** crea ese archivo cada día por sí sola.
- Si tienes un SyncHub, la copia también puede guardarse **en el hub**: vincula la aplicación con él
  desde la pantalla de copia. Ese vínculo abre las copias del Gestor de archivos y nada más.

Tus archivos no están en esta copia: cópialos con una tarea
([sección 7](#7-sincronización-de-carpetas)).

---

## 13. Gratis y premium

Gratis, para siempre: explorar, las operaciones con archivos, los favoritos, la galería, los visores
y el reproductor, la Papelera y *Liberar espacio*, el zip, las conexiones SMB, la copia manual a SMB
o al teléfono, *Enviar a dispositivo*, el bloqueo, y la copia automática de la aplicación.

Premium: los demás tipos de conexión (FTP/FTPS, SFTP, WebDAV, S3), toda sincronización más allá de
una copia manual, los horarios y la sincronización en vivo, las herramientas avanzadas del editor de
fotos, los perfiles de procesamiento, la caja fuerte y *Compartir este dispositivo*.

Una función premium se ve en todas partes con un destello dorado; al tocarla se abre la pantalla
premium. Una tarea que usa una opción premium se omite, nunca se ejecuta a medias.

---

## 14. Cuando algo falla

- Los mensajes de error dicen qué pasó con palabras sencillas. **Detalles**, bajo un mensaje, muestra
  la causa técnica, que puedes copiar en un comentario (*Ajustes → Acerca de → Enviar
  comentarios*).
- **Una conexión agota el tiempo:** comprueba que el *acceso a la red local* esté permitido para la
  aplicación, que el teléfono esté en la misma Wi-Fi que el servidor, y la dirección del servidor.
- **«Tus ajustes estaban dañados y se han restablecido»:** la aplicación no pudo leer sus ajustes y
  empezó de cero. Tus archivos están a salvo; conexiones, tareas y favoritos hay que volver a
  crearlos o restaurarlos desde una copia ([sección 12](#12-hacer-una-copia-de-la-aplicación)).
- **Una tarea se detuvo:** ábrela en *Tareas*; su página dice por qué. Los cortes de red pasajeros se
  reanudan solos; una tarea en pausa te espera.
