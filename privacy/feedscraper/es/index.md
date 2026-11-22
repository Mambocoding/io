<!-- Source: Mambocoding/FeedScraper, specs/SPEC-055-privacy-policy.md, section *The policy, verbatim — es*, at commit 82b5037 on dev. Copied verbatim (date filled in, contact linked, language bar added); the source is right if the two ever disagree. -->

# FeedScraper — Política de privacidad

*[English](../) · [Français](../fr/) · [Deutsch](../de/) · Español · [Nederlands](../nl/)*

*Última actualización: 2026-11-22*

FeedScraper es un lector de fuentes que funciona por completo en tu dispositivo.

**Qué se recopila: nada.** No hay cuenta ni registro. La aplicación no envía a nadie datos de uso, analíticas, informes
de fallos ni identificador publicitario, y no contiene ninguna biblioteca que lo haga. Nadie, ni siquiera el
desarrollador, puede ver lo que lees.

**Qué se guarda, y dónde.** Tus suscripciones, los artículos obtenidos de ellas, cuáles has leído o marcado con estrella,
las copias que guardaste para leer sin conexión y tus ajustes se guardan solo en tu dispositivo, en el almacenamiento
privado de la aplicación. La aplicación también desactiva la copia de seguridad en la nube del sistema para sus datos, de
modo que nada de ello se copia fuera del dispositivo por esa vía.

**Qué sale de tu dispositivo.** Solo las solicitudes siguientes, de cuatro tipos:

1. **Las fuentes a las que te suscribiste.** La aplicación obtiene cada fuente de la dirección que le diste. Cuando abres
   un artículo, lo guardas para leerlo sin conexión o haces que la aplicación muestre su imagen, obtiene esa página o esa
   imagen del sitio al que apunta la fuente. Esas solicitudes van a los editores de las fuentes que elegiste, y cada uno
   ve lo que muestra cualquier solicitud web: la dirección solicitada y la dirección de red desde la que la hiciste.
2. **Un hub que emparejaste, si emparejaste uno.** La sincronización es opcional y está desactivada hasta que la
   configures, y el hub es una máquina que gestionas tú mismo: este proyecto no opera ningún servidor de ningún tipo.
   Cuando emparejas uno, la aplicación le envía tus suscripciones, tus marcas de leído, con estrella y guardado, y tus
   ajustes, y recibe lo mismo de tus otros dispositivos. **No** envía los artículos guardados en el dispositivo, ni su
   propio registro de qué fuentes no se pudieron obtener. La conexión se hace solo con la máquina que emparejaste,
   identificada por un certificado que confirmaste al emparejarla. Para ayudarte a encontrar tu hub, la pantalla de
   emparejamiento pregunta a los dispositivos de tu red doméstica si hay un hub; la solicitud no sale de tu red doméstica,
   y puedes escribir la dirección del hub en su lugar. Conectar con el propio hub nunca va más allá de la dirección que
   emparejaste.
3. **Los anuncios, salvo que los desactives.** Aproximadamente una vez al día, mientras la aplicación está abierta, lee un
   archivo público de anuncios del repositorio público del desarrollador. La solicitud es anónima: sin cuenta, sin cookie
   y sin ningún identificador tuyo ni de tu dispositivo. Como cualquier solicitud web, muestra la dirección de red de tu
   dispositivo al servidor de ese archivo. *Recibir anuncios*, en la lista de anuncios dentro de *Ajustes*, la detiene;
   no se solicita nada mientras esté desactivado.
4. **Un servicio de asistente que configuraste, si configuraste uno.** El asistente está desactivado hasta que lo
   activas, aceptas lo que envía, introduces la dirección de un servicio y tu propia clave, y una prueba tiene éxito.
   Después, y solo cuando tocas *Resumir* o *Traducir* en un artículo, la aplicación envía el título y el texto de ese
   artículo, y el idioma en que se muestra la aplicación, a la dirección que introdujiste: nada más, nunca en segundo
   plano. Ese servicio los trata según sus propias condiciones y su propia política de privacidad, que aceptaste con él,
   y te factura directamente; el desarrollador nunca los recibe. Tu clave se queda en este dispositivo, cifrada, y nunca
   se incluye en una copia de seguridad ni se sincroniza.

No hay ningún otro destino.

Tres cosas salen de la aplicación solo cuando lo pides, y solo hacia una aplicación de tu teléfono: compartir un artículo
entrega su título y su dirección a la aplicación que eliges en el menú para compartir del sistema; abrir un artículo en
la pestaña del navegador integrado entrega su dirección a tu navegador, que luego obtiene la página por sí mismo; y leer
un artículo en voz alta entrega su título y su texto al motor de texto a voz configurado en tu teléfono, algunos de los
cuales usan voces en línea, una elección que se hace en los ajustes de tu teléfono, no en esta aplicación. Ninguna de
ellas va al desarrollador.

**Permisos, y para qué sirve cada uno.** Acceso a Internet, para obtener las fuentes. Estado de la red, para saber si
usas una conexión de uso medido antes de descargar imágenes. Estado del Wi-Fi y multidifusión Wi-Fi, usados solo para
listar los hubs de tu red doméstica mientras emparejas uno o buscas uno que cambió de dirección; escribir la dirección
funciona sin ellos. Acceso a la red local, en Android 17 y posteriores, solicitado la primera vez que una sincronización
lo necesita, para llegar a tu propio hub en tu red doméstica; rechazarlo mantiene todas las fuentes en tu teléfono y solo
detiene la sincronización. Notificaciones, opcionales y usadas solo para las fuentes sobre las que pediste que se te
avise. La cámara, opcional, solo se solicita en el momento en que tocas *Escanear* para emparejar un hub, y nunca es
necesaria: puedes escribir los mismos datos a mano. Si activas el bloqueo de la aplicación, esta pide al sistema que
verifique tu huella dactilar o el PIN del dispositivo; nunca recibe ni guarda ninguno de los dos.

**Llevarte tus datos.** La aplicación puede exportar tus suscripciones y ajustes a un archivo, en la ubicación que
elijas. Solo se escribe cuando lo pides.

**Eliminar tus datos.** Desinstalar la aplicación elimina todo lo que guardó. No existe ninguna copia en otro lugar que
tengas que solicitar.

**Menores.** La aplicación no está dirigida a menores, y no recopila nada de nadie, de ninguna edad.

**Cambios en esta política.** Si el comportamiento de la aplicación cambia, este texto cambia con él, en la misma
versión, y la fecha de arriba cambia.

**Quién es el responsable, y tu derecho a reclamar.** El responsable del tratamiento de esta aplicación es Mambocoding,
mambocoding@gmail.com. Como la aplicación no recopila nada ni envía nada al desarrollador, este no tiene datos personales
tuyos a los que acceder, que rectificar o que suprimir. Si crees que tus datos se han tratado de forma ilícita, tienes
derecho a presentar una reclamación ante una autoridad de control de protección de datos, en particular en el país donde
vives, donde trabajas o donde crees que se produjo la infracción.

**Contacto.** Las preguntas sobre esta política pueden plantearse en el [gestor de incidencias público](https://github.com/Mambocoding/io/issues) del repositorio
público del desarrollador, `Mambocoding/io`, enlazado desde la página de la aplicación en la tienda.
