# Bestandsbeheer — handleiding

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · Nederlands*

Geschreven voor Bestandsbeheer 1.2.329 (oktober 2026). Waar deze handleiding en de app iets anders
zeggen, heeft de app gelijk.

---

## 1. Wat Bestandsbeheer is

Bestandsbeheer is een bestandsverkenner voor je telefoon en je tv. Het bladert door de opslag van de
telefoon, een SD-kaart of een USB-stick en de servers in je thuisnetwerk, en het kopieert, back-upt
en synchroniseert mappen tussen al die plekken.

- Alles blijft op je eigen apparaten: geen account, geen cloud van ons.
- De basis is gratis en zonder reclame. Sommige functies horen bij premium; ze dragen een gouden
  sterretje (zie [hoofdstuk 13](#13-gratis-en-premium)).
- Op een tv bladert dezelfde app door dezelfde plekken met de afstandsbediening.

---

## 2. De eerste keer

1. Een korte wizard vraagt je de gebruiksvoorwaarden te aanvaarden en laat je dan de **app-modus** en
   een thema kiezen. De modus pas je later aan in [Instellingen](app:settings) → *Interface*:
   - **Bestandsbeheer** (standaard) opent bij je bestanden;
   - **Fotoviewer** opent bij je foto's, als galerij.
2. Daarna vraagt Android toegang tot je bestanden. Kies **Toegang verlenen** om de hele opslag te
   doorbladeren, of **Kies in plaats daarvan een map** om maar één map te openen.
3. De eerste keer dat je een verbinding met je thuisnetwerk opent, kan Android om **toegang tot het
   lokale netwerk** vragen. Sta die toe: zonder die toegang loopt elke verbinding met je netwerk vast
   op een time-out. Je kunt hem later aanzetten in de machtigingen van de app.

---

## 3. Bladeren

- Het **pad** bovenaan is een rij chips: tik op een chip om terug te gaan naar die map. De map die je
  net verliet blijft als vervaagde chip staan, zodat je weer vooruit kunt.
- **Weergaven:** gedetailleerde lijst, raster of groot raster, via het menu ⋮, of knijp in de lijst.
- **Sorteren:** op naam, datum, grootte of type, oplopend of aflopend; mappen kunnen bovenaan
  blijven.
- **Zoeken:** tik op het vergrootglas; de resultaten vervangen de lijst zodra je typt. Er wordt
  gezocht in de huidige map en daaronder; een pictogram in de zoekbalk breidt het uit naar het hele
  apparaat.
- **Recent:** het klokpictogram op de rij *Interne opslag* van het menu toont de bestanden die je
  onlangs opende (7 of 30 dagen). *Recente geschiedenis wissen* vergeet de eigen lijst van de app.
- **Laatste locatie onthouden** (standaard aan) opent opnieuw de laatst bezochte map.
- **Gesplitst scherm:** op een breed scherm (een tablet, of een telefoon liggend) staan twee panelen
  naast elkaar, zodat je van het ene naar het andere kopieert. Uit te zetten via *Instellingen →
  Interface*.

### 3.1 Favorieten

Bovenaan de interne opslag leiden tegels naar **Foto's**, **Muziek** en **Downloads**. Tik op
**+ Toevoegen** om een map vast te zetten; lang drukken op een tegel haalt hem weg (alleen de
snelkoppeling, nooit de map). Elke verbinding en elke SD-kaart heeft eigen favorieten. Het paneel
klapt in met zijn pijl, of verdwijnt via *Instellingen → Interface → Favorietenpaneel tonen*.

---

## 4. Werken met bestanden

- **Selecteer** met lang drukken en tik daarna op meer bestanden; *Alles selecteren* staat in de
  actiebalk.
- De **actiebalk** (de zwevende pil) bevat wat je met de selectie kunt doen: kopiëren, verplaatsen,
  hernoemen, verwijderen, delen, comprimeren… De positie (zwevend, boven of onder) en de knoppen
  stel je in via *Instellingen → Interface → Actiebalk*.
- **Kopiëren en verplaatsen:** na *Kopiëren* of *Verplaatsen* ga je naar de bestemming en plak je.
  Bestaat een naam al, dan vraagt de app het voordat er iets verplaatst: **Vervangen** of
  **Dupliceren** (`naam (1)`), met *Voor alle conflicten* om maar één keer te antwoorden.
- Plakken van meer dan drie bestanden gaat op de achtergrond verder, met de voortgang in een melding
  en in **Gereedschap → Overdrachten**.
- **Verwijderen:** op de interne opslag gaat een verwijderd bestand eerst naar de **Prullenbak**
  ([hoofdstuk 10](#10-ruimte-vrijmaken-en-de-prullenbak)). Op een netwerkshare of een SD-kaart die
  via de kiezer van Android is geopend, is verwijderen definitief, en de bevestiging zegt dat.
- **Eigenschappen** tonen grootte, datums en locatie; voor een selectie de totale grootte.
- **Zip:** open een `.zip` om erin te bladeren, pak hem uit, of comprimeer een selectie tot een nieuw
  archief.
- **Teksteditor:** tekstbestanden openen in een ingebouwde editor met zoeken en vervangen.

---

## 5. Foto's, documenten en media

- **Fotoviewer:** veeg naar de volgende of vorige foto, knijp of dubbeltik om te zoomen. De titel
  toont wanneer de foto is genomen. Eén tik verbergt of toont de balken.
- De pil van de viewer bevat **Delen · Bewerken · Details · Gebruiken als… · Diavoorstelling ·
  Afdrukken · Verwijderen**. Na verwijderen schuift de volgende foto op zijn plaats.
- **Foto-editor:** bijsnijden, draaien, spiegelen en rechtzetten zijn gratis; formaat wijzigen,
  kleuren, filters, aantekeningen, uitknippen en gummen zijn premium.
- **PDF:** PDF-bestanden openen in de app, met zoeken en naar een pagina springen. Bestandsbeheer kan
  ook de PDF-lezer van de telefoon worden.
- **Speler:** muziek en video's spelen in de app, ook rechtstreeks vanaf een netwerkshare.
- Een bestand op een verbinding opent rechtstreeks in de app; een andere app krijgt een tijdelijke
  kopie.

---

## 6. Netwerkverbindingen

Bestandsbeheer bereikt de servers in je thuisnetwerk alsof het mappen op de telefoon zijn.

1. Open het menu en dan **Verbindingen → Verbinding toevoegen**.
2. Kies het type: **SMB** (gedeelde mappen van een computer en de meeste NAS'en, gratis), **FTP/FTPS**, **SFTP**,
   **WebDAV** of **S3** (premium).
3. Vul het adres van de server, je gebruikersnaam en wachtwoord in, en eventueel een startmap. Het
   wachtwoord wordt versleuteld op de telefoon bewaard.
4. De verbinding verschijnt in het menu met haar vrije ruimte. Tik erop om te bladeren.

De eerste keer dat een server een certificaat toont dat de app nog niet kent, vraagt ze of je het
vertrouwt; daarna wordt een ander certificaat geweigerd.

### 6.1 De bestandsruimte van je SyncHub

Als je thuis een SyncHub draait, is zijn bestandsruimte een **WebDAV**-verbinding: het adres van de
hub, je accountnaam als gebruikersnaam en het app-token van de hub als wachtwoord.

---

## 7. Mapsynchronisatie

**Taken** kopiëren mappen van de ene plek naar de andere, keer op keer, met één tik of volgens een
schema.

1. Open **Taken** in het menu en maak een taak. De wizard vraagt:
   - **Welk soort synchronisatie?** **Back-up** (kopieert nieuwe en gewijzigde bestanden; er wordt
     niets verwijderd), **Spiegelen** (maakt het doel een exacte kopie), **Verplaatsen**,
     **Downloaden** of **Tweerichting**;
   - de **bron**- en de **doel**map, op de telefoon of op een verbinding;
   - de opties: filters, wat te doen bij een conflict, meldingen en of de taak automatisch loopt.
2. Start hem met de afspeelknop, in de takenlijst of in het menu. **Alle taken uitvoeren** onderaan
   de lijst voert ze na elkaar uit.
3. De pagina van een taak toont de voortgang, het laatste resultaat en de geschiedenis; hij kan
   gepauzeerd, gestopt, bewerkt of uitgeschakeld worden.

Gratis: een handmatige **back-up** naar de telefoon of een SMB-share — ook rechtstreeks vanuit de
verkenner met *Back-up naar netwerk…*. Premium: de andere soorten, schema's, live synchronisatie en
de geavanceerde opties.

Een automatische taak loopt elke 1, 3, 6, 12 of 24 uur, alleen via wifi tenzij je mobiele data
toestaat, en eventueel alleen tijdens het opladen.

---

## 8. Bestanden naar een apparaat in de buurt sturen

**Naar apparaat sturen** wisselt bestanden uit met telefoons en computers op hetzelfde wifi, zonder
kabel of cloud.

- Om te **ontvangen** open je *Naar apparaat sturen* en zet je **Mij zichtbaar maken** aan. Je blijft
  alleen zichtbaar zolang dit scherm open is.
- Een binnenkomend aanbod vraagt altijd eerst: **Accepteren**, **Weigeren** of **Blokkeren**, en waar
  het moet worden opgeslagen. Er komt niets binnen voordat je accepteert.
- Om te **versturen** kies je een apparaat in de lijst en dan de bestanden; of gebruik *Delen* in een
  andere app en kies *Delen met apparaat*.
- Een apparaat dat niet gevonden wordt, voeg je toe via zijn adres of door zijn QR-code te scannen.

Overdrachten op hetzelfde wifi zijn niet versleuteld: gebruik het thuis, niet op een openbaar
netwerk.

---

## 9. Dit apparaat delen (premium)

Een computer op hetzelfde wifi bladert door de bestanden van de telefoon in zijn webbrowser en
downloadt ze, zonder iets te installeren.

1. **Verbindingen → Dit apparaat delen**, kies de gedeelde map en beslis of de browser ook mag
   uploaden en verwijderen (*Uploaden en verwijderen vanuit de browser toestaan*, standaard uit).
2. **Delen starten:** het scherm toont een adres, een QR-code en een pincode van zes cijfers.
3. Open het adres op de computer en typ de pincode.

Delen stopt met *Delen stoppen*, of vanzelf na 30 minuten zonder gebruik. Na vijf foute pincodes
antwoordt het niet meer. De verbinding is niet versleuteld, en het scherm zegt dat: gebruik het
alleen thuis.

---

## 10. Ruimte vrijmaken en de Prullenbak

- **Gereedschap → Ruimte vrijmaken** deelt grote en oude bestanden in categorieën in. Er is niets
  vooraf geselecteerd: je bekijkt elk bestand en kiest dan **Naar prullenbak**.
- **Gereedschap → Prullenbak** toont wat van de interne opslag is verwijderd. **Herstellen** zet een
  bestand terug op zijn plaats; **Prullenbak legen** verwijdert alles definitief.
- In *Instellingen → Prullenbak* kies je of verwijderen via de Prullenbak gaat of meteen verwijdert,
  en hoe lang de Prullenbak bestanden bewaart (tot hij geleegd wordt, of 5, 15, 30 of 90 dagen).

---

## 11. Privacy: app-vergrendeling en kluis

- **App-vergrendeling** (gratis, *Instellingen → Privacy*): Bestandsbeheer vraagt bij het openen je
  vingerafdruk, gezicht of schermvergrendeling, en na een vertraging die je kiest als je de app
  verlaat. De inhoud is verborgen in het overzicht van recente apps.
- **Kluis** (premium): een privé, versleutelde ruimte. Bestanden die je erheen verplaatst
  (*Naar kluis verplaatsen*) worden op de telefoon versleuteld en verborgen voor de galerij en andere
  apps. De kluis opent met je schermvergrendeling.
  - Bij het aanmaken toont de app een **herstelcode**. Schrijf hem op en bewaar hem ver van de
    telefoon: het is de enige weg terug als de schermvergrendeling wordt verwijderd, de telefoon
    wordt gereset of je van telefoon wisselt. Niemand kan hem voor je resetten; zonder hem zijn de
    bestanden in de kluis voorgoed verloren.
  - *Een kopie buiten opslaan* schrijft een ontsleutelde kopie van een bestand buiten de kluis.

---

## 12. Een back-up van de app

*Instellingen → Back-up & herstel* bewaart de app zelf — verbindingen, taken, favorieten, thema's en
instellingen — in één versleuteld bestand, beschermd met een wachtzin die je zelf kiest, en zet die
terug op een nieuwe telefoon.

- **Automatische back-up** maakt dat bestand elke dag vanzelf.
- Als je een SyncHub hebt, kan de back-up ook **op de hub** worden bewaard: koppel de app eraan via
  het back-upscherm. Die koppeling opent de back-ups van Bestandsbeheer en verder niets.

Je bestanden zelf zitten niet in deze back-up: kopieer ze met een taak
([hoofdstuk 7](#7-mapsynchronisatie)).

---

## 13. Gratis en premium

Gratis, voorgoed: bladeren, bestandsbewerkingen, favorieten, galerij, viewers en speler, de
Prullenbak en *Ruimte vrijmaken*, zip, SMB-verbindingen, handmatige back-up naar SMB of de telefoon,
*Naar apparaat sturen*, de app-vergrendeling en de automatische back-up van de app.

Premium: de andere verbindingstypen (FTP/FTPS, SFTP, WebDAV, S3), elke synchronisatie die verder gaat
dan een handmatige back-up, schema's en live synchronisatie, de geavanceerde gereedschappen van de
foto-editor, verwerkingsprofielen, de kluis en *Dit apparaat delen*.

Een premiumfunctie is overal zichtbaar met een gouden sterretje; erop tikken opent het
premiumscherm. Een taak met een premiumoptie wordt overgeslagen, nooit half uitgevoerd.

---

## 14. Als er iets misgaat

- Foutmeldingen zeggen in gewone woorden wat er gebeurde. **Details** onder een melding toont de
  technische oorzaak, die je in een feedbackmail kunt kopiëren (*Instellingen → Over → Feedback
  sturen*).
- **Een verbinding loopt vast op een time-out:** controleer of *toegang tot het lokale netwerk* is
  toegestaan voor de app, of de telefoon op hetzelfde wifi zit als de server, en het adres van de
  server.
- **„Je instellingen waren beschadigd en zijn teruggezet”:** de app kon haar instellingen niet lezen
  en is opnieuw begonnen. Je bestanden zijn veilig; verbindingen, taken en favorieten moeten opnieuw
  worden ingesteld of uit een back-up worden hersteld ([hoofdstuk 12](#12-een-back-up-van-de-app)).
- **Een taak is gestopt:** open hem in *Taken*; zijn pagina zegt waarom. Korte netwerkstoringen gaan
  vanzelf verder; een gepauzeerde taak wacht op jou.
