# StocksScraper — handleiding

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · Nederlands*

Geschreven voor StocksScraper 0.2.175 (oktober 2026). Waar deze handleiding en de app iets anders
zeggen, heeft de app gelijk.

---

## 1. Wat StocksScraper is

StocksScraper volgt een **volglijst** — aandelen, ETF's, grondstoffen en crypto — en **meldt je
wanneer er een beweegt** met ±5 % (of de drempel die je kiest). Het is voor persoonlijk gebruik:
alles wordt op je telefoon berekend, zonder server en zonder account.

- De **volglijst** is gratis, volledig en onbeperkt.
- De **portefeuille** — wat je bezit, wat het waard is, of je winst maakt — is het premiumdeel, een
  eenmalige aankoop. Hij is zichtbaar, met een sterretje, voordat je hem hebt.
- Er is geen koersbron ingebouwd: **jij** geeft de app de adressen van de bronnen die je gebruikt.

---

## 2. Gegevensbronnen

[Instellingen](app:settings) → *Gegevensbronnen* bevat één adres per **rol**, elk genoemd naar de vorm
van wat ze teruggeeft: een koersreeks zonder sleutel (de hoofdbron), een koersmomentopname en een
tijdreeks (beide met een sleutel die je invult), een CSV-koers en een cryptoprijs. Een rol zonder
adres slaapt.

- Elk soort instrument heeft een eigen **terugvalketen**: faalt de eerste bron, dan wordt de volgende
  gevraagd. Je hoeft nooit met de hand te kiezen.
- *Status* op hetzelfde scherm zegt welke bron het laatst antwoordde en wat de keten doet.
- Zonder enige bron zegt de lijst dat, in plaats van op elke rij een fout te tonen.
- Wie een adres invult, staat in voor de voorwaarden van die dienst.

---

## 3. De volglijst

- **Voeg** een instrument toe met **+** (of *Zoeken / toevoegen* in het menu): zoek op naam of
  ticker; lokale noteringen worden ook gevonden.
- **Categorieën:** groepeer je favorieten onder eigen koppen, klap ze in en sleep ze in de volgorde
  die je wilt (*Herschikken*).
- Elke rij toont het soort instrument, de koers en — naar keuze in het menu ⋮ — de cijfers of een
  trendlijn. Een **puntje** zegt of de markt open is: een levende of een bevroren koers.
- Bij het openen toont de app meteen de laatst bekende koersen, gedimd en gedateerd, en vernieuwt ze
  daarna.
- Tik op een instrument voor de **details**: een koersgrafiek over meerdere periodes, de marktstatus,
  het nieuws, links en de eigen meldingen.
- Het **hartje** op een instrument bepaalt of het op de startpagina van je SyncHub verschijnt.

---

## 4. Meldingen

- Er komt een melding als een instrument de **drempel** (standaard 5 %) beweegt ten opzichte van de
  vorige slotkoers. De app controleert standaard elk uur, op de achtergrond.
- *Instellingen → Meldingen* stelt de drempel in, hoe vaak gecontroleerd wordt, hoeveel meldingen per
  instrument per dag (standaard één), een optionele **week**beweging (standaard uit) en **Stil 's
  nachts**: een melding die in het venster valt, wordt aan het einde getoond als ze nog geldt.
- In de **Meldingen** van een instrument: een eigen drempel, **koersniveaus** (gaan één keer af als ze
  overschreden worden) en **Dempen** voor 1 dag, 1 week of tot je het weer aanzet.
- **Meldingen** in het menu beantwoordt *wat heb ik gemist?*: elke melding die afging over de hele
  lijst, nieuwste eerst; het menu ⋮ filtert koersniveaus of procentuele bewegingen.
- Een melding gaat over de sessie van vandaag en zegt wanneer de beweging gebeurde. Erop tikken opent
  het instrument.

---

## 5. Portefeuille (premium)

- **Posities:** wat je bezit, gewaardeerd in één **referentievaluta** (*Instellingen →
  Portefeuille*), met winst per regel en in totaal, en een waardecurve over de gekozen periode.
- **Een positie is haar transacties:** open een positie om aankopen, verkopen en dividenden toe te
  voegen; aantal en gemiddelde aankoopprijs volgen daaruit.
- **Kassaldi** en **subportefeuilles** (één per rekening bijvoorbeeld): de titel wisselt ertussen.
- **Beleggingsplan:** een doorlopende kooporder — wekelijks, maandelijks, twee keer per maand of per
  kwartaal — boekt zijn aankopen zelf op de geplande dagen.
- **Importeren / exporteren:** plak of kies een lijst met posities (CSV), of importeer een
  bankafschrift — een overzicht van posities of een gedateerd journaal — waarvan het formaat vanzelf
  wordt herkend.
- De portefeuille wordt nergens heen gestuurd, tenzij je *Mijn portefeuille synchroniseren* aanzet
  ([hoofdstuk 7](#7-synchub)).

---

## 6. Nieuws en widget

- **Nieuws** verzamelt artikelen over je lijst; de details van een instrument tonen de eigen
  artikelen. Lezen, een ster geven, bewaren om offline te lezen of het origineel openen.
- De **widget** toont je lijst op het startscherm, met de laatst bekende koersen; hij haalt nooit
  zelf iets op.

---

## 7. SyncHub

Als je thuis een **SyncHub** draait, houdt de app je lijst, categorieën, meldingen en instellingen
gelijk op meerdere telefoons en in de webinterface van de hub.

1. Open **SyncHub** in het menu. De app zoekt de hub in je netwerk, of je typt zijn adres.
2. Open in de webinterface van de hub **Instellingen → Apparaten → Apparaat koppelen** en scan de
   QR-code. De app vertrouwt de hub pas als de vingerafdruk van zijn certificaat bevestigd is.

- De **portefeuille** reist alleen mee als je **Mijn portefeuille synchroniseren** (premium) aanzet,
  na een bevestiging.
- **Alles opnieuw versturen** vult een hub die zijn gegevens kwijt is weer aan.
- Is de hub lang onbereikbaar, dan zegt de app dat.

---

## 8. Beveiliging en back-ups

- *Instellingen → Beveiliging → Appvergrendeling*: bescherm de hele app, of alleen de portefeuille,
  met je vingerafdruk, gezicht of schermvergrendeling. De vergrendeling verbergt; ze **versleutelt
  niet**.
- *Instellingen → Back-up & herstel* bewaart de lijst, de meldingen en de instellingen in een bestand
  — de portefeuille alleen als je die aanvinkt — en zet ze terug. API-sleutels komen nooit in een
  onversleutelde back-up.

---

## 9. Als er iets misgaat

- **„Geen gegevensbron ingesteld”:** vul minstens het adres van de hoofdbron in
  ([hoofdstuk 2](#2-gegevensbronnen)).
- **Een koers lijkt oud:** het puntje en de leeftijdsregel zeggen of de markt dicht is of de bron niet
  antwoordde; *Gegevensbronnen → Status* zegt welke bron het laatst antwoordde.
- **Een melding kwam niet:** controleer de drempel en het aantal per dag, of het instrument gedempt
  is, de nachtelijke stilte, en of de telefoon de meldingen van de app toestaat.
- Vragen en ideeën: *Instellingen → Over → Feedback sturen*.
