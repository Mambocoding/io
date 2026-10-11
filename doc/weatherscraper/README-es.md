# WeatherScraper — guía de uso

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · Español · [Nederlands](README-nl.md)*

Escrita para WeatherScraper 0.1.135 (octubre de 2026). Si esta guía y la aplicación no dicen lo
mismo, la aplicación tiene razón.

---

## 1. Qué es WeatherScraper

WeatherScraper muestra una **previsión a 14 días** para las ciudades que elijas. No tiene previsión
propia y no nombra ningún sitio meteorológico: eres **tú** quien le dice dónde leer.

- **Una página de previsión que pegas:** la dirección de una página de previsión de varios días, de
  un sitio en el que confías. La aplicación lee su tabla de días.
- **Un servicio de previsión que configuras:** la dirección de una API de previsión que tienes
  derecho a usar, consultada para una ciudad por sus coordenadas.

Una ciudad puede tener las dos, así que una página que cambia de diseño no te deja sin previsión. La
fuente de cada previsión siempre se nombra en pantalla, con el host que escribiste.

Una instalación nueva está vacía: ninguna ciudad, ninguna dirección. Un breve asistente ayuda a
configurarlas.

---

## 2. Primer inicio

El asistente pregunta, en orden:

1. Qué **fuentes** quieres usar: páginas pegadas, un servicio de previsión o ambos.
2. Las **direcciones** del servicio, si las hay: la dirección de previsión y la dirección de
   geocodificación, que sirve para encontrar una ciudad por su nombre. Deja un campo vacío para
   saltarlo; todo se puede cambiar después en [Ajustes](app:settings).
