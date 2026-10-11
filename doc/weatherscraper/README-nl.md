# WeatherScraper — handleiding

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · Nederlands*

Geschreven voor WeatherScraper 0.1.135 (oktober 2026). Waar deze handleiding en de app iets anders
zeggen, heeft de app gelijk.

---

## 1. Wat WeatherScraper is

WeatherScraper toont een **verwachting voor 14 dagen** voor de steden die je kiest. Het heeft geen
eigen verwachting en noemt geen enkele weersite: **jij** zegt waar het moet lezen.

- **Een verwachtingspagina die je plakt:** het adres van een meerdaagse verwachtingspagina van een
  site die je vertrouwt. De app leest de tabel met dagen.
- **Een verwachtingsdienst die je instelt:** het adres van een verwachtings-API die je mag gebruiken,
  bevraagd voor een stad op haar coördinaten.

Een stad kan beide hebben, zodat een pagina met een nieuwe opmaak je niet zonder verwachting laat. De
bron van elke verwachting staat altijd op het scherm, met de host die je hebt ingevuld.

Een nieuwe installatie is leeg: geen stad, geen adres. Een korte wizard helpt je ze in te stellen.

---

## 2. De eerste keer

De wizard vraagt, op volgorde:

1. Welke **bronnen** je wilt gebruiken: geplakte pagina's, een verwachtingsdienst of beide.
2. De **adressen** van de dienst, als die er zijn: het verwachtingsadres en het geocoderingsadres,
   waarmee een stad op naam wordt gevonden. Laat een veld leeg om het over te slaan; alles is later aan
   te passen in [Instellingen](app:settings).
