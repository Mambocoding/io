# SyncHub — gebruikershandleiding

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · Nederlands*

Geschreven voor SyncHub 0.2.216 (oktober 2026). Als deze handleiding en de pagina's van de hub iets
anders zeggen, heeft de hub gelijk.

---

## 1. Wat SyncHub is

SyncHub is een kleine server die u **op uw eigen apparaat** draait — meestal een NAS thuis — zodat de
gegevens van uw apps bij u blijven in plaats van in de cloud van een ander.

- Hij bewaart de gegevens van meerdere apps (feeds, weer, beurs, notities) voor **meerdere
  personen**; elk account staat volledig los van de andere.
- Hij **haalt uw inhoud dag en nacht op**, zodat een telefoon die uit stond niets mist.
- Hij biedt een **webinterface** in uw browser met dezelfde inhoud als uw telefoon.
- Hij **synchroniseert in beide richtingen**: wat u in de browser een ster geeft of als gelezen
  markeert, verschijnt op de telefoon, en omgekeerd.

Hij is **optioneel**: een app zonder ingestelde hub werkt precies zoals voorheen.

Hij **stelt zich nooit open voor internet**. Hij antwoordt alleen op uw thuisnetwerk. Hem van buitenaf
bereiken is uw eigen keuze, via een VPN of uw eigen reverse proxy (zie
[hoofdstuk 12](#12-van-buitenshuis-bereiken)).

---

## 2. Wat u nodig hebt

- Een apparaat dat altijd aan staat en **containers** draait (een NAS met containerbeheer, een kleine
  Linux-server, een mini-pc). `amd64` en `arm64` worden ondersteund.
- Ongeveer **300 MB vrij geheugen** en enkele honderden MB schijfruimte, plus wat uw bestanden en
  bijlagen innemen.
- **Hostnetwerk** (`network_mode: host`, Linux) voor de container. Zonder werkt alles, behalve dat uw
  telefoon de hub niet zelf vindt: u typt dan zijn adres.
- Het **adres van het apparaat op uw thuisnetwerk**, bijvoorbeeld `192.168.1.20`. De lijst met
  verbonden apparaten van uw router toont het. Laat de router dat apparaat bij voorkeur altijd
  hetzelfde adres geven.

---

## 3. Installeren

### 3.1 Een map en twee bestanden aanmaken

Maak op het apparaat een map voor SyncHub aan (bijvoorbeeld `/volume1/docker/synchub` of
`~/synchub`) en zet deze twee bestanden erin.

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
      # Het adres van uw apparaat op het thuisnetwerk, na synchub.local. Verplicht.
      SYNCHUB_ALLOWED_HOSTS: "synchub.local,192.168.XXX.XXX"
      SYNCHUB_TLS_KEYSTORE_PASSWORD: "${SYNCHUB_TLS_KEYSTORE_PASSWORD:?set it in the .env beside this file}"
      # Uw tijdzone, zodat datums en tijden op de webpagina's kloppen.
      TZ: "Europe/Amsterdam"
      # Optioneel, nodig voor aanmelden in twee stappen (hoofdstuk 9).
      # SYNCHUB_SECRET_KEY: ""

  # Optioneel: de launcher, die een knop "Update toepassen" toevoegt (hoofdstuk 10.2).
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

**`.env`** (de naam begint met een punt)

```sh
# De SyncHub-versie die moet draaien: drie getallen, nooit "latest".
SYNCHUB_TAG=

# Een wachtwoord dat het certificaat van de hub beschermt. Kies het nu en wijzig het nooit.
SYNCHUB_TLS_KEYSTORE_PASSWORD=

# Alleen voor de optionele launcher (hoofdstuk 10.2): het absolute pad van deze map.
SYNCHUB_LAUNCHER_TAG=latest
SYNCHUB_PROJECT_DIR=
```

### 3.2 Vier waarden invullen

| Waar | Wat invullen |
| --- | --- |
| `.env` → `SYNCHUB_TAG` | De huidige versie. Die wordt gepubliceerd op <https://raw.githubusercontent.com/Mambocoding/io/main/synchub/latest.json> (veld `version`), bijvoorbeeld `0.2.216`. |
| `.env` → `SYNCHUB_TLS_KEYSTORE_PASSWORD` | Een lang, willekeurig wachtwoord. Bewaar een kopie: raakt het kwijt, dan kan de hub zijn certificaat niet meer openen en moet elke telefoon opnieuw gekoppeld worden. |
| `compose.yml` → `SYNCHUB_ALLOWED_HOSTS` | Vervang `192.168.XXX.XXX` door het adres van uw apparaat. De hub weigert elk verzoek aan een adres dat niet in deze lijst staat, met een kaal *Bad Request*. |
| `compose.yml` → `TZ` | Uw tijdzone (`Europe/Amsterdam`, `Europe/Brussels`…). |

Houd `compose.yml` en `.env` **samen** in dezelfde map: het eerste start niet zonder het tweede.

### 3.3 Starten

In die map:

```sh
docker compose up -d
docker compose logs synchub
```

Om het image te downloaden zijn geen account en geen wachtwoord nodig. Veel containerbeheerders van
NAS-apparaten kunnen een `compose.yml` ook als "project" importeren; het resultaat is hetzelfde.

Zoek in het logboek naar deze regels:

```
First run: admin account created.
Setup token (use as the admin password): ...
Serving https://192.168.1.20:8443
TLS certificate SHA-256 fingerprint: A1:B2:...
```

Kopieer het **installatietoken** (*setup token*): het is het eerste wachtwoord van het
beheerdersaccount.

---

## 4. Eerste keer aanmelden

1. Open in een browser op uw thuisnetwerk **`https://synchub.local:8443`** of
   **`https://<adres van uw apparaat>:8443`**.
2. De browser waarschuwt dat de verbinding niet vertrouwd is. De eerste keer is dat normaal;
   accepteer de waarschuwing om verder te gaan. [Hoofdstuk 6](#6-een-slotje-in-de-browser) haalt de
   waarschuwing voorgoed weg.
3. Meld u aan als `admin` met het installatietoken als wachtwoord.
4. Een **installatiewizard** opent: die leidt u door het koppelen van een telefoon, aanmelden in twee
   stappen, het adres dat uw telefoons gebruiken en de netwerkinstellingen. U komt er altijd weer bij
   via **Instellingen → Installatie**.
5. Wijzig het beheerderswachtwoord: **Instellingen → Account → Wachtwoord wijzigen** (minstens
   12 tekens).

**Zet de apps aan die u gebruikt** in **Instellingen → Apps** (alleen beheerders). Elke app gaat
meteen aan of uit, zonder herstart.

---

## 5. Een telefoon koppelen

1. Open in de app op uw telefoon de hub-instellingen. De app **vindt de hub zelf** op uw netwerk en
   biedt *SyncHub op 192.168.1.20* aan. Zo niet, typ dan `https://<adres>:8443`.
2. Open in de browser **Instellingen → Apparaten → Apparaat koppelen**. Er verschijnt een
   **QR-code**, met daaronder een code, het adres en de vingerafdruk van het certificaat.
3. **Scan de QR-code** met de app. Scannen is beter dan overtypen: de app controleert de vingerafdruk
   van het certificaat dan exact, teken voor teken.
4. De code is **vijf minuten** en **één keer** geldig. Is hij verlopen, druk dan opnieuw op
   *Apparaat koppelen*.

De telefoon hoort bij het account dat de code heeft aangemaakt. Elke app (feeds, weer, beurs,
notities) wordt apart gekoppeld en staat op een eigen regel onder **Instellingen → Apparaten**.

**Kijk naar de kolom *Gesynchroniseerd***, niet naar *Laatst gezien*: *Laatst gezien* zegt alleen dat
de telefoon heeft aangeklopt; *Gesynchroniseerd* zegt dat er echt gegevens zijn overgegaan. *nooit*
betekent dat de eerste echte synchronisatie van de telefoon nog moet plaatsvinden.

---

## 6. Een slotje in de browser

Het certificaat van de hub wordt door de hub zelf gemaakt, dus geen enkele browser vertrouwt het
vanzelf. Uw telefoon heeft daar geen last van (die onthoudt bij het koppelen precies dit
certificaat), maar de browser waarschuwt elke keer. Om de waarschuwing weg te halen, installeert u
**één keer** het **basiscertificaat** van de hub op elke computer of telefoon waarmee u surft.

### 6.1 Downloaden

Open als beheerder **Instellingen → Apparaten**, onderdeel **Vertrouwen van de browser**, en druk op
**Basiscertificaat downloaden**. U krijgt een bestand `synchub-ca.crt`.

Dit basiscertificaat kan alleen instaan voor `synchub.local`, `localhost` en de adressen van uw hub —
voor niets anders op internet.

> **Geen downloadknop?** Het onderdeel is **alleen voor beheerders** zichtbaar. Bent u beheerder en
> meldt het onderdeel dat de hub geen basiscertificaat heeft, dan is uw hub geïnstalleerd vóór deze
> functie: hij houdt zijn oude certificaat en vervangt het nooit uit zichzelf. De enige manier om een
> basiscertificaat te krijgen is het certificaat (`/data/keystore.p12`) te verwijderen en opnieuw te
> starten. Dan **moet elke gekoppelde telefoon het nieuwe certificaat bevestigen** (Instellingen →
> Apparaten toont daarvoor een QR-code) of opnieuw gekoppeld worden. Tot die tijd blijft u de
> waarschuwing van de browser accepteren.

### 6.2 Installeren

**Windows** (Edge, Chrome)
1. Dubbelklik op `synchub-ca.crt` → **Certificaat installeren…**
2. Kies **Huidige gebruiker** → **Volgende**.
3. Kies **Alle certificaten in het onderstaande archief opslaan** → **Bladeren…** →
   **Vertrouwde basiscertificeringsinstanties** → **OK** → **Volgende** → **Voltooien**.
4. Bevestig de beveiligingswaarschuwing met **Ja** en sluit en open daarna de browser opnieuw.

**macOS** (Safari, Chrome)
1. Dubbelklik op `synchub-ca.crt`: Sleutelhangertoegang opent en voegt het toe aan de sleutelhanger
   *inlogsessie*.
2. Dubbelklik op het certificaat *SyncHub Local CA* → **Vertrouw** → *Bij gebruik van dit
   certificaat*: **Altijd vertrouwen**. Sluit het venster en voer uw wachtwoord in.

**Android**
1. Open de **Instellingen** van de telefoon → **Beveiliging en privacy** → **Meer
   beveiligingsinstellingen** → **Versleuteling en inloggegevens** → **Een certificaat installeren** →
   **CA-certificaat**.
2. Bevestig de waarschuwing en kies `synchub-ca.crt` uit uw downloads.
3. De menunamen verschillen iets per fabrikant; zoek in de instellingen naar "certificaat".

**Linux** (Chrome, Chromium) — **Instellingen → Privacy en beveiliging → Beveiliging → Certificaten
beheren**, importeer het bestand als vertrouwde **certificeringsinstantie**.

**Firefox** (alle systemen) houdt een eigen lijst bij — **Instellingen → Privacy & Beveiliging →
Certificaten → Certificaten bekijken… → Organisaties → Importeren…**, vink daarna **Deze CA
vertrouwen voor het identificeren van websites** aan.

Open daarna `https://synchub.local:8443` opnieuw: het slotje is er.

---

## 7. Meerdere personen, één hub

- **Elk account heeft alles voor zich**: feeds, leesmarkeringen, plaatsen, volglijst, notities,
  instellingen. Tussen accounts wordt niets gedeeld, en geen instelling deelt het.
- Een gloednieuw account is daarom **leeg** — dat is geen gegevensverlies.
- Een beheerder maakt accounts aan en verwijdert ze, en kan een nieuw wachtwoord instellen voor wie
  het zijne vergeten is (**Instellingen → Gebruikers**), maar **kan nooit** de gegevens van een ander
  **lezen**.
- Rollen: elk account is *gebruiker*; **admin** beheert de hub; **updater** mag alleen updates
  toepassen.

---

## 8. Uw bestanden

Elk account heeft een privé **bestandsruimte**, bereikbaar met elke WebDAV-client (de bestandsbeheerder
van uw computer kan dat meestal). Maak een token aan in **Instellingen → Account** en verbind uw
client met `https://<hub>:8443/files/`, met uw accountnaam en dat token — nooit uw wachtwoord.

---

## 9. Aanmelden in twee stappen

Aanmelden in twee stappen voegt aan uw wachtwoord een zescijferige code uit een authenticator-app
toe. Op een hub die thuis blijft is het optioneel; als u de hub van buitenaf bereikt, is het **sterk
aanbevolen**.

**Voordat het eerste account het aanzet**, heeft de hub een geheime sleutel nodig:

1. Maak er een aan: `openssl rand -base64 32`.
2. Zet hem in `compose.yml` → `SYNCHUB_SECRET_KEY: "<de sleutel>"` (haal het `#` weg), daarna
   `docker compose up -d`.
3. **Bewaar een kopie van die sleutel op een veilige plek en wijzig hem nooit.** Raakt hij kwijt, dan
   moet elk account met aanmelden in twee stappen door een beheerder worden gereset, en voor het
   terugzetten van een back-up is dezelfde sleutel nodig.

Daarna doet ieder: **Instellingen → Account**, scant de QR-code met een authenticator-app, bevestigt
met een code en **bewaart de tien herstelcodes** die één keer worden getoond.

Zolang de sleutel ontbreekt, meldt het logboek `SYNCHUB_SECRET_KEY is not set: two-factor enrolment
is refused until it is.` — onschuldig als u de functie niet gebruikt.

---

## 10. Bijwerken

De hub controleert één keer per dag of er een nieuwe versie is en meldt dat een beheerder onder
**Instellingen → Over**, samen met wat de nieuwe versie van u vraagt (meestal niets).

### 10.1 Met de hand — drie stappen

1. Zet in `.env` `SYNCHUB_TAG` op de nieuwe versie.
2. `docker compose pull`
3. `docker compose up -d`

Zonder stap 1 haalt de pull de versie op die u al hebt.

### 10.2 Met een knop — de launcher (optioneel)

De launcher is een tweede, kleine container die een update toepast wanneer een beheerder onder
**Instellingen → Over** op **Update toepassen** drukt, en die elke keer bijhoudt dat de hub stopte en
waarom.

1. Zet in `.env` `SYNCHUB_PROJECT_DIR` op het absolute pad van uw SyncHub-map.
2. `docker compose --profile launcher up -d`

**Weet wat u toestaat**: de launcher houdt de socket van de container-engine vast, wat neerkomt op
volledige controle over het apparaat. Hij neemt van de hub geen andere opdracht aan dan "ga" en
installeert alleen ooit een officiële SyncHub-versie. Is dat u te veel, werk dan met de hand bij.

---

## 11. Back-ups

- **Elke dag om 3:30 uur** bewaart de hub een momentopname van zijn **configuratie** (accounts,
  gekoppelde apparaten, tokens, instellingen). **Instellingen → Back-up** toont ze, maakt er een op
  verzoek (**Nu een momentopname maken**), downloadt ze, neemt geüploade aan en zet ze terug
  (**Herstellen…**).
- Uw **gegevens** (artikelen, notities, volglijsten…) zitten niet in een momentopname: die staan ook
  op uw telefoons en komen daarvandaan terug.
- Standaard staan de momentopnamen op dezelfde schijf als de gegevens. Kopieer ze elders met het
  back-upprogramma van uw NAS — **richt het op de map met momentopnamen**, niet op de draaiende
  database, die niet veilig gekopieerd kan worden terwijl de hub loopt.
- Apps kunnen ook hun eigen back-ups op de hub zetten: **Instellingen → Back-ups** toont de uwe.

Terugzetten op een nieuw apparaat: installeer de hub, gebruik **dezelfde `SYNCHUB_SECRET_KEY`** en
kies *Een momentopname herstellen* bij de eerste installatiestap. Elke telefoon bevestigt daarna één
keer het nieuwe certificaat.

---

## 12. Van buitenshuis bereiken

SyncHub opent uit zichzelf nooit een deur naar internet. Wilt u hem buitenshuis bereiken, gebruik dan
een **VPN** naar uw thuisnetwerk — de eenvoudigste en veiligste manier. Gebruikt u in plaats daarvan
een reverse proxy:

- voeg het adres dat uw telefoon kiest toe aan `SYNCHUB_ALLOWED_HOSTS`;
- zet eerst voor elk account **aanmelden in twee stappen** aan.

---

## 13. Het opstartlogboek lezen

`docker compose logs synchub` toont wat de hub bij het opstarten deed. Het logboek is in het Engels.
Wat de gebruikelijke regels betekenen:

| Regel | Betekenis | Wat te doen |
| --- | --- | --- |
| `SLF4J(W): No SLF4J providers were found` en `WARNING: A restricted method… sqlite-jdbc` | Meldingen van bibliotheken in de hub. | Niets. |
| `Applied migration V…` | De database is bijgewerkt voor de nieuwe versie. | Niets. |
| `First run: admin account created.` + `Setup token…` | De hub is gestart op een **leeg** gegevensvolume. | Bij de allereerste installatie: aanmelden met het token. **Na een update: uw gegevensvolume is niet behouden** — zie [hoofdstuk 14](#14-als-er-iets-misgaat). |
| `SYNCHUB_SECRET_KEY is not set…` | Aanmelden in twee stappen is niet beschikbaar. | Niets, of [hoofdstuk 9](#9-aanmelden-in-twee-stappen). |
| `Data directory: /data — docker volume "synchub-data"` | Waar uw gegevens staan. | Controleer dat na elke update **hetzelfde** volume wordt genoemd. |
| `Allowed Host headers: [synchub.local, 192.168.1.20]` | De adressen waarop de hub antwoordt. | Het adres dat telefoon en browser gebruiken, moet in de lijst staan. |
| `TLS: adopted the existing keystore…` | De hub heeft zijn certificaat behouden. Normaal bij elke start na de eerste. | Niets. |
| `TLS keystore … is readable by group or others` | Het bestand met de privésleutel van het certificaat is leesbaar voor anderen op het apparaat. | Eén keer: `docker compose exec synchub chmod 600 /data/keystore.p12`, daarna herstarten. Verder verandert er niets. |
| `Serving https://192.168.1.20:8443` | Het adres om te openen. Het wordt ook op uw netwerk aangekondigd, zodat telefoons het vinden. | Niets. Staat er *not advertising*, dan zegt dezelfde regel waarom. |
| `TLS handshake refused by 192.168.1.42 — the peer rejected this hub's certificate` | Het apparaat op dat adres heeft het certificaat van de hub geweigerd. | Is het een **computer**: de browser vertrouwt de hub nog niet, zie [hoofdstuk 6](#6-een-slotje-in-de-browser). Is het een **gekoppelde telefoon**: het certificaat is verouderd, scan de QR-code onder **Instellingen → Apparaten**. |
| `RSS: N subscription(s) … scraped on the phone — not fetched here` | Feeds die uw telefoon zelf leest en die de hub overslaat. | Niets. |
| `Stocks: N instrument(s) … with no symbol any role speaks` | De hub kan voor deze fondsen geen koersen ophalen. | Controleer de adressen op de beursinstellingenpagina; blijft het zo, meld het dan. |
| `sync: …` | Eén regel per synchronisatie met een telefoon. | Handig om te zien of een telefoon echt synchroniseert. |

---

## 14. Als er iets misgaat

**De browser toont alleen *Bad Request*.** Het getypte adres staat niet in `SYNCHUB_ALLOWED_HOSTS`.
Voeg het toe in `compose.yml` en daarna `docker compose up -d`. Zodra de hub deze waarde heeft
opgeslagen, wijzigt u haar voortaan via **Instellingen → Installatie**.

**Na een update toont het logboek een nieuw installatietoken en wil elke telefoon opnieuw gekoppeld
worden.** De hub is gestart op een **leeg** gegevensvolume: uw gegevens zijn niet gewist, ze staan in
een ander volume. Voer `docker volume ls` uit en controleer dat `/data` naar `synchub-data` wijst. In
het containerformulier van uw NAS mag de volumeregel nooit leeg blijven.

**Voer nooit `docker compose down -v` uit** (en ook niet `docker volume prune`): `-v` **verwijdert**
het gegevensvolume — database, certificaat en alle koppelingen. `docker compose up -d`, `restart` en
`down` zonder `-v` zijn veilig.

**De telefoon meldt dat het certificaat van de hub is veranderd sinds het koppelen.** De hub heeft een
nieuw certificaat. Open **Instellingen → Apparaten** en scan de QR-code daar met de app: de telefoon
houdt zijn koppeling en vertrouwt het nieuwe certificaat. Is de hub ook zijn gegevens kwijt, koppel
dan opnieuw met **Apparaat koppelen**.

**De telefoon meldt dat de hub onbereikbaar is.** Controleer op volgorde: de hub draait; de telefoon
zit op het thuisnetwerk; het adres dat hij gebruikt staat in `SYNCHUB_ALLOWED_HOSTS` (logregel
`Allowed Host headers`); open hetzelfde `https://…`-adres in de browser van de telefoon.

**Een apparaat is groen onder Instellingen → Apparaten, maar er verschijnt niets.** Kijk naar
*Gesynchroniseerd*: *nooit* betekent dat er nog geen gegevens zijn overgegaan. **Instellingen →
Synchronisatie** toont per verzameling wat de hub voor uw account bewaart.

**`https://synchub.local:8443` opent niet op een Android-telefoon.** Android-browsers zetten
`.local`-namen niet om. Gebruik het adres (`https://192.168.1.20:8443`). De app heeft er geen last
van: die vindt de hub op een andere manier.

---

*Vragen: open een issue in deze repository. Privacybeleid van de apps: [`privacy/`](../../privacy/).*
