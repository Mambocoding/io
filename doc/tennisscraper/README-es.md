# Tennis Scraper — guía de uso

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · Español · [Nederlands](README-nl.md)*

Escrita para Tennis Scraper 0.1.140 (octubre de 2026). Si esta guía y la aplicación no dicen lo mismo,
la aplicación tiene razón.

---

## 1. Qué es Tennis Scraper

Tennis Scraper sigue el tenis profesional individual — los circuitos masculino y femenino — y **te
avisa cuando empieza un partido que sigues**, mientras se juega y cuando termina.

- Todo ocurre en tu teléfono: sin cuenta, sin servidor nuestro. Las notificaciones las calcula el
  propio teléfono.
- La aplicación no trae ninguna dirección de datos: eres **tú** quien escribe la dirección de la
  fuente que usas ([sección 8](#8-fuente-de-datos-y-estado)). Hasta entonces, las pantallas siguen
  vacías y lo dicen.
- Sigues **jugadores**, **torneos** enteros desde la ronda que elijas, o un **partido** concreto.
- **Un partido, una notificación** de cada tipo, tengas las razones que tengas para seguirlo.

---

## 2. Hoy

**Hoy** es la pantalla de inicio, hecha de bloques que eliges: **partidos**, **noticias**,
**clasificación** y **calendario**.

- El bloque de partidos muestra los partidos de tus favoritos y los que sigues en una sola línea de
  tiempo, con separadores de día: próximos con su hora, **en vivo** con el marcador y un punto que
  late, terminados con el resultado. Un partido entre dos de tus favoritos aparece una vez.
- Toca el título de un bloque para abrir su pantalla; edita la página para añadir, quitar o
  reordenar bloques.
- El **modo antispoiler** (menú ⋮) oculta en Hoy las noticias y todos los marcadores y *Ganó* /
  *Perdió*, para un partido que verás más tarde. Las filas en vivo conservan su marca *LIVE*.
- Desliza hacia abajo para actualizar. Hoy también se actualiza en segundo plano, así que se abre con
  datos frescos.
- El menú ⋮ también filtra por circuito: **Todos**, o uno de los dos circuitos. El filtro vale en
  todas las pantallas y nunca cambia lo que se descarga.

---

## 3. Jugadores y seguimiento

- **Jugadores** muestra tus favoritos, agrupados por circuito. Escribe en el campo de búsqueda para
  encontrar cualquier jugador; la estrella añade o quita un favorito.
- La **campana** de un favorito lo silencia: sigue siendo favorito, pero sus partidos ya no notifican
  (salvo que otra razón para seguir el partido siga valiendo).
- **Seguir este torneo** (desde su cabecera en Partidos o Calendario): elige desde qué ronda — cuadro
  principal, cuartos, semifinales o la final. Cada partido del torneo desde esa ronda notifica
  entonces.
- **Seguir este partido** (en el detalle de un partido): sus alertas llegan aunque no sigas a ninguno
  de los dos jugadores. El seguimiento caduca solo tras el partido.

---

## 4. Partidos, calendario, cuadros, clasificación

- **Partidos** lista los partidos de un día por torneo, con clasificados, categoría y ronda. Toca un
  partido para ver su **detalle**: jugadores, marcador por set, ronda y las acciones de abajo.
- **Calendario** lista los torneos por semana; abre uno para ver su **cuadro**, ronda a ronda. *Sitio
  oficial* abre la página del torneo cuando la aplicación la conoce.
- **Clasificación** muestra la clasificación actual de cada circuito; toca un jugador para ver su
  detalle.
- En el detalle de un partido:
  - **Compartir** envía el partido como texto;
  - **Añadir al calendario** (partido próximo con hora de inicio) lo pasa a tu aplicación de
    calendario;
  - **Ver** (en vivo o a punto de empezar) abre el partido en una página de búsqueda de emisiones —
    solo si has puesto una *Dirección de búsqueda para ver* en [Ajustes](app:settings).

---

## 5. Notificaciones

[Ajustes](app:settings) → *Notificaciones* reúne todos los interruptores:

- **Alertas de partido:** *Empieza pronto* (activada, con cuánto antes), *Inicio del partido*
  (activada), *Marcador en vivo* (desactivada) y *Resultado* (activada).
- **Cada día:** un **resumen diario** de los partidos de tus favoritos, una notificación por jugador,
  a la hora que elijas; y un aviso cuando empieza un torneo que sigues.
- **Horario silencioso** (desactivado por defecto, 23:00–08:00 al activarlo): las alertas que caen
  dentro se descartan.
- **Jugadores silenciados** lista los favoritos que silenciaste.

Al tocar una notificación se abre el partido.

---

## 6. Noticias

Si escribes una **dirección del feed de noticias** (un feed RSS o Atom, en *Ajustes*), **Noticias**
lista los últimos artículos, y Hoy puede mostrar *noticias de tus favoritos*. **Marcar todo como
leído** está en la barra de acciones. Sin dirección, las noticias se ocultan por completo y no se
descarga nada.

---

## 7. Widget y coche

- **Widget:** hasta tres partidos seguidos del día en la pantalla de inicio — en vivo primero, luego
  próximos, luego terminados. Un toque abre Hoy.
- **En el coche:** con el teléfono conectado a la pantalla de un coche, las alertas de partido se
  pueden leer en voz alta, y se pueden consultar los favoritos y el programa del día.

---

## 8. Fuente de datos y estado

- *Ajustes → Fuente de datos* elige de dónde vienen los partidos: una fuente de **marcador** (sin
  clave) o una **lista de encuentros con clave** (clave necesaria), cada una mediante una dirección
  que escribes. Quien escribe una dirección responde de las condiciones de ese servicio. Los
  favoritos se guardan por fuente.
- *Ajustes → Estado* dice qué hizo la aplicación por última vez: la fuente en uso, la última descarga
  correcta y la última fallida, y las cachés. Es el lugar donde mirar cuando no llegó una
  notificación.

---

## 9. Hacer una copia de la aplicación

*Ajustes → Copia de seguridad y restauración* guarda tus favoritos, seguimientos y ajustes en un
archivo, y los restaura en un teléfono nuevo.

---

## 10. Cuando algo falla

- **No llegó una notificación:** comprueba en *Ajustes → Estado* la última descarga, que la alerta
  esté activada, que el jugador no esté silenciado, que no estuvieras en horario silencioso, y que el
  teléfono permita notificaciones y no duerma la aplicación.
- **Un marcador en vivo parece atascado:** el marcador mostrado es el último que dio la fuente;
  desliza hacia abajo para actualizar.
- **No hay noticias:** la dirección del feed de noticias está vacía, o el feed no respondió.
- Preguntas e ideas: *Ajustes → Acerca de → Enviar comentarios*.