3. Tu **primera ciudad**.
4. Si quieres, tu **SyncHub** ([sección 9](#9-synchub)).

No se guarda nada hasta que tocas *Empezar*.

---

## 3. Añadir ciudades

Abre el menú y toca **+ Añadir una ciudad**.

- **Por nombre:** escribe al menos dos letras; aparecen los lugares que coinciden, con su región. Un
  toque añade la ciudad. Hace falta una dirección de geocodificación en los ajustes.
- **Desde una página** (*Herramientas → Extraer de una página*, marcado como experimental):
  1. Pega la **dirección** de la página de previsión de varios días del sitio (no su portada) y toca
     **Analizar**. La aplicación descarga la página una vez.
  2. Se muestran hasta tres tablas candidatas como filas de previsión, cada una con una confianza:
     *Parece una previsión*, *Dudoso — compruebe la vista previa*, *Probablemente incorrecto*. *¿No es
     la tabla correcta?* muestra la siguiente.
  3. La vista previa dice qué datos del día encontró (lluvia, viento, sol) y si el sitio tiene
     **páginas por día**, que dan las horas de un día cuando lo abres.
  4. Pon nombre a la ciudad y toca **Añadir ciudad**. Si el nombre coincide con un lugar, se guardan
     sus coordenadas: el servicio de previsión toma el relevo si la página deja de funcionar.

El extractor respeta el `robots.txt` del sitio, se identifica con honestidad y descarga pocas veces.
Si una página está construida con JavaScript o rechaza la solicitud, lo dice. *Avanzado* permite
escribir los selectores a mano. Respetar las condiciones del sitio te corresponde a ti.

En el menú, cada ciudad tiene un **corazón** (tus favoritas, que también aparecen en la página de
inicio del hub), un asa para reordenarla y **×** para quitarla (se borra su previsión guardada).

---

## 4. Leer la previsión

La pantalla de inicio muestra la ciudad seleccionada. **Desliza de lado** o usa el menú para cambiar
de ciudad.

- **Tres vistas**, desde el menú ⋮: **Ahora**, **7 días** (por defecto, tarjetas con detalles) y
  **14 días** (una lista compacta). Encima de ambas listas, un **gráfico de temperaturas** muestra las
  máximas sobre las mínimas.
- Cada día muestra: día de la semana y fecha, una ilustración, mín / máx, y luego condición ·
  probabilidad de lluvia · milímetros · viento. Un dato que la fuente no dio aparece como **—**: la
  aplicación nunca inventa uno.
- **La línea de estado** siempre está: la antigüedad de la previsión, de qué fuente viene (el host que
  escribiste) y el último fallo si una actualización falló. Un fallo nunca quita la previsión; se
  queda, con su antigüedad.
- Toca un día para ver su **detalle**: las horas cuando la fuente las tiene, la humedad y las
  categorías de alerta del día.
- **Actualizar:** desliza hacia abajo, o el icono de actualizar en la cabecera.
- La **barra de acciones** ofrece *Compartir* (una imagen de la previsión) y, para una ciudad de
  página, *Abrir la página de origen*.

### 4.1 Una ciudad con dos fuentes

Cuando una ciudad tiene una página y coordenadas, **Comparar fuentes** (en *Ajustes*) muestra una
página por fuente más una página **Promedio** (temperaturas medias, la peor condición de las dos). Si
no, el ajuste **Fuente preferida** decide qué fuente se usa primero; la otra toma el relevo cuando la
primera falla.

---

## 5. Actualización

- Cada mañana a las 7:00, la aplicación actualiza todas tus ciudades.
- Al abrir una ciudad cuya previsión tiene más de 30 minutos, la actualiza.
- **Intervalo de actualización** (desactivado por defecto) añade una actualización cada 1, 3, 6 o 12
  horas. Puedes limitar las actualizaciones en segundo plano a la Wi-Fi.
- Como mucho dos solicitudes por actualización para una ciudad de página (la lista y luego la página
  de hoy), con pausas crecientes tras los fallos. Nunca se satura un sitio.

---

## 6. Alertas y avisos oficiales

### 6.1 Alertas a partir de tu previsión

*Ajustes → Notificaciones → Alertas* (desactivado por defecto) vigila **hoy y mañana** en tus
previsiones guardadas y te avisa una vez por ciudad, día y tipo cuando se espera uno de seis
fenómenos: **helada**, **calor**, **lluvia intensa**, **viento fuerte**, **nieve** o **tormenta**. La
**sensibilidad** (*Baja*, *Normal*, *Alta*) mueve los umbrales; cada tipo se puede desactivar, y cada
ciudad también. Una ciudad de página suele dar solo temperaturas y condiciones, así que las alertas
de lluvia y viento vienen sobre todo del servicio de previsión. Estas alertas se calculan en el
teléfono a partir de tu propia previsión: no son oficiales.

### 6.2 Avisos oficiales

Si escribes una **dirección del canal de avisos** (un canal de avisos oficiales en formato CAP,
*Ajustes → Dirección de la API*), la pantalla de previsión muestra los avisos que cubren la ciudad,
citados tal como se emitieron, y puede notificarlos. La aplicación no es un canal de alerta: se
actualiza a su propio ritmo, así que manda la página del emisor. Fuera de la zona del canal, la
aplicación no muestra nada en vez de «ningún aviso».

---

## 7. Ajustes de las fuentes

En [Ajustes](app:settings):

- **Modelo de previsión:** *Automático* deja elegir al servicio; en su lugar se puede elegir uno de
  cinco modelos con nombre. **Modelo por ciudad** lo sustituye para una ciudad. Un interruptor puede
  dibujar la dispersión entre modelos en el gráfico.
- **Fuente preferida** y **Comparar fuentes** ([sección 4.1](#41-una-ciudad-con-dos-fuentes)).
- **Dirección de la API:** las direcciones de previsión, de geocodificación y del canal de avisos,
  cada una vacía hasta que la rellenes.
- **Intervalo de actualización** y datos móviles ([sección 5](#5-actualización)).

---

## 8. Widget y coche

- **Widget:** colócalo en la pantalla de inicio y elige una ciudad y una vista; su tamaño decide
  cuánto muestra. Muestra la previsión guardada y nunca descarga nada por sí mismo.
- **En el coche:** con el teléfono conectado a la pantalla de un coche, elige una ciudad y lee hoy y
  los días siguientes, con la fuente y la antigüedad en la cabecera. Las alertas se quedan en el
  teléfono.

---

## 9. SyncHub

Si tienes un **SyncHub** en casa, la aplicación puede compartir con él sus ciudades, corazones y
ajustes.

1. Abre **SyncHub** al pie del menú. La aplicación busca el hub en tu red, o escribes su dirección.
2. En la interfaz web del hub, abre **Ajustes → Dispositivos → Emparejar un dispositivo** y escanea el
   código QR con la aplicación.

- **Fiabilidad** (en el menú) muestra, para cada ciudad con un sensor de temperatura declarado en el
  hub, cuánto se desvió la previsión de cada fuente de lo que midió el sensor, según los días de
  antelación, en 30, 90 o 365 días. Las primeras cifras llegan tras una semana más o menos.
- *Enviar todo de nuevo*, en la pantalla de sincronización, reenvía los datos de la aplicación si al
  hub le falta algo.

---

## 10. Cuando algo falla

- **«Esta página parece construida con JavaScript»:** la aplicación solo lee lo que la página envía;
  prueba otra página del sitio, o añade la ciudad por su nombre.
- **«El robots.txt de esta página prohíbe el acceso automatizado»:** el sitio pide a los robots que no
  lean esa página; la aplicación obedece. Elige otra fuente.
- **La previsión es antigua:** la línea de estado dice por qué falló la última actualización. La
  previsión guardada se queda hasta que una actualización salga bien.
- **Un dato muestra —:** la fuente no lo dio. No es cero.
- Preguntas e ideas: *Ajustes → Acerca de → Enviar comentarios*.
