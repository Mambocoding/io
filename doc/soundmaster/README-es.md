# SoundMaster — guía de uso

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · Español · [Nederlands](README-nl.md)*

Escrita para SoundMaster 0.1.48 (octubre de 2026). Si esta guía y la aplicación no dicen lo mismo,
la aplicación tiene razón.

---

## 1. Qué es SoundMaster

SoundMaster es un **sonómetro**: muestra, en decibelios, cuánto ruido hay alrededor de tu teléfono.
También **graba** sonido cuando se lo pides.

Promete lo que un teléfono puede cumplir, y nada más:

- **Calibrado** frente a un sonómetro real, una medida acierta con unos **±3 dB**. Con el valor de
  partida, puede desviarse unos **±10 dB**.
- Dos medidas en el mismo teléfono se comparan bien (unos ±3 dB), incluso sin calibrar.
- El rango útil va aproximadamente de **30 a 95 dB**.

Responde a *«¿hay ruido en esta sala?»*, nunca a *«¿incumple esto una norma?»*: no es un
instrumento de clase 1 ni 2. *Ajustes → Acerca de* incluye la declaración completa.

---

## 2. Primer inicio

SoundMaster necesita el **micrófono**. Nunca lo pide por sí solo al abrirse: Medición muestra una
frase y un botón **Permitir acceso al micrófono**. Si lo rechazaste de forma definitiva, Medición lo
dice y ofrece abrir los ajustes del sistema.

El micrófono solo se usa mientras la aplicación está en pantalla. No se mide ni se graba nada en
segundo plano.

---

## 3. Medir

**Medición** es la primera pantalla.

- La **aguja** muestra el nivel actual; el número grande es el mismo nivel.
- Las dos **marcas** del arco, *Mín* y *Máx*, retienen el nivel más bajo y más alto de la aguja
  desde que se abrió la aplicación o desde el último reinicio.
