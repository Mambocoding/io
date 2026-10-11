# FlightScraper — guía de uso

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · Español · [Nederlands](README-nl.md)*

Escrita para FlightScraper 0.1.79 (octubre de 2026). Si esta guía y la aplicación no dicen lo mismo,
la aplicación tiene razón.

---

## 1. Qué es FlightScraper

FlightScraper vigila **un aeropuerto** y lleva un **registro de sus movimientos**: cada aterrizaje y
cada despegue que observa, con indicativo, matrícula, tipo de aeronave, operador y hora. Las
**reglas de vigilancia** pueden avisarte cuando llega una aeronave que te interesa.

- Lee **posiciones ADS-B** — lo que las aeronaves emiten por sí mismas —, no un horario. Por eso ve
  también vuelos que ningún horario recoge: militares, gubernamentales, traslados, desvíos o vuelos de
  prueba.
- Un movimiento es una **deducción** a partir de posiciones, así que cada uno lleva su confianza:
  *observado*, *deducido* o *incierto*. Un campo que falta aparece como **—**, nunca adivinado.
- Solo muestra lo que se emite alrededor de un aeropuerto. No es un seguidor de vuelos ni una
  herramienta de vigilancia.

La aplicación no nombra ningún servicio de datos: eres **tú** quien le da la dirección de una fuente.

---

## 2. Primeros pasos

1. **Elige tu aeropuerto:** *Aeropuertos* en el menú → busca por nombre, ciudad o código. El
   directorio de aeropuertos viene con la aplicación y funciona sin conexión; rellena por ti las
   coordenadas, la altitud y la zona horaria. Ajusta el **radio** (hasta dónde mirar alrededor del
   aeropuerto, en km). Se pueden guardar varios aeropuertos; se vigila exactamente uno.
2. **Introduce una fuente:** [Ajustes](app:settings) → *Fuente de datos*. Pega la dirección de una
   fuente ADS-B que tengas derecho a usar (un agregador comunitario, o tu propio receptor). Si la
   fuente acepta un círculo, usa `{lat}`, `{lon}` y `{radius_nm}`: la aplicación los rellena.
   **Probar** consulta una vez y dice cuántas aeronaves volvieron.
3. Espera dos consultas: la **primera solo registra lo que ya está ahí**; los movimientos aparecen a
   partir de la segunda.

---

## 3. El registro de movimientos

**Movimientos** es la pantalla de inicio: del más reciente al más antiguo, agrupados por día.

- Cada fila: una flecha (llegada o salida), la hora local, el indicativo, el designador de tipo y su
  descripción, la matrícula, las reglas que coincidieron y una marca de confianza.
- El menú ⋮ filtra **Llegadas / Salidas / Todos**, **muestra u oculta los sin coincidencia**, ordena
  y actualiza. La lupa busca en el registro.
- **La línea de estado** sobre la lista dice cuándo fue la última consulta correcta y cuántas
  aeronaves había en el círculo, o por qué falló la última. Un fallo nunca quita nada.
- Toca un movimiento para ver su **detalle**: identidad, horas, confianza con una frase que la
  explica, reglas que coincidieron, un resumen de la trayectoria y **esta aeronave aquí** — cuántas
  veces vino antes.
