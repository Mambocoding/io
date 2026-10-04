# SyncHub — Benutzerhandbuch

*[English](README-en.md) · [Français](README-fr.md) · Deutsch · [Español](README-es.md) · [Nederlands](README-nl.md)*

Geschrieben für SyncHub 0.2.216 (Oktober 2026). Wenn dieses Handbuch und die Seiten des Hubs nicht
übereinstimmen, hat der Hub recht.

---

## 1. Was SyncHub ist

SyncHub ist ein kleiner Server, den Sie **auf Ihrem eigenen Gerät** betreiben — meist einem NAS zu
Hause —, damit die Daten Ihrer Apps bei Ihnen bleiben statt in der Cloud eines anderen.

- Er verwahrt die Daten mehrerer Apps (Feeds, Wetter, Börse, Notizen) für **mehrere Personen**;
  jedes Konto ist vollständig von den anderen getrennt.
- Er **ruft Ihre Inhalte rund um die Uhr ab**, sodass ein ausgeschaltetes Telefon nichts verpasst.
- Er bietet eine **Weboberfläche** im Browser mit denselben Inhalten wie Ihr Telefon.
- Er **synchronisiert in beide Richtungen**: Was Sie im Browser markieren oder als gelesen
  kennzeichnen, erscheint auf dem Telefon, und umgekehrt.

Er ist **optional**: Eine App ohne eingerichteten Hub funktioniert genau wie bisher.