- El **arco** pasa de verde a rojo al subir el nivel (rojo desde 85 dB).
- Bajo el número, un sonido cotidiano de nivel parecido da una idea de la escala.
- La línea bajo el número dice cómo se calcula el nivel: *ponderado A* o *sin ponderar*, *rápido* o
  *lento* ([sección 6](#6-ajustes-que-cambian-la-medida)).

Algunos estados **no son niveles**, y la aplicación nunca los muestra como números:

- **Saturación** — el sonido es demasiado fuerte para el micrófono; el nivel real es mayor que
  cualquier cifra mostrada.
- **Sin señal** — el micrófono entrega silencio puro (a menudo otra aplicación lo ocupa).
- *por debajo del rango útil* — una sala tranquila, bajo unos 30 dB: el número se mantiene, pero
  fíate menos.

### 3.1 Una medición: medir un rato y guardar

La **barra de acciones** de abajo actúa sobre la medición:

1. **Iniciar** (el pequeño icono de gráfico) empieza una medición; el mismo botón la detiene.
2. Durante una medición, **Esta medición** muestra su nivel más bajo y más alto y su **Leq** (la
   energía media de la medición), con un trazo de los últimos 60 segundos.
3. **Guardar sesión** conserva el resultado en el **Historial**. *Reiniciar la medición* borra la
   medición y las marcas. **Compartir** envía la lectura actual como texto.

Salir de la aplicación pausa la medición; continúa al volver. Cambiar la ponderación en frecuencia,
o un cambio de fuente del micrófono, termina la medición, lista para guardar.

### 3.2 La alerta

Por encima del **umbral de alerta** (85 dB salvo que lo cambies), Medición se vuelve roja e indica
cuánto se supera. Se puede activar una **alerta sonora** (un pitido corto); está desactivada por
defecto porque el propio micrófono del teléfono oye el pitido. La alerta vale lo que vale la
calibración que hay detrás.

---

## 4. Espectro

**Espectro** divide el sonido en diez bandas de octava, de 31,5 Hz a 16 kHz, y muestra qué banda
domina. Las bandas son **relativas**: dicen qué parte del sonido es la más fuerte, nunca un nivel en
dB por banda. *Congelado* en el menú ⋮ fija la imagen; *En directo* la reanuda.

---

## 5. Grabar

El botón redondo **Grabar**, en **Grabación** y en Medición cuando no hay medición en curso, inicia
una grabación; **Pausa** y **Reanudar** están al lado.

- Las grabaciones se listan de la más reciente a la más antigua, con su duración y tamaño, y marcas
  de *saturada* y *pausada*. Reproduce una en la propia lista.
- Selecciona una grabación para la barra de acciones: **eliminar**, **compartir**, **cambiar
  nombre** y **descargar** (una copia en la carpeta que elijas).
- Grabar no cambia la medida: el sonómetro sigue midiendo.
- Las grabaciones se quedan en el teléfono. No están en la copia de seguridad de la aplicación, y
  una grabación termina cuando la aplicación sale de la pantalla.

### 5.1 Transcribir una grabación

**Transcribir**, en la barra de acciones de Grabación, convierte la voz de una grabación en texto
**en el teléfono**, con el reconocimiento de voz del sistema. No se envía nada a ningún sitio.
Requiere Android 13 o posterior y un teléfono cuyo reconocimiento funcione sin conexión; si tu
idioma no está instalado, la pantalla ofrece descargarlo desde el sistema. La transcripción se puede
copiar o compartir, y puede contener errores.

---

## 6. Ajustes que cambian la medida

En [Ajustes](app:settings) → *Medición*:

- **Ponderación en frecuencia:** *Ponderado A* (por defecto, cercano al oído) o *Sin ponderar*.
- **Ponderación temporal:** *Rápida (125 ms)*, por defecto, sigue los cambios enseguida; *Lenta
  (1 s)* calma la aguja.
- **Umbral de alerta** y **Alerta sonora** ([sección 3.2](#32-la-alerta)).
- **Iniciar una medición al abrir:** una medición empieza sola con la primera lectura tras abrir la
  aplicación.
- **Calibración** ([sección 7](#7-calibración)).
- **Niveles típicos:** sonidos cotidianos y su nivel habitual, la lista con la que compara Medición.

---

## 7. Calibración

Cada micrófono de teléfono es distinto. La **calibración** suma un desfase, en dB, a todas las
medidas.

1. Pon SoundMaster junto a un **sonómetro real**, en el mismo lugar, con un sonido estable.
2. Abre *Ajustes → Medición → Calibración* y ajusta el desfase hasta que ambos marquen lo mismo.

*Usar el valor de partida* vuelve a +110 dB. Otra aplicación de teléfono no es una referencia: solo
comprueba que nada esté muy mal. Cada sesión guardada conserva el desfase con el que se midió.

---

## 8. Historial

El **Historial** lista las sesiones guardadas, de la más reciente a la más antigua: fecha, duración,
Leq, nivel más bajo y más alto, pico, ponderaciones, desfase y fuente del micrófono. Una sesión
saturada marca sus cifras: son mínimos, no niveles. Selecciona sesiones para eliminarlas o
compartirlas.

---

## 9. Hacer una copia de la aplicación

*Ajustes → Copia de seguridad y restauración* guarda los ajustes y el historial de sesiones en un
archivo (nunca el audio), y los restaura.

- La **copia automática** crea ese archivo cada día.
- Si tienes un SyncHub, la copia también puede guardarse **en el hub**: empareja desde la pantalla
  de copia, con el código que muestra el hub. Ese emparejamiento abre las copias de SoundMaster y
  nada más. Es la única vez que la aplicación usa la red.

---

## 10. Cuando algo falla

- **«No se pudo abrir el micrófono»:** quizá otra aplicación lo ocupa, o el teléfono rechaza este
  tipo de captura. Cierra la otra aplicación y vuelve a SoundMaster.
- **Sin señal** aunque la sala no está en silencio: otra aplicación o una llamada ocupa el
  micrófono.
- **«Tus ajustes estaban dañados y se han restablecido»:** la aplicación empezó de cero, con el
  desfase de partida. **Tus sesiones y grabaciones están a salvo**; vuelve a calibrar.
- Preguntas e ideas: *Ajustes → Acerca de → Enviar comentarios*.
