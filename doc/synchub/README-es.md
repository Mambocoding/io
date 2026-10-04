# SyncHub — guía de uso

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · Español · [Nederlands](README-nl.md)*

Escrita para SyncHub 0.2.216 (octubre de 2026). Si esta guía y las páginas del hub no coinciden, el
hub tiene razón.

---

## 1. Qué es SyncHub

SyncHub es un pequeño servidor que usted ejecuta **en su propia máquina** — normalmente un NAS en
casa — para que los datos de sus apps se queden en casa en lugar de en la nube de otro.

- Guarda los datos de varias apps (fuentes, tiempo, bolsa, notas) para **varias personas**; cada
  cuenta está completamente separada de las demás.
- **Descarga sus contenidos día y noche**, así que un teléfono que estuvo apagado no se pierde nada.
- Ofrece una **interfaz web** en el navegador con el mismo contenido que su teléfono.
- **Sincroniza en ambos sentidos**: lo que marca como favorito o como leído en el navegador aparece en
  el teléfono, y al revés.

Es **opcional**: una app sin hub configurado funciona exactamente como antes.

**Nunca se abre a Internet.** Solo responde en su red doméstica. Acceder desde fuera es decisión
suya, mediante una VPN o su propio proxy inverso (vea la [sección 12](#12-acceder-desde-fuera-de-casa)).

---

## 2. Qué necesita

- Una máquina siempre encendida que ejecute **contenedores** (un NAS con gestor de contenedores, un
  pequeño servidor Linux, un mini PC). Se admiten `amd64` y `arm64`.
- Unos **300 MB de memoria** libres y unos cientos de MB de disco, más lo que ocupen sus archivos y
  adjuntos.
- **Red del anfitrión** (`network_mode: host`, Linux) para el contenedor. Sin ella todo funciona,
  salvo que el teléfono no encontrará el hub por sí solo: tendrá que escribir su dirección.
- La **dirección de la máquina en su red doméstica**, por ejemplo `192.168.1.20`. La lista de
  dispositivos conectados de su router la muestra. Lo ideal es que el router le dé siempre la misma
  dirección a esa máquina.

---

## 3. Instalación

### 3.1 Crear una carpeta y dos archivos

Cree una carpeta para SyncHub en la máquina (por ejemplo `/volume1/docker/synchub` o `~/synchub`) y
ponga en ella estos dos archivos.

**`compose.yml`**

```yaml
name: synchub

services:
  synchub:
    image: ghcr.io/mambocoding/synchub:${SYNCHUB_TAG:?set SYNCHUB_TAG in the .env beside this file}
    restart: unless-stopped
    network_mode: host
    cap_drop: [ALL]
    security_opt:
      - no-new-privileges:true
    read_only: true
    tmpfs:
      - /tmp
    volumes:
      - synchub-data:/data
      - launcher-state:/launcher
    environment:
      SYNCHUB_BIND: "0.0.0.0"
      # La dirección de su máquina en la red doméstica, después de synchub.local. Obligatoria.
      SYNCHUB_ALLOWED_HOSTS: "synchub.local,192.168.XXX.XXX"
      SYNCHUB_TLS_KEYSTORE_PASSWORD: "${SYNCHUB_TLS_KEYSTORE_PASSWORD:?set it in the .env beside this file}"
      # Su zona horaria, para que las fechas de las páginas web sean correctas.
      TZ: "Europe/Madrid"
      # Opcional, necesaria para el inicio de sesión en dos pasos (sección 9).
      # SYNCHUB_SECRET_KEY: ""

  # Opcional: el lanzador, que añade un botón "Aplicar actualización" (sección 10.2).
  synchub-launcher:
    profiles: ["launcher"]
    image: ghcr.io/mambocoding/synchub-launcher:${SYNCHUB_LAUNCHER_TAG:-latest}
    restart: unless-stopped
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - launcher-state:/state
      - ${SYNCHUB_PROJECT_DIR:-/unset}:${SYNCHUB_PROJECT_DIR:-/unset}
      - ${SYNCHUB_PROJECT_DIR:-/unset}/compose.yml:${SYNCHUB_PROJECT_DIR:-/unset}/compose.yml:ro
    environment:
      SYNCHUB_PROJECT_DIR: "${SYNCHUB_PROJECT_DIR:-}"
      SYNCHUB_COMPOSE_PROJECT: "${SYNCHUB_COMPOSE_PROJECT:-synchub}"
      SYNCHUB_SERVICE: "synchub"
      SYNCHUB_LAUNCHER_POLL_SECONDS: "${SYNCHUB_LAUNCHER_POLL_SECONDS:-10}"

volumes:
  synchub-data:
    name: synchub-data
  launcher-state:
    name: synchub-launcher-state
```

**`.env`** (el nombre empieza por un punto)

```sh
# La versión de SyncHub que se ejecuta: tres números, nunca "latest".
SYNCHUB_TAG=

# Una contraseña que protege el certificado del hub. Elíjala ahora y no la cambie nunca.
SYNCHUB_TLS_KEYSTORE_PASSWORD=

# Solo para el lanzador opcional (sección 10.2): la ruta absoluta de esta carpeta.
SYNCHUB_LAUNCHER_TAG=latest
SYNCHUB_PROJECT_DIR=
```

### 3.2 Rellenar cuatro valores

| Dónde | Qué escribir |
| --- | --- |
| `.env` → `SYNCHUB_TAG` | La versión actual. Se publica en <https://raw.githubusercontent.com/Mambocoding/io/main/synchub/latest.json> (campo `version`), por ejemplo `0.2.216`. |
| `.env` → `SYNCHUB_TLS_KEYSTORE_PASSWORD` | Una contraseña larga y aleatoria. Guarde una copia: si se pierde, el hub ya no puede abrir su certificado y hay que volver a emparejar cada teléfono. |
| `compose.yml` → `SYNCHUB_ALLOWED_HOSTS` | Sustituya `192.168.XXX.XXX` por la dirección de su máquina. El hub rechaza cualquier petición a una dirección que no esté en esta lista, con un simple *Bad Request*. |
| `compose.yml` → `TZ` | Su zona horaria (`Europe/Madrid`, `Atlantic/Canary`, `America/Mexico_City`, `America/Argentina/Buenos_Aires`…). |

Mantenga `compose.yml` y `.env` **juntos** en la misma carpeta: el primero no arranca sin el segundo.

### 3.3 Arrancar

En esa carpeta:

```sh
docker compose up -d
docker compose logs synchub
```

No hace falta cuenta ni contraseña para descargar la imagen. Muchos gestores de contenedores de NAS
también pueden importar un `compose.yml` como "proyecto"; el resultado es el mismo.

En el registro, busque estas líneas:

```
First run: admin account created.
Setup token (use as the admin password): ...
Serving https://192.168.1.20:8443
TLS certificate SHA-256 fingerprint: A1:B2:...
```

Copie el **token de configuración** (*setup token*): es la primera contraseña de la cuenta de
administrador.

---

## 4. Primer inicio de sesión

1. En un navegador de su red doméstica, abra **`https://synchub.local:8443`** o
   **`https://<dirección de su máquina>:8443`**.
2. El navegador avisa de que la conexión no es de confianza. La primera vez es normal: acepte el
   aviso para continuar. La [sección 6](#6-un-candado-en-el-navegador) lo elimina para siempre.
3. Inicie sesión como `admin` con el token de configuración como contraseña.
4. Se abre un **asistente de configuración**: le guía para emparejar un teléfono, activar el inicio
   de sesión en dos pasos, elegir la dirección que usarán sus teléfonos y ajustar la red. Puede
   volver a él cuando quiera desde **Ajustes → Configuración**.
5. Cambie la contraseña del administrador: **Ajustes → Cuenta → Cambiar contraseña** (12 caracteres
   como mínimo).

**Active las apps que usa** en **Ajustes → Apps** (solo administradores). Cada una se activa o
desactiva al instante, sin reiniciar.

---

## 5. Emparejar un teléfono

1. En la app del teléfono, abra los ajustes del hub. La app **encuentra el hub por sí sola** en su
   red y ofrece *SyncHub en 192.168.1.20*. Si no, escriba `https://<dirección>:8443`.
2. En el navegador, abra **Ajustes → Dispositivos → Emparejar un dispositivo**. Aparece un **código
   QR**, con un código, la dirección y la huella del certificado escritos debajo.
3. **Escanee el código QR** con la app. Mejor escanear que teclear: así la app comprueba la huella
   del certificado exactamente, carácter por carácter.
4. El código vale **cinco minutos** y **una sola vez**. Si caduca, pulse de nuevo
   *Emparejar un dispositivo*.

El teléfono pertenece a la cuenta que creó el código. Cada app (fuentes, tiempo, bolsa, notas) se
empareja por separado y aparece en su propia línea en **Ajustes → Dispositivos**.

**Mire la columna *Sincronizado***, no *Visto por última vez*: *Visto por última vez* solo dice que
el teléfono llamó a la puerta; *Sincronizado* dice que de verdad pasaron datos. *nunca* significa que
la primera sincronización real del teléfono aún no ha ocurrido.

---

## 6. Un candado en el navegador

El certificado del hub lo crea el propio hub, así que ningún navegador confía en él de entrada. A su
teléfono no le afecta (recuerda el certificado exacto al emparejarse), pero el navegador avisa cada
vez. Para quitar el aviso, instale **una vez** el **certificado raíz** del hub en cada ordenador o
teléfono desde el que navegue.

### 6.1 Descargarlo

Como administrador, abra **Ajustes → Dispositivos**, apartado **Confianza del navegador**, y pulse
**Descargar certificado raíz**. Obtendrá un archivo `synchub-ca.crt`.

Esta raíz solo puede responder por `synchub.local`, `localhost` y las direcciones de su hub — por
nada más en Internet.

> **¿No hay botón de descarga?** El apartado **solo lo ven los administradores**. Si es
> administrador y el apartado indica que el hub no tiene certificado raíz, su hub se instaló antes de
> esta función: conserva su certificado antiguo y nunca lo sustituirá por sí mismo. La única forma de
> obtener una raíz es borrar el certificado (`/data/keystore.p12`) y reiniciar, lo que **obliga a
> cada teléfono emparejado a confirmar el nuevo certificado** (Ajustes → Dispositivos muestra un
> código QR para ello) o a emparejarse de nuevo. Hasta entonces, siga aceptando el aviso del
> navegador.

### 6.2 Instalarlo

**Windows** (Edge, Chrome)
1. Haga doble clic en `synchub-ca.crt` → **Instalar certificado…**
2. Elija **Usuario actual** → **Siguiente**.
3. Elija **Colocar todos los certificados en el siguiente almacén** → **Examinar…** →
   **Entidades de certificación raíz de confianza** → **Aceptar** → **Siguiente** → **Finalizar**.
4. Confirme el aviso de seguridad con **Sí** y cierre y vuelva a abrir el navegador.

**macOS** (Safari, Chrome)
1. Haga doble clic en `synchub-ca.crt`: se abre Acceso a Llaveros y lo añade al llavero *inicio de
   sesión*.
2. Haga doble clic en el certificado *SyncHub Local CA* → **Confiar** → *Al utilizar este
   certificado*: **Confiar siempre**. Cierre la ventana e introduzca su contraseña.

**Android**
1. Abra los **Ajustes** del teléfono → **Seguridad y privacidad** → **Más ajustes de seguridad** →
   **Cifrado y credenciales** → **Instalar un certificado** → **Certificado de CA**.
2. Confirme el aviso y elija `synchub-ca.crt` en sus descargas.
3. Los nombres de los menús varían algo según el fabricante; busque "certificado" en los ajustes.

**Linux** (Chrome, Chromium) — **Configuración → Privacidad y seguridad → Seguridad → Gestionar
certificados**, importe el archivo como **entidad** de confianza.

**Firefox** (todos los sistemas) tiene su propia lista — **Ajustes → Privacidad & Seguridad →
Certificados → Ver certificados… → Autoridades → Importar…**, y marque **Confiar en esta CA para
identificar sitios web**.

Después vuelva a abrir `https://synchub.local:8443`: el candado está ahí.

---

## 7. Varias personas, un solo hub

- **Cada cuenta tiene todo lo suyo**: fuentes, marcas de leído, ciudades, lista de valores, notas,
  ajustes. Nada se comparte entre cuentas, y ningún ajuste lo comparte.
- Por eso una cuenta recién creada está **vacía** — no es una pérdida de datos.
- Un administrador crea y borra cuentas y puede poner una contraseña nueva a quien haya olvidado la
  suya (**Ajustes → Usuarios**), pero **nunca puede leer** los datos de otra persona.
- Roles: toda cuenta es *usuario*; **admin** gestiona el hub; **updater** solo puede aplicar
  actualizaciones.

---

## 8. Sus archivos

Cada cuenta tiene un **espacio de archivos** privado, accesible desde cualquier cliente WebDAV (el
gestor de archivos de su ordenador suele hablarlo). Cree un token en **Ajustes → Cuenta** y conecte
su cliente a `https://<hub>:8443/files/` con su nombre de cuenta y ese token — nunca con su
contraseña.

---

## 9. Inicio de sesión en dos pasos

El inicio de sesión en dos pasos añade a su contraseña un código de seis cifras de una app de
autenticación. Es opcional en un hub que se queda en casa, y **muy recomendable** si accede al hub
desde fuera.

**Antes de que la primera cuenta lo active**, el hub necesita una clave secreta:

1. Genere una: `openssl rand -base64 32`.
2. Póngala en `compose.yml` → `SYNCHUB_SECRET_KEY: "<la clave>"` (quite el `#`) y luego
   `docker compose up -d`.
3. **Guarde una copia de esa clave en un lugar seguro y no la cambie nunca.** Si se pierde, cada
   cuenta que use el inicio de sesión en dos pasos necesita que un administrador la restablezca, y
   restaurar una copia de seguridad exige la misma clave.

Después, cada persona: **Ajustes → Cuenta**, escanea el código QR con una app de autenticación,
confirma con un código y **guarda los diez códigos de recuperación**, que se muestran una sola vez.

Mientras la clave no esté definida, el registro dice `SYNCHUB_SECRET_KEY is not set: two-factor
enrolment is refused until it is.` — sin consecuencias si no usa la función.

---

## 10. Actualizar

El hub comprueba una vez al día si hay una versión nueva y se lo indica a un administrador en
**Ajustes → Acerca de**, junto con lo que la nueva versión le exige (normalmente nada).

### 10.1 A mano — tres pasos

1. En `.env`, ponga `SYNCHUB_TAG` en la nueva versión.
2. `docker compose pull`
3. `docker compose up -d`

Sin el paso 1, la descarga trae la versión que ya tiene.

### 10.2 Con un botón — el lanzador (opcional)

El lanzador es un segundo contenedor pequeño que aplica una actualización cuando un administrador
pulsa **Aplicar actualización** en **Ajustes → Acerca de**, y que registra cada vez que el hub se
detuvo y por qué.

1. En `.env`, ponga `SYNCHUB_PROJECT_DIR` en la ruta absoluta de su carpeta de SyncHub.
2. `docker compose --profile launcher up -d`

**Sepa lo que autoriza**: el lanzador tiene el socket del motor de contenedores, lo que equivale al
control total de la máquina. No acepta del hub ninguna orden aparte de "adelante" y solo instala
versiones oficiales de SyncHub. Si eso le parece demasiado, actualice a mano.

---

## 11. Copias de seguridad

- **Cada día a las 3:30**, el hub guarda una instantánea de su **configuración** (cuentas,
  dispositivos emparejados, tokens, ajustes). **Ajustes → Copia de seguridad** las lista, toma una a
  petición (**Tomar una instantánea ahora**), las descarga, acepta las que suba y las restaura
  (**Restaurar…**).
- Sus **datos** (artículos, notas, listas de valores…) no están en la instantánea: también viven en
  sus teléfonos y vuelven desde ellos.
- Por defecto, las instantáneas están en el mismo disco que los datos. Cópielas a otro sitio con la
  herramienta de copias de su NAS — **apúntela a la carpeta de instantáneas**, no a la base de datos
  en uso, que no se puede copiar con seguridad mientras el hub funciona.
- Las apps también pueden guardar sus propias copias en el hub: **Ajustes → Copias de seguridad**
  muestra las suyas.

Restaurar en una máquina nueva: instale el hub, use **la misma `SYNCHUB_SECRET_KEY`** y elija
*Restaurar una instantánea* en el primer paso de configuración. Después, cada teléfono confirma una
vez el nuevo certificado.

---

## 12. Acceder desde fuera de casa

SyncHub nunca abre por sí mismo una puerta a Internet. Si quiere acceder fuera de casa, use una
**VPN** hacia su red doméstica — la forma más sencilla y segura. Si usa en su lugar un proxy inverso:

- añada a `SYNCHUB_ALLOWED_HOSTS` la dirección que marca su teléfono;
- active antes el **inicio de sesión en dos pasos** en cada cuenta.

---

## 13. Leer el registro de arranque

`docker compose logs synchub` muestra lo que hizo el hub al arrancar. El registro está en inglés. Qué
significan las líneas habituales:

| Línea | Significado | Qué hacer |
| --- | --- | --- |
| `SLF4J(W): No SLF4J providers were found` y `WARNING: A restricted method… sqlite-jdbc` | Mensajes de bibliotecas internas del hub. | Nada. |
| `Applied migration V…` | La base de datos se actualizó para la nueva versión. | Nada. |
| `First run: admin account created.` + `Setup token…` | El hub arrancó sobre un volumen de datos **vacío**. | En la primera instalación: inicie sesión con el token. **Tras una actualización: no se conservó su volumen de datos** — vea la [sección 14](#14-si-algo-va-mal). |
| `SYNCHUB_SECRET_KEY is not set…` | El inicio de sesión en dos pasos no está disponible. | Nada, o la [sección 9](#9-inicio-de-sesión-en-dos-pasos). |
| `Data directory: /data — docker volume "synchub-data"` | Dónde están sus datos. | Compruebe que nombra el **mismo** volumen tras cada actualización. |
| `Allowed Host headers: [synchub.local, 192.168.1.20]` | Las direcciones a las que responde el hub. | La dirección que usan su teléfono y su navegador debe estar en la lista. |
| `TLS: adopted the existing keystore…` | El hub conservó su certificado. Normal en cada arranque tras el primero. | Nada. |
| `TLS keystore … is readable by group or others` | El archivo con la clave privada del certificado es legible por otros en la máquina. | Una vez: `docker compose exec synchub chmod 600 /data/keystore.p12` y reinicie. Nada más cambia. |
| `Serving https://192.168.1.20:8443` | La dirección que hay que abrir. También se anuncia en su red, para que los teléfonos la encuentren. | Nada. Si ve *not advertising*, la misma línea dice por qué. |
| `TLS handshake refused by 192.168.1.42 — the peer rejected this hub's certificate` | El dispositivo de esa dirección rechazó el certificado del hub. | Si es un **ordenador**: su navegador aún no confía en el hub, vea la [sección 6](#6-un-candado-en-el-navegador). Si es un **teléfono emparejado**: su certificado está desfasado, escanee el código QR de **Ajustes → Dispositivos**. |
| `RSS: N subscription(s) … scraped on the phone — not fetched here` | Fuentes que su teléfono lee por sí mismo y que el hub deja de lado. | Nada. |
| `Stocks: N instrument(s) … with no symbol any role speaks` | El hub no puede obtener cotizaciones para esos valores. | Revise las direcciones de la página de ajustes de bolsa; si persiste, comuníquelo. |
| `sync: …` | Una línea por sincronización con un teléfono. | Útil para ver si un teléfono sincroniza de verdad. |

---

## 14. Si algo va mal

**El navegador solo muestra *Bad Request*.** La dirección que escribió no está en
`SYNCHUB_ALLOWED_HOSTS`. Añádala en `compose.yml` y luego `docker compose up -d`. Una vez que el hub
ha guardado este valor, cámbielo en **Ajustes → Configuración**.

**Tras una actualización, el registro muestra un token de configuración nuevo y todos los teléfonos
piden emparejarse otra vez.** El hub arrancó sobre un volumen de datos **vacío**: sus datos no se
borraron, están en otro volumen. Ejecute `docker volume ls` y compruebe que `/data` apunta a
`synchub-data`. En el formulario de contenedores de su NAS, la línea del volumen nunca debe quedar
vacía.

**No ejecute nunca `docker compose down -v`** (ni `docker volume prune`): `-v` **borra** el volumen
de datos — base de datos, certificado y todos los emparejamientos. `docker compose up -d`, `restart`
y `down` sin `-v` son seguros.

**El teléfono dice que el certificado del hub ha cambiado desde el emparejamiento.** El hub tiene un
certificado nuevo. Abra **Ajustes → Dispositivos** y escanee con la app el código QR que aparece: el
teléfono conserva su emparejamiento y confía en el nuevo certificado. Si el hub también perdió sus
datos, empareje de nuevo con **Emparejar un dispositivo**.

**El teléfono dice que el hub no está accesible.** Compruebe por orden: el hub funciona; el teléfono
está en la red doméstica; la dirección que usa está en `SYNCHUB_ALLOWED_HOSTS` (línea `Allowed Host
headers` del registro); abra la misma dirección `https://…` en el navegador del teléfono.

**Un dispositivo aparece en verde en Ajustes → Dispositivos pero no se ve nada.** Mire
*Sincronizado*: *nunca* significa que aún no han pasado datos. **Ajustes → Sincronización** muestra,
colección por colección, lo que el hub guarda para su cuenta.

**`https://synchub.local:8443` no se abre en un teléfono Android.** Los navegadores de Android no
resuelven los nombres `.local`. Use la dirección (`https://192.168.1.20:8443`). A la app no le afecta:
encuentra el hub de otra manera.

---

*Preguntas: abra una incidencia (issue) en este repositorio. Políticas de privacidad de las apps:
[`privacy/`](../../privacy/).*
