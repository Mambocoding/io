# StocksScraper — guía de uso

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · Español · [Nederlands](README-nl.md)*

Escrita para StocksScraper 0.2.175 (octubre de 2026). Si esta guía y la aplicación no dicen lo mismo,
la aplicación tiene razón.

---

## 1. Qué es StocksScraper

StocksScraper sigue una **lista de favoritos** — acciones, ETF, materias primas y criptomonedas — y
**te avisa cuando uno se mueve** un ±5 % (o el umbral que elijas). Es de uso personal: todo se
calcula en tu teléfono, sin servidor ni cuenta.

- La **lista de favoritos** es gratuita, completa e ilimitada.
- La **cartera** — lo que tienes, lo que vale, si ganas — es la parte premium, una compra única. Se
  ve, con un destello, antes de tenerla.
- No hay ninguna fuente de precios integrada: eres **tú** quien da a la aplicación las direcciones de
  las fuentes que usas.

---

## 2. Fuentes de datos

[Ajustes](app:settings) → *Fuentes de datos* contiene una dirección por **rol**, cada uno nombrado por
la forma de lo que responde: una serie de cotizaciones sin clave (la fuente principal), una
instantánea de cotización y una serie temporal (ambas con una clave que escribes), una cotización CSV
y un precio de criptomoneda. Un rol sin dirección queda inactivo.

- Cada tipo de instrumento tiene su propia **cadena de respaldo**: si la primera fuente falla, se
  pregunta a la siguiente. Nunca tienes que elegir a mano.
- *Estado*, en la misma pantalla, dice qué fuente respondió la última y qué hace la cadena.
- Sin ninguna fuente, la lista lo dice en lugar de mostrar un error en cada fila.
- Quien escribe una dirección responde de las condiciones de ese servicio.

---

## 3. La lista de favoritos

- **Añade** un instrumento con **+** (o *Buscar / añadir* en el menú): busca por nombre o símbolo;
  también se encuentran las cotizaciones locales.
- **Categorías:** agrupa tus favoritos bajo tus propios títulos, pliégalos y arrástralos al orden que
  quieras (*Reordenar*).
- Cada fila muestra el tipo de instrumento, su precio y — a tu elección en el menú ⋮ — sus cifras o
  una línea de tendencia. Un **punto** dice si el mercado está abierto: un precio vivo o congelado.
- Al abrirse, la aplicación muestra enseguida los últimos precios conocidos, atenuados y fechados, y
  luego los actualiza.
- Toca un instrumento para ver su **detalle**: un gráfico de precios en varios periodos, el estado
  del mercado, sus noticias, enlaces y sus propias alertas.
- El **corazón** de un instrumento elige si aparece en la página de inicio de tu SyncHub.

---

## 4. Alertas

- Llega una alerta cuando un instrumento se mueve el **umbral** (5 % por defecto) frente al cierre
  anterior. La aplicación comprueba cada hora por defecto, en segundo plano.
- *Ajustes → Notificaciones* fija el umbral, cada cuánto comprobar, cuántas alertas por instrumento y
  día (una por defecto), una alerta opcional de movimiento **semanal** (desactivada por defecto) y
  **Silenciar por la noche**: una alerta que cae en la franja se muestra al terminar, si sigue
  valiendo.
- En las **Alertas** de un instrumento: su propio umbral, **niveles de precio** (suenan una vez al
  cruzarse) y **Silencio** durante 1 día, 1 semana o hasta que lo reactives.
- **Alertas**, en el menú, responde a *¿qué me perdí?*: todas las alertas que saltaron en la lista,
  de la más reciente a la más antigua; el menú ⋮ filtra niveles de precio o variaciones porcentuales.
- Una alerta trata de la sesión de hoy y dice cuándo ocurrió el movimiento. Al tocarla se abre el
  instrumento.

---

## 5. Cartera (premium)

- **Posiciones:** lo que tienes, valorado en una **moneda de referencia** (*Ajustes → Cartera*), con
  la ganancia por línea y en total, y una curva de valor en el periodo que elijas.
- **Una posición son sus transacciones:** abre una posición para añadir compras, ventas y dividendos;
  la cantidad y el coste medio salen de ellas.
- Saldos de **efectivo** y **subcarteras** (una por cuenta, por ejemplo): el título cambia entre
  ellas.
- **Plan de inversión:** una orden de compra periódica — semanal, mensual, dos veces al mes o
  trimestral — registra sus propias compras en los días previstos.
- **Importar / exportar:** pega o elige una lista de posiciones (CSV), o importa el extracto de un
  banco — una foto de las posiciones o un diario fechado — cuyo formato se reconoce solo.
- La cartera nunca se envía a ningún sitio salvo que actives *Sincronizar mi cartera*
  ([sección 7](#7-synchub)).

---

## 6. Noticias y widget

- **Noticias** reúne artículos sobre tu lista; el detalle de un instrumento muestra los suyos. Lee,
  marca con estrella, guarda para leer sin conexión o abre el original.
- El **widget** muestra tu lista en la pantalla de inicio, con los últimos precios conocidos; nunca
  descarga nada por sí mismo.

---

## 7. SyncHub

Si tienes un **SyncHub** en casa, la aplicación mantiene iguales tu lista, categorías, alertas y
ajustes en varios teléfonos y en la interfaz web del hub.

1. Abre **SyncHub** en el menú. La aplicación busca el hub en tu red, o escribes su dirección.
2. En la interfaz web del hub, abre **Ajustes → Dispositivos → Emparejar un dispositivo** y escanea el
   código QR. La aplicación solo confía en el hub cuando la huella de su certificado está confirmada.

- La **cartera** solo viaja si activas **Sincronizar mi cartera** (premium), tras una confirmación.
- **Reenviar todo** vuelve a llenar un hub que perdió sus datos.
- Si el hub no se puede alcanzar durante mucho tiempo, la aplicación te lo dice.

---

## 8. Seguridad y copias de seguridad

- *Ajustes → Seguridad → Bloqueo de la aplicación*: protege toda la aplicación, o solo la cartera,
  con tu huella, tu cara o el bloqueo de pantalla. El bloqueo oculta; **no cifra**.
- *Ajustes → Copia de seguridad y restauración* guarda la lista, las alertas y los ajustes en un
  archivo — la cartera solo si la marcas — y los restaura. Las claves de API nunca van en una copia
  sin cifrar.

---

## 9. Cuando algo falla

- **«Ninguna fuente de datos configurada»:** escribe al menos la dirección de la fuente principal
  ([sección 2](#2-fuentes-de-datos)).
- **Un precio parece antiguo:** el punto y la línea de antigüedad dicen si el mercado está cerrado o
  la fuente no respondió; *Fuentes de datos → Estado* dice qué fuente respondió la última.
- **No llegó una alerta:** comprueba el umbral y el número por día, si el instrumento está
  silenciado, el silencio nocturno, y que el teléfono permita las notificaciones de la aplicación.
- Preguntas e ideas: *Ajustes → Acerca de → Enviar comentarios*.