3. Je **eerste stad**.
4. Eventueel je **SyncHub** ([hoofdstuk 9](#9-synchub)).

Er wordt niets bewaard tot je op *Starten* tikt.

---

## 3. Steden toevoegen

Open het menu en tik op **+ Stad toevoegen**.

- **Op naam:** typ minstens twee letters; passende plaatsen verschijnen met hun regio. Eén tik voegt
  de stad toe. Hiervoor is een geocoderingsadres in de instellingen nodig.
- **Vanaf een pagina** (*Hulpmiddelen → Uit een pagina halen*, gemarkeerd als experimenteel):
  1. Plak het **adres** van de meerdaagse verwachtingspagina van de site (niet de startpagina) en tik
     op **Analyseren**. De app haalt de pagina één keer op.
  2. Tot drie kandidaat-tabellen worden als verwachtingsrijen getoond, elk met een inschatting: *Lijkt
     op een verwachting*, *Niet zeker — controleer het voorbeeld*, *Waarschijnlijk fout*. *Niet de
     juiste tabel?* toont de volgende.
  3. Het voorbeeld zegt welke daggegevens gevonden zijn (regen, wind, zon) en of de site
     **dagpagina's** heeft, die de uren van een dag geven als je die opent.
  4. Geef de stad een naam en tik op **Stad toevoegen**. Past de naam bij een plaats, dan worden haar
     coördinaten bewaard: de verwachtingsdienst neemt het over als de pagina niet meer werkt.

De extractor respecteert de `robots.txt` van de site, maakt zich eerlijk bekend en haalt zelden op.
Is een pagina met JavaScript gebouwd of weigert ze het verzoek, dan zegt hij dat. *Geavanceerd* laat
je de selectors met de hand schrijven. De voorwaarden van de site naleven is jouw zaak.

In het menu heeft elke stad een **hartje** (je favorieten, ook getoond op de startpagina van de hub),
een greep om te herschikken en **×** om haar te verwijderen (haar bewaarde verwachting wordt gewist).

---

## 4. De verwachting lezen

Het startscherm toont de gekozen stad. **Veeg opzij** of gebruik het menu om van stad te wisselen.

- **Drie weergaven**, via het menu ⋮: **Nu**, **7 dagen** (standaard, kaarten met details) en **14
  dagen** (een compacte lijst). Boven beide lijsten toont een **temperatuurgrafiek** de maxima boven
  de minima.
- Elke dag toont: weekdag en datum, een illustratie, min / max, en dan weertype · kans op regen ·
  millimeters · wind. Een waarde die de bron niet gaf, staat er als **—**: de app verzint er nooit een.
- **De statusregel** staat er altijd: hoe oud de verwachting is, van welke bron ze komt (de host die
  je invulde) en de laatste fout als een vernieuwing mislukte. Een mislukte vernieuwing haalt de
  verwachting nooit weg; die blijft staan, met haar leeftijd.
- Tik op een dag voor de **details**: de uren als de bron ze heeft, de luchtvochtigheid en de
  waarschuwingscategorieën van die dag.
- **Vernieuwen:** trek omlaag, of het vernieuwpictogram in de kop.
- De **actiebalk** biedt *Delen* (een afbeelding van de verwachting) en, voor een paginastad, *De
  bronpagina openen*.

### 4.1 Een stad met twee bronnen

Heeft een stad een pagina en coördinaten, dan toont **Bronnen vergelijken** (in *Instellingen*) een
pagina per bron plus een pagina **Gemiddelde** (gemiddelde temperaturen, het slechtste weertype van
de twee). Anders beslist de instelling **Voorkeursbron** welke bron eerst wordt gebruikt; de andere
neemt het over als de eerste faalt.

---

## 5. Vernieuwen

- Elke ochtend om 07:00 vernieuwt de app al je steden.
- Open je een stad waarvan de verwachting ouder is dan 30 minuten, dan vernieuwt ze die stad.
- **Vernieuwingsinterval** (standaard uit) voegt elke 1, 3, 6 of 12 uur een vernieuwing toe.
  Vernieuwen op de achtergrond kun je tot wifi beperken.
- Hoogstens twee verzoeken per vernieuwing voor een paginastad (de lijst, dan de pagina van vandaag),
  met steeds langere pauzes na fouten. Een site wordt nooit bestookt.

---

## 6. Waarschuwingen en officiële waarschuwingen

### 6.1 Waarschuwingen uit je verwachting

*Instellingen → Meldingen → Waarschuwingen* (standaard uit) houdt **vandaag en morgen** in je bewaarde
verwachtingen in de gaten en meldt zich één keer per stad, dag en soort als een van zes dingen wordt
verwacht: **vorst**, **hitte**, **zware regen**, **harde wind**, **sneeuw** of **onweer**. De
**gevoeligheid** (*Laag*, *Normaal*, *Hoog*) verschuift de drempels; elke soort kan uit, elke stad
ook. Een paginastad geeft meestal alleen temperaturen en weertypes, dus regen- en windwaarschuwingen
komen vooral van de verwachtingsdienst. Deze waarschuwingen worden op de telefoon berekend uit je
eigen verwachting: ze zijn niet officieel.

### 6.2 Officiële waarschuwingen

Vul je een **adres van een waarschuwingsfeed** in (een feed met officiële waarschuwingen in het
CAP-formaat, *Instellingen → API-adres*), dan toont het verwachtingsscherm de waarschuwingen die de
stad betreffen, geciteerd zoals uitgegeven, en kan ze melden. De app is geen alarmkanaal: ze vernieuwt
op haar eigen ritme, dus de pagina van de uitgever is leidend. Buiten het gebied van de feed toont de
app niets in plaats van „geen waarschuwingen”.

---

## 7. Instellingen van de bronnen

In [Instellingen](app:settings):

- **Voorspellingsmodel:** *Automatisch* laat de dienst kiezen; in plaats daarvan kun je een van vijf
  benoemde modellen kiezen. **Model per stad** overschrijft het voor één stad. Een schakelaar kan de
  spreiding tussen modellen in de grafiek tekenen.
- **Voorkeursbron** en **Bronnen vergelijken** ([hoofdstuk 4.1](#41-een-stad-met-twee-bronnen)).
- **API-adres:** de adressen voor verwachting, geocodering en waarschuwingsfeed, elk leeg tot je het
  invult.
- **Vernieuwingsinterval** en mobiele data ([hoofdstuk 5](#5-vernieuwen)).

---

## 8. Widget en auto

- **Widget:** zet hem op het startscherm en kies een stad en een weergave; zijn grootte bepaalt
  hoeveel hij toont. Hij toont de bewaarde verwachting en haalt nooit zelf iets op.
- **In de auto:** met de telefoon verbonden met het scherm van een auto kies je een stad en lees je
  vandaag en de volgende dagen, met bron en leeftijd in de kop. Waarschuwingen blijven op de
  telefoon.

---

## 9. SyncHub

Als je thuis een **SyncHub** draait, kan de app haar steden, hartjes en instellingen met hem delen.

1. Open **SyncHub** onderaan het menu. De app zoekt de hub in je netwerk, of je typt zijn adres.
2. Open in de webinterface van de hub **Instellingen → Apparaten → Apparaat koppelen** en scan de
   QR-code met de app.

- **Betrouwbaarheid** (in het menu) toont, voor elke stad met een temperatuursensor die op de hub is
  opgegeven, hoe ver de verwachting van elke bron afweek van wat de sensor mat, per aantal dagen
  vooruit, over 30, 90 of 365 dagen. De eerste cijfers komen na ongeveer een week.
- *Alles opnieuw verzenden* op het synchronisatiescherm stuurt de gegevens van de app opnieuw als de
  hub iets mist.

---

## 10. Als er iets misgaat

- **„Deze pagina lijkt met JavaScript gebouwd”:** de app leest alleen wat de pagina stuurt; probeer
  een andere pagina van de site, of voeg de stad op naam toe.
- **„De robots.txt van deze pagina verbiedt geautomatiseerde toegang”:** de site vraagt robots die
  pagina niet te lezen; de app gehoorzaamt. Kies een andere bron.
- **De verwachting is oud:** de statusregel zegt waarom de laatste vernieuwing mislukte. De bewaarde
  verwachting blijft tot een vernieuwing slaagt.
- **Een waarde toont —:** de bron gaf haar niet. Dat is geen nul.
- Vragen en ideeën: *Instellingen → Over → Feedback sturen*.
