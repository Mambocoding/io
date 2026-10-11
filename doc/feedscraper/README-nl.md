# FeedScraper — handleiding

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · Nederlands*

Geschreven voor FeedScraper 0.1.252 (oktober 2026). Waar deze handleiding en de app iets anders
zeggen, heeft de app gelijk.

---

## 1. Wat FeedScraper is

FeedScraper is een **feedlezer**: je abonneert je op de feeds van de sites die je volgt (RSS, Atom, RDF
of JSON Feed), en hun nieuwe artikelen komen naar je telefoon.

- Alles wordt op de telefoon opgehaald en bewaard: geen account, geen server van ons.
- Lezen, een ster geven, bewaren om offline te lezen, zoeken en het nieuws op de achtergrond krijgen.
- Als je thuis een **SyncHub** draait, kunnen je feeds en wat je las je volgen naar andere telefoons en
  naar de webinterface van de hub ([hoofdstuk 8](#8-synchroniseren-met-je-synchub)). Zonder hub is de
  app een gewone lezer.

---

## 2. Feeds toevoegen

- **Feed toevoegen** (in het menu): plak het adres van een feed, of gewoon van de site — biedt de
  pagina meerdere feeds aan, dan kies je er een. De titel komt uit de feed; pas hem aan als je wilt en
  kies een categorie.
- **Importeren uit een bestand** (OPML, de standaard abonnementenlijst, in *Instellingen*): haalt de
  feeds van een andere lezer binnen. Importeren voegt alleen toe; het verwijdert of herschikt je feeds
  nooit. **Exporteren naar een bestand** doet het omgekeerde.
- **Feed uit een pagina halen** (*Hulpmiddelen*): voor een site zonder feed stelt de app een regel voor
  die de artikelen uit de pagina haalt, en past die bij elke vernieuwing toe. Het is experimenteel.

---

## 3. Lezen

- **Weergaven** in het menu: **Alle feeds**, **Favorieten** (artikelen met een ster), **Opgeslagen
  (offline)** en een **Feeds**-overzicht met één knop per feed. Elke feed en elke categorie is ook een
  weergave.
- De lijst staat stil terwijl je leest: artikelen die tijdens een bezoek binnenkomen, wachten achter een
  pil *nieuwe artikelen* bovenaan. Scrol tot het einde om oudere te laden.
- **Veeg** een rij om haar als gelezen of ongelezen te markeren, of om er een ster aan te geven. **Lang
  drukken** selecteert een artikel en de actiebalk toont wat je ermee kunt doen.
- **Alles als gelezen markeren** leegt een weergave in één keer.
- Open een artikel om het te lezen; veeg of gebruik de pijlen voor het vorige en volgende. De actiebalk
  biedt ster, delen, offline opslaan en openen in de browser. Tekstgrootte en regelafstand zijn aan te
  passen.
- Het vergrootglas **zoekt** in de huidige weergave; één tik breidt uit naar alle feeds.
- Op een breed scherm staan de lijst en het geopende artikel naast elkaar.

---

## 4. Offline lezen

**Offline opslaan** bewaart een artikel met tekst en afbeeldingen, leesbaar zonder netwerk; **Feed
offline opslaan** doet dat voor alle ongelezen artikelen van een feed. Opgeslagen artikelen staan in
**Opgeslagen (offline)**. *Instellingen* toont hoeveel ruimte ze innemen, kan ze na het lezen met een
vertraging verwijderen, en kan afbeeldingen tot wifi beperken.

---

## 5. Je feeds ordenen

- **Feeds en categorieën bewerken** (in het menu) herschikt feeds en categorieën, verplaatst feeds
  tussen categorieën, voegt categorieën samen of verwijdert ze.
- Een feed bewerken wijzigt zijn adres, titel en categorie, schakelt hem uit, of **zegt het abonnement
  op**. *Artikelen verbergen waarvan de titel bevat* verbergt artikelen op trefwoord (één term per
  regel); ze worden niet verwijderd, en de term wissen brengt ze terug.
- Een **hartje** op een feed maakt hem favoriet; met een hub gebruikt de hub het om te zeggen wat nieuw
  is.
- Een feed die blijft falen, wordt in het menu gemarkeerd, met een link naar zijn **ophaallogboek**.
  Bestaat het adres van een feed niet meer, dan stelt de app de feeds voor die de site nu aanbiedt.

---

## 6. Vernieuwen en meldingen

- Feeds vernieuwen op de achtergrond, downloaden alleen wat veranderde en houden afstand van feeds die
  falen. *Instellingen* bepaalt hoe vaak, of mobiele data gebruikt mag worden en of elke feed
  vernieuwd wordt als de app opent.
- Trek omlaag in een weergave om haar meteen te vernieuwen.
- **Meldingen bij nieuwe artikelen** staan standaard uit en worden per feed gekozen.
- **Gelezen artikelen verwijderen die ouder zijn dan** (standaard uit) houdt de database klein.

---

## 7. Instellingen en privacy

In [Instellingen](app:settings): **Openen bij starten** (waar je gebleven was, het feedoverzicht of je
favorieten), weergave, vernieuwen, meldingen, offline opslag, back-ups en de app-vergrendeling.

- Artikelen worden opgeschoond voor ze getoond worden: geen enkel script uit een artikel draait ooit.
- De **app-vergrendeling** (standaard uit) vraagt je vingerafdruk of schermvergrendeling; ze verbergt,
  ze versleutelt niet.
- *Back-up & herstel* bewaart je feeds, categorieën, leesstatus en instellingen in een bestand en zet
  ze terug.

---

## 8. Synchroniseren met je SyncHub

Synchroniseren met een hub is wat een eenmalige aankoop ontgrendelt; al het andere is gratis.

1. Open **SyncHub** in het menu. De app zoekt de hub in je netwerk, of je typt zijn adres.
2. Open in de webinterface van de hub **Instellingen → Apparaten → Apparaat koppelen** en scan de
   QR-code met de app.
3. Vergelijk de vingerafdruk van het certificaat als erom gevraagd wordt: de app vertrouwt de hub pas
   als jij die bevestigt.

- Feeds, categorieën, hartjes, gelezen- en sterstatus en instellingen reizen dan in beide richtingen;
  de hub blijft je feeds ophalen terwijl je telefoon slaapt.
- Verandert het certificaat van de hub, dan stopt de synchronisatie tot jij beslist. Niets wordt
  stilletjes opnieuw vertrouwd.
- Is de hub lang onbereikbaar, dan zegt de app dat. Het puntje in het menu toont de
  synchronisatiestatus in één oogopslag.

---

## 9. Als er iets misgaat

- **„… is niet vernieuwd — diagnose”:** open het ophaallogboek van de feed; het zegt wat de site
  antwoordde.
- **„… blijft ons weigeren”:** de site blokkeert automatische lezers; de app kan daar netjes niets aan
  doen.
- **Een artikel toont geen afbeelding:** sommige sites weigeren afbeeldingen aan apps; het artikel is
  toch te lezen.
- **De synchronisatie stopte na een wijziging aan de hub:** vergelijk de nieuwe vingerafdruk op de
  pagina's van de hub voordat je hem weer vertrouwt.
- Vragen en ideeën: *Instellingen → Over → Feedback sturen*.