- La barra de acciones del detalle: **Compartir** (como texto), **Abrir fuera** en el seguidor que
  elijas ([sección 7](#7-enlaces-a-un-seguidor-de-vuelos)), **Eliminar**.

---

## 4. En vivo y Mapa

- **En vivo** lista las aeronaves que están en el círculo ahora, con distancia y altitud,
  actualizadas mientras la pantalla está abierta. Su sección **Esperado** muestra aeronaves que se
  acercan al aeropuerto — una predicción, señalada como tal, dada como un intervalo, y que desaparece
  cuando deja de valer.
- **Mapa** dibuja las mismas aeronaves donde están, alrededor del aeropuerto y su círculo. Un mapa de
  fondo solo aparece si escribes una dirección de teselas en *Ajustes → Fuente de teselas del mapa*;
  el mapa funciona sin ella.

En vivo y Mapa solo consultan mientras están en pantalla.

---

## 5. Reglas de vigilancia y notificaciones

Las **reglas de vigilancia** deciden qué movimientos te importan.

- Una regla combina criterios: un **tipo** exacto (`A332`), una **familia de tipos** (un prefijo),
  **militar**, un **prefijo de indicativo**, una **matrícula**, palabras en la **descripción** o el
  **operador**, una **primera visita** de esta aeronave o de este tipo, un código **squawk**. Deben
  cumplirse *todos* o *alguno*.
- Elige llegadas, salidas o ambas, y una importancia. Prueba una regla contra el registro antes de
  que avise: la pantalla muestra con qué movimientos pasados habría coincidido.
- Las **notificaciones** están desactivadas hasta que las actives (*Ajustes → Notificaciones*). Se te
  avisa **una vez** por aeronave, sentido y día, sea cual sea el número de reglas que coincidan.
- El **horario silencioso** (22:00–07:00 en el aeropuerto por defecto) retiene las notificaciones
  hasta la mañana; una regla de alta importancia puede ignorarlo.
- Una regla también puede avisarte cuando una aeronave que coincide **se aproxima**, antes de que
  aterrice.

---

## 6. Consultas: cada cuánto mira la aplicación

- Mientras En vivo, Mapa o Vigilancia activa están abiertos: cada minuto por defecto (nunca más a
  menudo que cada 30 segundos). Tras fallos, la aplicación espera más — 1, 2, 4 y luego 8 minutos.
- En segundo plano: más o menos cada 15 minutos, lo que aún capta una llegada, con hasta 15 minutos de
  retraso.
- **Horario de sondeo** (*Ajustes → Notificaciones*): en las horas que elijas, el segundo plano
  consulta en ráfagas cortas.
- **Vigilancia activa:** durante una tarde, sigue consultando al ritmo del primer plano con la
  pantalla apagada, durante el tiempo que fijes. Mientras funciona se muestra una notificación, con
  un botón *Detener*.

---

## 7. Enlaces a un seguidor de vuelos

FlightScraper no nombra ningún seguidor de vuelos. En *Ajustes → Enlaces*, añade las plantillas de
dirección de los seguidores que uses, con marcadores que la aplicación rellena con el movimiento
(matrícula, indicativo, código hexadecimal…). El primer enlace es el predeterminado de *Abrir
fuera*. La aplicación nunca descarga estas direcciones por sí misma.

---

## 8. Horarios (experimental)

*Herramientas → Horarios* muestra el panel de llegadas y salidas del aeropuerto vigilado, leído de
páginas cuyas direcciones pegas. Se queda **al lado** del registro, nunca dentro: nada de lo que lee
se convierte en un movimiento ni dispara una alerta. Se señalan las filas que el registro
probablemente vio.

---

## 9. Tus datos

- *Ajustes → Datos → Copia de seguridad y restauración* guarda el registro, los aeropuertos, las
  reglas, los enlaces y los ajustes en un archivo, y los restaura.
- *Ajustes → Registro* fija cuánto tiempo se conservan los movimientos (para siempre por defecto) y
  **exporta el registro** como archivo de hoja de cálculo (CSV).

---

## 10. Cuando algo falla

- **«Ninguna fuente configurada»:** introduce una dirección de fuente
  ([sección 2](#2-primeros-pasos)).
- **«La fuente está limitando a esta aplicación»:** la fuente pide a la aplicación que vaya más
  despacio; se espacia sola. Elige un intervalo más largo si se repite.
- **No aparece nada tras la primera consulta:** es normal — los movimientos empiezan con la segunda.
- **Un movimiento dice *incierto*:** la trayectoria tenía huecos; la aplicación dice lo que vio, nada
  más.
- **No llegan las notificaciones:** comprueba que estén activadas en la aplicación, permitidas por el
  teléfono, y que no estés en horario silencioso. El ahorro de batería del teléfono puede retrasar
  las consultas en segundo plano: en *Ajustes* hay una fila para excluir la aplicación.
- Preguntas e ideas: *Ajustes → Acerca de → Enviar comentarios*.