Er **öffnet sich nie zum Internet**. Er antwortet nur in Ihrem Heimnetz. Ihn von außen zu erreichen
ist Ihre Entscheidung, über ein VPN oder Ihren eigenen Reverse Proxy (siehe
[Abschnitt 12](#12-von-unterwegs-zugreifen)).

---

## 2. Was Sie brauchen

- Ein ständig eingeschaltetes Gerät, das **Container** ausführt (ein NAS mit Containerverwaltung, ein
  kleiner Linux-Server, ein Mini-PC). `amd64` und `arm64` werden unterstützt.
- Etwa **300 MB freien Arbeitsspeicher** und einige hundert MB Speicherplatz, dazu den Platz für
  Ihre Dateien und Anhänge.
- **Host-Netzwerk** (`network_mode: host`, Linux) für den Container. Ohne funktioniert alles, nur
  findet Ihr Telefon den Hub nicht von selbst: Sie geben dann seine Adresse ein.
- Die **Adresse des Geräts in Ihrem Heimnetz**, zum Beispiel `192.168.1.20`. Die Geräteliste Ihres
  Routers zeigt sie an. Am besten lassen Sie den Router diesem Gerät immer dieselbe Adresse geben.

---

## 3. Installation

### 3.1 Einen Ordner und zwei Dateien anlegen

Legen Sie auf dem Gerät einen Ordner für SyncHub an (zum Beispiel `/volume1/docker/synchub` oder
`~/synchub`) und speichern Sie darin diese beiden Dateien.

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
      # Die Adresse Ihres Geräts im Heimnetz, nach synchub.local. Pflicht.
      SYNCHUB_ALLOWED_HOSTS: "synchub.local,192.168.XXX.XXX"
      SYNCHUB_TLS_KEYSTORE_PASSWORD: "${SYNCHUB_TLS_KEYSTORE_PASSWORD:?set it in the .env beside this file}"
      # Ihre Zeitzone, damit Datum und Uhrzeit auf den Webseiten stimmen.
      TZ: "Europe/Berlin"
      # Optional, nötig für die Zwei-Faktor-Anmeldung (Abschnitt 9).
      # SYNCHUB_SECRET_KEY: ""

  # Optional: der Launcher, der eine Schaltfläche „Update einspielen" hinzufügt (Abschnitt 10.2).
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

**`.env`** (der Name beginnt mit einem Punkt)

```sh
# Die SyncHub-Version, die laufen soll: drei Zahlen, niemals „latest".
SYNCHUB_TAG=

# Ein Passwort, das das Zertifikat des Hubs schützt. Jetzt wählen und nie mehr ändern.
SYNCHUB_TLS_KEYSTORE_PASSWORD=

# Nur für den optionalen Launcher (Abschnitt 10.2): der absolute Pfad dieses Ordners.
SYNCHUB_LAUNCHER_TAG=latest
SYNCHUB_PROJECT_DIR=
```

### 3.2 Vier Werte eintragen

| Wo | Was eintragen |
| --- | --- |
| `.env` → `SYNCHUB_TAG` | Die aktuelle Version. Sie wird unter <https://raw.githubusercontent.com/Mambocoding/io/main/synchub/latest.json> veröffentlicht (Feld `version`), zum Beispiel `0.2.216`. |
| `.env` → `SYNCHUB_TLS_KEYSTORE_PASSWORD` | Ein langes, zufälliges Passwort. Bewahren Sie eine Kopie auf: Geht es verloren, kann der Hub sein Zertifikat nicht mehr öffnen und jedes Telefon muss neu gekoppelt werden. |
| `compose.yml` → `SYNCHUB_ALLOWED_HOSTS` | Ersetzen Sie `192.168.XXX.XXX` durch die Adresse Ihres Geräts. Der Hub weist jede Anfrage an eine Adresse, die nicht in dieser Liste steht, mit einem bloßen *Bad Request* ab. |
| `compose.yml` → `TZ` | Ihre Zeitzone (`Europe/Berlin`, `Europe/Vienna`, `Europe/Zurich`…). |

Lassen Sie `compose.yml` und `.env` **zusammen** im selben Ordner: Die erste startet nicht ohne die
zweite.

### 3.3 Starten

In diesem Ordner:

```sh
docker compose up -d
docker compose logs synchub
```

Zum Herunterladen des Images sind weder Konto noch Passwort nötig. Viele Containerverwaltungen von
NAS-Geräten können eine `compose.yml` auch als „Projekt" importieren; das Ergebnis ist dasselbe.

Suchen Sie im Protokoll nach diesen Zeilen:

```
First run: admin account created.
Setup token (use as the admin password): ...
Serving https://192.168.1.20:8443
TLS certificate SHA-256 fingerprint: A1:B2:...
```

Kopieren Sie das **Einrichtungs-Token** (*setup token*): Es ist das erste Passwort des
Administratorkontos.

---

## 4. Erste Anmeldung

1. Öffnen Sie in einem Browser in Ihrem Heimnetz **`https://synchub.local:8443`** oder
   **`https://<Adresse Ihres Geräts>:8443`**.
2. Der Browser warnt, dass die Verbindung nicht vertrauenswürdig ist. Beim ersten Mal ist das
   normal; akzeptieren Sie die Warnung, um fortzufahren. [Abschnitt 6](#6-ein-schloss-im-browser)
   beseitigt sie dauerhaft.
3. Melden Sie sich als `admin` mit dem Einrichtungs-Token als Passwort an.
4. Ein **Einrichtungsassistent** öffnet sich: Er führt Sie durch das Koppeln eines Telefons, die
   Zwei-Faktor-Anmeldung, die Adresse, die Ihre Telefone verwenden, und die Netzwerkeinstellungen.
   Sie erreichen ihn jederzeit wieder über **Einstellungen → Einrichtung**.
5. Ändern Sie das Administratorpasswort: **Einstellungen → Konto → Passwort ändern** (mindestens
   12 Zeichen).

**Schalten Sie die Apps ein, die Sie nutzen**, unter **Einstellungen → Apps** (nur Administratoren).
Jede wird sofort ein- oder ausgeschaltet, ohne Neustart.

---

## 5. Ein Telefon koppeln

1. Öffnen Sie in der App auf Ihrem Telefon die Hub-Einstellungen. Die App **findet den Hub von
   selbst** in Ihrem Netz und bietet *SyncHub unter 192.168.1.20* an. Falls nicht, geben Sie
   `https://<Adresse>:8443` ein.
2. Öffnen Sie im Browser **Einstellungen → Geräte → Gerät koppeln**. Ein **QR-Code** erscheint,
   darunter ein Code, die Adresse und der Fingerabdruck des Zertifikats.
3. **Scannen Sie den QR-Code** mit der App. Scannen ist besser als Abtippen: Die App prüft den
   Fingerabdruck des Zertifikats dann exakt, Zeichen für Zeichen.
4. Der Code gilt **fünf Minuten** und **einmal**. Ist er abgelaufen, drücken Sie erneut
   *Gerät koppeln*.

Das Telefon gehört zu dem Konto, das den Code erzeugt hat. Jede App (Feeds, Wetter, Börse, Notizen)
wird einzeln gekoppelt und erscheint als eigene Zeile unter **Einstellungen → Geräte**.

**Lesen Sie die Spalte *Synchronisiert***, nicht *Zuletzt gesehen*: *Zuletzt gesehen* sagt nur,
dass das Telefon angeklopft hat; *Synchronisiert* sagt, dass wirklich Daten übertragen wurden.
*nie* bedeutet, dass die erste echte Synchronisierung des Telefons noch aussteht.

---

## 6. Ein Schloss im Browser

Das Zertifikat des Hubs stellt der Hub selbst aus, daher vertraut ihm kein Browser von Haus aus. Ihr
Telefon betrifft das nicht (es merkt sich beim Koppeln genau dieses Zertifikat), aber der Browser
warnt jedes Mal. Um die Warnung loszuwerden, installieren Sie **einmal** das **Stammzertifikat** des
Hubs auf jedem Computer oder Telefon, mit dem Sie surfen.

### 6.1 Herunterladen

Öffnen Sie als Administrator **Einstellungen → Geräte**, Bereich **Browser-Vertrauen**, und drücken
Sie **Stammzertifikat herunterladen**. Sie erhalten eine Datei `synchub-ca.crt`.

Dieses Stammzertifikat kann nur für `synchub.local`, `localhost` und die Adressen Ihres Hubs bürgen
— für nichts anderes im Internet.

> **Keine Schaltfläche zum Herunterladen?** Der Bereich ist **nur für Administratoren** sichtbar.
> Wenn Sie Administrator sind und der Bereich meldet, dass der Hub kein Stammzertifikat besitzt,
> wurde Ihr Hub vor dieser Funktion installiert: Er behält sein altes Zertifikat und ersetzt es nie
> von sich aus. Der einzige Weg zu einem Stammzertifikat ist, das Zertifikat
> (`/data/keystore.p12`) zu löschen und neu zu starten. Dann **muss jedes gekoppelte Telefon das
> neue Zertifikat bestätigen** (Einstellungen → Geräte zeigt dafür einen QR-Code) oder neu gekoppelt
> werden. Bis dahin akzeptieren Sie weiter die Warnung des Browsers.

### 6.2 Installieren

**Windows** (Edge, Chrome)
1. Doppelklicken Sie auf `synchub-ca.crt` → **Zertifikat installieren…**
2. Wählen Sie **Aktueller Benutzer** → **Weiter**.
3. Wählen Sie **Alle Zertifikate in folgendem Speicher speichern** → **Durchsuchen…** →
   **Vertrauenswürdige Stammzertifizierungsstellen** → **OK** → **Weiter** → **Fertig stellen**.
4. Bestätigen Sie die Sicherheitswarnung mit **Ja**, schließen und öffnen Sie dann den Browser neu.

**macOS** (Safari, Chrome)
1. Doppelklicken Sie auf `synchub-ca.crt`: Die Schlüsselbundverwaltung öffnet sich und fügt es dem
   Schlüsselbund *Anmeldung* hinzu.
2. Doppelklicken Sie auf das Zertifikat *SyncHub Local CA* → **Vertrauen** → *Bei Verwendung dieses
   Zertifikats*: **Immer vertrauen**. Fenster schließen und Passwort eingeben.

**Android**
1. Öffnen Sie die **Einstellungen** des Telefons → **Sicherheit & Datenschutz** → **Weitere
   Sicherheitseinstellungen** → **Verschlüsselung & Anmeldedaten** → **Zertifikat installieren** →
   **CA-Zertifikat**.
2. Bestätigen Sie die Warnung und wählen Sie `synchub-ca.crt` aus Ihren Downloads.
3. Die Menünamen unterscheiden sich je nach Hersteller etwas; suchen Sie in den Einstellungen nach
   „Zertifikat".

**Linux** (Chrome, Chromium) — **Einstellungen → Datenschutz und Sicherheit → Sicherheit →
Zertifikate verwalten**, die Datei als vertrauenswürdige **Zertifizierungsstelle** importieren.

**Firefox** (alle Systeme) führt eine eigene Liste — **Einstellungen → Datenschutz & Sicherheit →
Zertifikate → Zertifikate anzeigen… → Zertifizierungsstellen → Importieren…**, dann **Dieser CA
vertrauen, um Websites zu identifizieren** ankreuzen.

Öffnen Sie anschließend `https://synchub.local:8443` erneut: Das Schloss ist da.

---

## 7. Mehrere Personen, ein Hub

- **Jedes Konto hat alles für sich**: Feeds, Gelesen-Markierungen, Orte, Watchlist, Notizen,
  Einstellungen. Zwischen Konten wird nichts geteilt, und keine Einstellung teilt es.
- Ein ganz neues Konto ist deshalb **leer** — das ist kein Datenverlust.
- Ein Administrator legt Konten an und löscht sie und kann für jemanden, der sein Passwort vergessen
  hat, ein neues setzen (**Einstellungen → Benutzer**), kann aber **niemals** die Daten einer anderen
  Person **lesen**.
- Rollen: Jedes Konto ist *Benutzer*; **admin** verwaltet den Hub; **updater** darf nur Updates
  einspielen.

---

## 8. Ihre Dateien

Jedes Konto hat einen privaten **Dateibereich**, erreichbar mit jedem WebDAV-Client (der
Dateimanager Ihres Computers kann das meist). Erzeugen Sie ein Token unter **Einstellungen → Konto**
und verbinden Sie Ihren Client mit `https://<Hub>:8443/files/`, mit Ihrem Kontonamen und diesem
Token — niemals mit Ihrem Passwort.

---

## 9. Zwei-Faktor-Anmeldung

Die Zwei-Faktor-Anmeldung ergänzt Ihr Passwort um einen sechsstelligen Code aus einer
Authenticator-App. Auf einem Hub, der zu Hause bleibt, ist sie optional; wenn Sie den Hub von außen
erreichen, ist sie **dringend empfohlen**.

**Bevor das erste Konto sie einschaltet**, braucht der Hub einen geheimen Schlüssel:

1. Erzeugen Sie einen: `openssl rand -base64 32`.
2. Tragen Sie ihn in `compose.yml` ein → `SYNCHUB_SECRET_KEY: "<der Schlüssel>"` (das `#`
   entfernen), dann `docker compose up -d`.
3. **Bewahren Sie eine Kopie dieses Schlüssels sicher auf und ändern Sie ihn nie.** Geht er
   verloren, muss jedes Konto mit Zwei-Faktor-Anmeldung von einem Administrator zurückgesetzt werden,
   und das Wiederherstellen einer Sicherung erfordert denselben Schlüssel.

Danach jede Person: **Einstellungen → Konto**, den QR-Code mit einer Authenticator-App scannen, mit
einem Code bestätigen und **die zehn Wiederherstellungscodes aufbewahren**, die nur einmal angezeigt
werden.

Solange der Schlüssel fehlt, meldet das Protokoll `SYNCHUB_SECRET_KEY is not set: two-factor
enrolment is refused until it is.` — harmlos, wenn Sie die Funktion nicht nutzen.

---

## 10. Aktualisieren

Der Hub prüft einmal täglich, ob es eine neue Version gibt, und zeigt es einem Administrator unter
**Einstellungen → Über** an, zusammen mit dem, was die neue Version von Ihnen verlangt (meist nichts).

### 10.1 Von Hand — drei Schritte

1. Setzen Sie in `.env` `SYNCHUB_TAG` auf die neue Version.
2. `docker compose pull`
3. `docker compose up -d`

Ohne Schritt 1 lädt der Pull die Version, die Sie schon haben.

### 10.2 Per Knopfdruck — der Launcher (optional)

Der Launcher ist ein zweiter, kleiner Container, der ein Update einspielt, wenn ein Administrator
unter **Einstellungen → Über** auf **Update einspielen** drückt, und der jedes Anhalten des Hubs samt
Grund festhält.

1. Setzen Sie in `.env` `SYNCHUB_PROJECT_DIR` auf den absoluten Pfad Ihres SyncHub-Ordners.
2. `docker compose --profile launcher up -d`

**Wissen Sie, was Sie erlauben**: Der Launcher hält den Socket der Container-Engine, was der vollen
Kontrolle über das Gerät entspricht. Vom Hub nimmt er keine Anweisung außer „los" entgegen und
installiert immer nur eine offizielle SyncHub-Version. Ist Ihnen das zu viel, aktualisieren Sie von
Hand.

---

## 11. Sicherungen

- **Täglich um 3:30 Uhr** speichert der Hub einen Snapshot seiner **Konfiguration** (Konten,
  gekoppelte Geräte, Tokens, Einstellungen). **Einstellungen → Sicherung** listet sie auf, erstellt
  einen auf Wunsch (**Jetzt einen Snapshot erstellen**), lädt sie herunter, nimmt hochgeladene an und
  stellt sie wieder her (**Wiederherstellen…**).
- Ihre **Daten** (Artikel, Notizen, Watchlists…) sind nicht im Snapshot: Sie liegen auch auf Ihren
  Telefonen und kommen von dort zurück.
- Standardmäßig liegen die Snapshots auf derselben Festplatte wie die Daten. Kopieren Sie sie mit dem
  Sicherungswerkzeug Ihres NAS woandershin — **richten Sie es auf den Snapshot-Ordner**, nicht auf die
  laufende Datenbank, die sich während des Betriebs nicht sicher kopieren lässt.
- Apps können auch eigene Sicherungen auf dem Hub ablegen: **Einstellungen → Sicherungen** listet
  Ihre auf.

Wiederherstellen auf einem neuen Gerät: Hub installieren, **denselben `SYNCHUB_SECRET_KEY`**
verwenden und im ersten Einrichtungsschritt *Snapshot wiederherstellen* wählen. Jedes Telefon
bestätigt danach einmal das neue Zertifikat.

---

## 12. Von unterwegs zugreifen

SyncHub öffnet von sich aus nie eine Tür zum Internet. Wenn Sie ihn unterwegs erreichen wollen,
nutzen Sie ein **VPN** in Ihr Heimnetz — der einfachste und sicherste Weg. Wenn Sie stattdessen einen
Reverse Proxy verwenden:

- fügen Sie die Adresse, die Ihr Telefon wählt, zu `SYNCHUB_ALLOWED_HOSTS` hinzu;
- schalten Sie vorher für jedes Konto die **Zwei-Faktor-Anmeldung** ein.

---

## 13. Das Startprotokoll lesen

`docker compose logs synchub` zeigt, was der Hub beim Start getan hat. Das Protokoll ist auf
Englisch. Was die üblichen Zeilen bedeuten:

| Zeile | Bedeutung | Was tun |
| --- | --- | --- |
| `SLF4J(W): No SLF4J providers were found` und `WARNING: A restricted method… sqlite-jdbc` | Meldungen von Bibliotheken im Hub. | Nichts. |
| `Applied migration V…` | Die Datenbank wurde für die neue Version aktualisiert. | Nichts. |
| `First run: admin account created.` + `Setup token…` | Der Hub ist auf einem **leeren** Datenvolume gestartet. | Bei der allerersten Installation: mit dem Token anmelden. **Nach einem Update: Ihr Datenvolume wurde nicht übernommen** — siehe [Abschnitt 14](#14-wenn-etwas-schiefgeht). |
| `SYNCHUB_SECRET_KEY is not set…` | Die Zwei-Faktor-Anmeldung ist nicht verfügbar. | Nichts, oder [Abschnitt 9](#9-zwei-faktor-anmeldung). |
| `Data directory: /data — docker volume "synchub-data"` | Wo Ihre Daten liegen. | Prüfen, dass nach jedem Update **dasselbe** Volume genannt wird. |
| `Allowed Host headers: [synchub.local, 192.168.1.20]` | Die Adressen, auf die der Hub antwortet. | Die Adresse, die Telefon und Browser verwenden, muss in der Liste stehen. |
| `TLS: adopted the existing keystore…` | Der Hub hat sein Zertifikat behalten. Bei jedem Start nach dem ersten normal. | Nichts. |
| `TLS keystore … is readable by group or others` | Die Datei mit dem privaten Schlüssel des Zertifikats ist für andere auf dem Gerät lesbar. | Einmal: `docker compose exec synchub chmod 600 /data/keystore.p12`, dann neu starten. Sonst ändert sich nichts. |
| `Serving https://192.168.1.20:8443` | Die Adresse zum Öffnen. Sie wird auch im Netz angekündigt, damit Telefone sie finden. | Nichts. Steht dort *not advertising*, nennt dieselbe Zeile den Grund. |
| `TLS handshake refused by 192.168.1.42 — the peer rejected this hub's certificate` | Das Gerät unter dieser Adresse hat das Zertifikat des Hubs abgelehnt. | Ist es ein **Computer**: Sein Browser vertraut dem Hub noch nicht, siehe [Abschnitt 6](#6-ein-schloss-im-browser). Ist es ein **gekoppeltes Telefon**: Sein Zertifikat ist veraltet, den QR-Code unter **Einstellungen → Geräte** scannen. |
| `RSS: N subscription(s) … scraped on the phone — not fetched here` | Feeds, die Ihr Telefon selbst liest und die der Hub auslässt. | Nichts. |
| `Stocks: N instrument(s) … with no symbol any role speaks` | Der Hub kann für diese Werte keine Kurse abrufen. | Die Adressen auf der Börsen-Einstellungsseite prüfen; bleibt es so, melden. |
| `sync: …` | Eine Zeile pro Synchronisierung mit einem Telefon. | Nützlich, um zu sehen, ob ein Telefon wirklich synchronisiert. |

---

## 14. Wenn etwas schiefgeht

**Der Browser zeigt nur *Bad Request*.** Die eingegebene Adresse steht nicht in
`SYNCHUB_ALLOWED_HOSTS`. Tragen Sie sie in `compose.yml` ein, dann `docker compose up -d`. Sobald
der Hub diesen Wert gespeichert hat, ändern Sie ihn stattdessen unter **Einstellungen → Einrichtung**.

**Nach einem Update zeigt das Protokoll ein neues Einrichtungs-Token und jedes Telefon will neu
gekoppelt werden.** Der Hub ist auf einem **leeren** Datenvolume gestartet: Ihre Daten wurden nicht
gelöscht, sie liegen in einem anderen Volume. Führen Sie `docker volume ls` aus und prüfen Sie, dass
`/data` auf `synchub-data` zeigt. Im Containerformular Ihres NAS darf die Volume-Zeile nie leer
bleiben.

**Führen Sie niemals `docker compose down -v` aus** (auch nicht `docker volume prune`): `-v`
**löscht** das Datenvolume — Datenbank, Zertifikat und alle Kopplungen. `docker compose up -d`,
`restart` und `down` ohne `-v` sind ungefährlich.

**Das Telefon meldet, dass sich das Zertifikat des Hubs seit dem Koppeln geändert hat.** Der Hub hat
ein neues Zertifikat. Öffnen Sie **Einstellungen → Geräte** und scannen Sie den dortigen QR-Code mit
der App: Das Telefon behält seine Kopplung und vertraut dem neuen Zertifikat. Hat der Hub auch seine
Daten verloren, koppeln Sie stattdessen neu mit **Gerät koppeln**.

**Das Telefon meldet, der Hub sei nicht erreichbar.** Prüfen Sie der Reihe nach: Der Hub läuft; das
Telefon ist im Heimnetz; die Adresse, die es verwendet, steht in `SYNCHUB_ALLOWED_HOSTS`
(Protokollzeile `Allowed Host headers`); öffnen Sie dieselbe `https://…`-Adresse im Browser des
Telefons.

**Ein Gerät ist unter Einstellungen → Geräte grün, aber nichts wird angezeigt.** Schauen Sie auf
*Synchronisiert*: *nie* bedeutet, dass noch keine Daten übertragen wurden. **Einstellungen →
Synchronisierung** zeigt Sammlung für Sammlung, was der Hub für Ihr Konto hält.

**`https://synchub.local:8443` öffnet sich auf einem Android-Telefon nicht.** Android-Browser lösen
`.local`-Namen nicht auf. Verwenden Sie die Adresse (`https://192.168.1.20:8443`). Die App ist nicht
betroffen: Sie findet den Hub auf anderem Weg.

---

*Fragen: Eröffnen Sie ein Issue in diesem Repository. Datenschutzerklärungen der Apps:
[`privacy/`](../../privacy/).*
