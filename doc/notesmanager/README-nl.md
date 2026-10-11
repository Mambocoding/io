# NotesManager — handleiding

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · Nederlands*

Geschreven voor NotesManager 0.1.34 (oktober 2026). Waar deze handleiding en de app iets anders
zeggen, heeft de app gelijk.

---

## 1. Wat NotesManager is

NotesManager bewaart drie soorten notities op je telefoon:

- **notities** — vrije tekst, in Markdown als je wilt;
- **checklists** — items om af te vinken;
- **takenlijsten** — items met een vervaldatum en, als je wilt, een herinnering.

Je notities staan op de telefoon. Als je thuis een **SyncHub** draait, reizen ze via die hub ook naar
je andere apparaten ([hoofdstuk 7](#7-synchroniseren-met-je-synchub)); zonder hub werkt de app precies
hetzelfde.

---

## 2. Een notitie schrijven

- Tik op **+**: een nieuwe notitie opent, klaar om te typen. Geen type om te kiezen, geen
  Opslaan-knop.
- Wat je typt, wordt **gaandeweg bewaard**, en nog eens op het moment dat je de app verlaat. De
  titelbalk zegt wanneer de notitie het laatst is bewaard.
- De titel is niet verplicht: zonder titel wordt de eerste regel van de notitie getoond.
- Tekst die je vanuit een andere app deelt (*Delen → NotesManager*) wordt een nieuwe notitie.

### 2.1 Checklists en takenlijsten

- In het menu ⋮ van een notitie maakt **Omzetten** er een **Checklist** of een **Takenlijst** van,
  en terug. Elke regel van een notitie wordt een item; items worden weer regels. Een takenlijst
  omzetten laat haar vervaldatums en herinneringen vallen, en de app vraagt het eerst.
- Voeg een item toe in de laatste rij en druk op Enter; het veld blijft open voor het volgende.
- Sleep een item aan zijn greep om het te verplaatsen; veeg het weg om het te verwijderen (met
  *Ongedaan maken*).
- Het menu ⋮ kan afgevinkte items verbergen of alle vinkjes weghalen.
- In een takenlijst krijgt een item een chip **vervaldatum** en daarna een chip **herinnering**: op
  het tijdstip van de herinnering toont een melding het item; erop tikken opent de notitie. De eerste
  herinnering vraagt toestemming om meldingen te tonen.

---

## 3. Notities terugvinden

- **Alle notities** toont je notities als kaarten of als lijst (het menu ⋮ wisselt). **Vastgezette**
  notities staan bovenaan.
- **Veeg** een kaart naar rechts om haar vast te zetten, naar links om haar te archiveren. Vegen
  verwijdert nooit.
- **Sorteer** op laatste wijziging, aanmaak, titel, of je eigen volgorde binnen een label.
- **Zoeken** (het vergrootglas) doorzoekt titels, teksten en items terwijl je typt — gearchiveerde
  notities inbegrepen. Accenten tellen niet mee: *ete* vindt *été*. Beperk tot **Tekst** of **Items**.

### 3.1 Labels

Een notitie kan meerdere **labels** dragen. Voeg er een toe vanuit de notitie (de chip *+* onder de
titel) of maak labels in het onderdeel **Labels** van het menu. Tikken op een label in het menu toont
alleen zijn notities; lang drukken hernoemt of verwijdert het. Een label verwijderen houdt zijn
notities.

---

## 4. Selecteren, archiveren, verwijderen

- **Lang drukken** start een selectie; tik op meer notities om ze toe te voegen. De actiebalk biedt
  dan vastzetten, archiveren, labels, delen en verwijderen voor allemaal tegelijk.
- **Archiveren** haalt een notitie uit *Alle notities* en de labels zonder haar te verwijderen; ze
  blijft vindbaar en bewerkbaar in **Archief**.
- **Verwijderen** stuurt notities naar de **Prullenbak**. Een notitie in de Prullenbak kan
  **hersteld** worden, of definitief verwijderd.
- De Prullenbak bewaart notities **30 dagen** en verwijdert ze dan. Die termijn is die van de hub:
  een notitie die langer bewaard bleef, zou op je andere apparaten weer tot leven kunnen komen.

---

## 5. Als twee apparaten dezelfde notitie bewerken

NotesManager **voegt twee versies van de tekst van een notitie nooit stilletjes samen**.

- Is de tekst van een notitie op twee apparaten gewijzigd voordat ze synchroniseerden, dan **blijven
  beide teksten bewaard**: de tweede wordt een **Conflictkopie**, direct na het origineel getoond. Lees
  ze allebei, houd wat je wilt, verwijder de andere.
- Wijzigt een notitie op een ander apparaat **terwijl jij typt**, dan wordt jouw tekst bewaard als
  conflictkopie en toont de notitie de tekst van het andere apparaat, met een regel die zegt waar je
  getypte tekst is gebleven.
- In een lijst worden items één voor één samengevoegd: vinkjes, volgorde en datums volgen de laatste
  wijziging; twee verschillende wijzigingen aan de tekst van hetzelfde item worden twee items.

---

## 6. Je gegevens: exporteren, importeren, alles verwijderen

In [Instellingen](app:settings) → *Gegevens*:

- **Notities exporteren** bewaart je notities als een pakket Markdown-bestanden (en takenlijsten in
  het gangbare formaat voor agendataken) dat andere apps kunnen openen.
- **Notities importeren** leest de export van een andere notitie-app: een zip met één JSON-bestand
  per notitie. De app toont wat ze vond voordat ze iets importeert; labels, vastgezette en
  gearchiveerde notities blijven behouden.
- **Alle notities verwijderen** wist elke notitie, elk label en elk item op deze telefoon, nadat je
  een bevestigingszin hebt getypt. Je instellingen, de app-vergrendeling en de hubkoppeling blijven.
  Is de telefoon gekoppeld, dan houdt de hub zijn kopie en stuurt die bij de volgende synchronisatie
  terug: wil je dat het verwijderen blijft, ontkoppel dan eerst de hub, of verwijder de notities op de
  hub zelf.

---

## 7. Synchroniseren met je SyncHub

1. Open **SyncHub** onderaan het menu. De app zoekt de hub in je thuisnetwerk; vindt ze hem niet,
   typ dan zijn adres.
2. Open in de webinterface van de hub **Instellingen → Apparaten → Apparaat koppelen** en
   **scan** de QR-code met de app (de knop *Scannen*). Het scannen controleert het certificaat van de
   hub precies.
3. Je notities gaan naar de hub en reizen vanaf dan in beide richtingen.

- **Synchronisatiemodus:** *Automatisch* synchroniseert vanzelf, kort na elke wijziging en op de
  achtergrond; *Handmatig* wacht op **Nu synchroniseren**.
- Het synchronisatiescherm toont wanneer de laatste ronde plaatsvond en, per soort gegevens, hoeveel
  wijzigingen elke kant op gingen.
- Is de hub lang onbereikbaar, dan kan de app je dat met een melding laten weten.
- De webinterface van de hub toont en bewerkt dezelfde notities.

---

## 8. Privacy en app-vergrendeling

- Notities worden alleen op de telefoon bewaard, en op je eigen hub als je er een koppelt. De app
  maakt met niets anders verbinding.
- **App-vergrendeling** (*Instellingen*): NotesManager vraagt bij het openen je vingerafdruk, gezicht
  of schermvergrendeling, en na de vertraging die je kiest. De app-vergrendeling verbergt de app; ze
  **versleutelt** je notities **niet**.

---

## 9. Als er iets misgaat

- **„Je instellingen waren beschadigd en zijn teruggezet”:** de app kon haar instellingen niet lezen
  en is opnieuw begonnen. **Je notities zijn veilig.** De hubkoppeling moet opnieuw; de hub ontvangt
  dan je notities opnieuw.
- **Een notitie is gemarkeerd als *Conflictkopie*:** twee versies van haar tekst zijn elkaar
  tegengekomen; zie [hoofdstuk 5](#5-als-twee-apparaten-dezelfde-notitie-bewerken).
- **Een herinnering ging niet af:** controleer of meldingen zijn toegestaan voor NotesManager en of de
  telefoon de app exacte alarmen laat instellen.
- Vragen en ideeën: *Instellingen → Over → Feedback sturen*.
