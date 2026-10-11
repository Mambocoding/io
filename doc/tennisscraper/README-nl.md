# Tennis Scraper — handleiding

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · Nederlands*

Geschreven voor Tennis Scraper 0.1.140 (oktober 2026). Waar deze handleiding en de app iets anders
zeggen, heeft de app gelijk.

---

## 1. Wat Tennis Scraper is

Tennis Scraper volgt professioneel enkelspeltennis — de circuits van mannen en vrouwen — en **meldt
je wanneer een wedstrijd die je volgt begint**, terwijl ze gespeeld wordt en wanneer ze eindigt.

- Alles draait op je telefoon: geen account, geen server van ons. De meldingen berekent de telefoon
  zelf.
- De app levert geen gegevensadres mee: **jij** vult het adres in van de gegevensbron die je gebruikt
  ([hoofdstuk 8](#8-gegevensbron-en-status)). Tot dan blijven de schermen leeg en zeggen ze dat.
- Je volgt **spelers**, hele **toernooien** vanaf een ronde naar keuze, of één **wedstrijd**.
- **Eén wedstrijd, één melding** van elke soort, hoeveel redenen je ook hebt om haar te volgen.

---

## 2. Vandaag

**Vandaag** is het startscherm, opgebouwd uit blokken die je kiest: **wedstrijden**, **nieuws**,
**klassement** en **kalender**.

- Het wedstrijdenblok toont de wedstrijden van je favorieten en de gevolgde wedstrijden op één
  tijdlijn, met dagscheidingen: komende met hun tijd, **live** met de stand en een kloppend puntje,
  afgelopen met de uitslag. Een wedstrijd tussen twee van je favorieten verschijnt één keer.
- Tik op de titel van een blok om het scherm ervan te openen; bewerk de pagina om blokken toe te
  voegen, te verwijderen of te herschikken.
- De **anti-spoilermodus** (menu ⋮) verbergt op Vandaag het nieuws en elke stand en *Gewonnen* /
  *Verloren*, voor een wedstrijd die je later kijkt. Live-rijen houden hun *LIVE*.
- Trek omlaag om te vernieuwen. Vandaag vernieuwt ook op de achtergrond en opent dus met verse
  gegevens.
- Het menu ⋮ filtert ook op circuit: **Alle**, of een van de twee circuits. Het filter geldt op elk
  scherm en verandert nooit wat er gedownload wordt.

---

## 3. Spelers en volgen

- **Spelers** toont je favorieten, gegroepeerd per circuit. Typ in het zoekveld om elke speler te
  vinden; de ster voegt een favoriet toe of haalt hem weg.
- Het **belletje** van een favoriet dempt hem: hij blijft favoriet, maar zijn wedstrijden melden zich
  niet meer (tenzij een andere reden om de wedstrijd te volgen nog geldt).
- **Dit toernooi volgen** (vanuit de kop in Wedstrijden of Kalender): kies vanaf welke ronde —
  hoofdtoernooi, kwartfinales, halve finales of de finale. Elke wedstrijd van dat toernooi vanaf die
  ronde meldt zich dan.
- **Deze wedstrijd volgen** (in de details van een wedstrijd): haar meldingen komen ook als je geen
  van beide spelers volgt. Het volgen vervalt vanzelf na de wedstrijd.

---

## 4. Wedstrijden, kalender, schema's, klassement

- **Wedstrijden** toont de wedstrijden van een dag per toernooi, met kwalificanten, categorie en
  ronde. Tik op een wedstrijd voor de **details**: spelers, stand per set, ronde en de acties
  hieronder.
- **Kalender** toont de toernooien per week; open er een voor het **schema**, ronde per ronde.
  *Officiële website* opent de eigen pagina van het toernooi als de app die kent.
- **Klassement** toont het huidige klassement van elk circuit; tik op een speler voor de details.
- In de details van een wedstrijd:
  - **Delen** stuurt de wedstrijd als tekst;
  - **Aan agenda toevoegen** (komende wedstrijd met een begintijd) geeft haar aan je agenda-app;
  - **Kijken** (live of op het punt te beginnen) opent de wedstrijd op een zoekpagina voor uitzendingen
    — alleen als je een *Zoekadres om te kijken* hebt ingevuld in [Instellingen](app:settings).

---

## 5. Meldingen

[Instellingen](app:settings) → *Meldingen* bevat elke schakelaar:

- **Wedstrijdmeldingen:** *Begint zo* (aan, met hoe lang van tevoren), *Begin van de wedstrijd* (aan),
  *Live-stand* (uit) en *Uitslag* (aan).
- **Elke dag:** een **dagoverzicht** van de wedstrijden van je favorieten, één melding per speler, op
  het tijdstip dat je kiest; en een bericht wanneer een gevolgd toernooi begint.
- **Stille uren** (standaard uit, 23:00–08:00 als ze aanstaan): meldingen die erin vallen, vervallen.
- **Gedempte spelers** toont de favorieten die je dempte.

Tikken op een melding opent de wedstrijd.

---

## 6. Nieuws

Vul je een **adres van een nieuwsfeed** in (een RSS- of Atom-feed, in *Instellingen*), dan toont
**Nieuws** de nieuwste artikelen, en kan Vandaag *nieuws over je favorieten* tonen. **Alles als
gelezen markeren** staat in de actiebalk. Zonder adres is het nieuws helemaal verborgen en wordt er
niets gedownload.

---

## 7. Widget en auto

- **Widget:** tot drie gevolgde wedstrijden van vandaag op het startscherm — live eerst, dan komende,
  dan afgelopen. Een tik opent Vandaag.
- **In de auto:** met de telefoon verbonden met het scherm van een auto kunnen wedstrijdmeldingen
  worden voorgelezen, en kun je de favorieten en het programma van de dag bekijken.

---

## 8. Gegevensbron en status

- *Instellingen → Gegevensbron* kiest waar de wedstrijden vandaan komen: een **scorebord**-bron
  (geen sleutel) of een **wedstrijdlijst met sleutel** (sleutel nodig), elk via een adres dat je
  invult. Wie een adres invult, staat in voor de voorwaarden van die dienst. Favorieten worden per
  bron bewaard.
- *Instellingen → Status* zegt wat de app het laatst deed: de gebruikte bron, de laatste geslaagde en
  de laatste mislukte ophaling, en de caches. Hier kijk je als een melding niet kwam.

---

## 9. Een back-up van de app

*Instellingen → Back-up & herstel* bewaart je favorieten, gevolgde items en instellingen in een
bestand en zet ze terug op een nieuwe telefoon.

---

## 10. Als er iets misgaat

- **Een melding kwam niet:** controleer in *Instellingen → Status* de laatste ophaling, of de melding
  aanstaat, of de speler niet gedempt is, of het geen stille uren waren, en of de telefoon meldingen
  toestaat en de app niet in slaap legt.
- **Een live-stand lijkt vast te zitten:** de getoonde stand is de laatste die de bron gaf; trek
  omlaag om te vernieuwen.
- **Geen nieuws:** het adres van de nieuwsfeed is leeg, of de feed antwoordde niet.
- Vragen en ideeën: *Instellingen → Over → Feedback sturen*.
