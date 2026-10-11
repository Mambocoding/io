# FlightScraper — handleiding

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · Nederlands*

Geschreven voor FlightScraper 0.1.79 (oktober 2026). Waar deze handleiding en de app iets anders
zeggen, heeft de app gelijk.

---

## 1. Wat FlightScraper is

FlightScraper houdt **één luchthaven** in de gaten en houdt een **logboek van haar bewegingen** bij:
elke landing en elke start die het ziet, met roepnaam, registratie, vliegtuigtype, maatschappij en
tijd. **Kijkregels** kunnen je waarschuwen als er een toestel komt dat je interesseert.

- Het leest **ADS-B-posities** — wat toestellen zelf uitzenden —, geen dienstregeling. Daarom ziet het
  ook vluchten die in geen enkel schema staan: militaire, overheids-, overbrengings-, uitgeweken of
  testvluchten.
- Een beweging is een **afleiding** uit posities, dus elke beweging draagt haar zekerheid:
  *waargenomen*, *afgeleid* of *onzeker*. Een ontbrekend veld staat er als **—**, nooit gegokt.
- Het toont alleen wat rond één luchthaven wordt uitgezonden. Het is geen vluchtvolger en geen
  bewakingsmiddel.

De app noemt geen enkele gegevensdienst: **jij** geeft haar het adres van een feed.

---

## 2. Aan de slag

1. **Kies je luchthaven:** *Luchthavens* in het menu → zoek op naam, stad of code. De
   luchthavenlijst zit in de app en werkt offline; ze vult coördinaten, hoogte en tijdzone voor je
   in. Stel de **straal** in (hoe ver rond de luchthaven gekeken wordt, in km). Je kunt meerdere
   luchthavens bewaren; er wordt er precies één gevolgd.
2. **Vul een feed in:** [Instellingen](app:settings) → *Feed*. Plak het adres van een ADS-B-feed die
   je mag gebruiken (een gemeenschapsaggregator, of je eigen ontvanger). Neemt de feed een cirkel aan,
   gebruik dan `{lat}`, `{lon}` en `{radius_nm}`: de app vult ze in. **Testen** vraagt één keer op en
   zegt hoeveel toestellen terugkwamen.
3. Wacht twee pollingrondes: de **eerste ronde legt alleen vast wat er al is**; bewegingen
   verschijnen vanaf de tweede.

---

## 3. Het bewegingslogboek

**Bewegingen** is het startscherm: nieuwste eerst, gegroepeerd per dag.

- Elke rij: een pijl (aankomst of vertrek), de lokale tijd, de roepnaam, de typeaanduiding en
  beschrijving, de registratie, de regels die overeenkwamen en een zekerheidsteken.
- Het menu ⋮ filtert **Aankomsten / Vertrekken / Alle**, **toont of verbergt niet-overeenkomende**
  bewegingen, sorteert en vernieuwt. Het vergrootglas doorzoekt het logboek.
- **De statusregel** boven de lijst zegt wanneer de laatste geslaagde ronde was en hoeveel toestellen
  in de cirkel waren, of waarom de laatste mislukte. Een mislukte ronde verwijdert nooit iets.
- Tik op een beweging voor de **details**: identiteit, tijden, zekerheid met een verklarende zin,
  overeenkomende regels, een samenvatting van het spoor en **dit toestel hier** — hoe vaak het eerder
  kwam.
- De actiebalk van de details: **Delen** (als tekst), **Extern openen** in een vluchtvolger naar
  keuze ([hoofdstuk 7](#7-links-naar-een-vluchtvolger)), **Verwijderen**.

---

## 4. Live en Kaart

- **Live** toont de toestellen die nu in de cirkel zijn, met afstand en hoogte, vernieuwd zolang het
  scherm open is. Het onderdeel **Verwacht** toont toestellen die de luchthaven naderen — een
  voorspelling, als zodanig aangeduid, als bereik gegeven, en weg zodra ze niet meer klopt.
- **Kaart** tekent dezelfde toestellen waar ze zijn, rond de luchthaven en haar cirkel. Een
  achtergrondkaart verschijnt alleen als je een tegeladres invult in *Instellingen → Kaarttegelbron*;
  de kaart werkt ook zonder.

Live en Kaart vragen alleen op zolang ze op het scherm staan.

---

## 5. Kijkregels en meldingen

**Kijkregels** bepalen welke bewegingen voor jou tellen.

- Een regel combineert criteria: een exact **type** (`A332`), een **typefamilie** (een voorvoegsel),
  **militair**, een **roepnaam-voorvoegsel**, een **registratie**, woorden in de **beschrijving** of
  bij de **maatschappij**, een **eerste bezoek** van dit toestel of dit type, een **squawk**-code.
  *Alle* of *één* ervan moet kloppen.
- Kies aankomsten, vertrekken of beide, en een belang. Test een regel op het logboek voordat hij
  waarschuwt: het scherm toont met welke eerdere bewegingen hij zou hebben overeengekomen.
- **Meldingen** staan uit tot je ze aanzet (*Instellingen → Meldingen*). Je krijgt **één keer** per
  toestel, richting en dag een melding, hoeveel regels er ook overeenkomen.
- **Stille uren** (standaard 22:00–07:00 op de luchthaven) houden meldingen tot de ochtend vast; een
  regel met hoog belang kan ze negeren.
- Een regel kan je ook waarschuwen als een overeenkomend toestel **nadert**, nog voor het landt.

---

## 6. Pollen: hoe vaak de app kijkt

- Zolang Live, Kaart of Actief kijken open is: standaard elke minuut (nooit vaker dan elke 30
  seconden). Na fouten wacht de app langer — 1, 2, 4 en dan 8 minuten.
- Op de achtergrond: ongeveer elke 15 minuten, wat een aankomst nog vangt, tot 15 minuten te laat.
- **Pollingschema** (*Instellingen → Meldingen*): op uren die je kiest, polt de achtergrond in korte
  vlagen.
- **Actief kijken:** voor een avond blijven pollen op het voorgrondritme met het scherm uit, voor een
  duur die je instelt. Zolang het loopt, staat er een melding met een knop *Stoppen*.

---

## 7. Links naar een vluchtvolger

FlightScraper noemt geen enkele vluchtvolger. Voeg in *Instellingen → Links* de adressjablonen toe van
de volgers die je gebruikt, met plaatshouders die de app uit de beweging invult (registratie,
roepnaam, hexcode…). De eerste link is de standaard voor *Extern openen*. De app haalt deze adressen
nooit zelf op.

---

## 8. Vluchtschema (experimenteel)

*Hulpmiddelen → Vluchtschema* toont het aankomst- en vertrekbord van de gevolgde luchthaven, gelezen
uit pagina's waarvan je de adressen plakt. Het blijft **naast** het logboek, nooit erin: niets wat het
leest wordt een beweging of zet een waarschuwing in gang. Rijen die het logboek waarschijnlijk zag,
worden gemarkeerd.

---

## 9. Je gegevens

- *Instellingen → Gegevens → Back-up & herstel* bewaart het logboek, de luchthavens, regels, links en
  instellingen in een bestand en zet ze terug.
- *Instellingen → Logboek* bepaalt hoe lang bewegingen bewaard blijven (standaard voor altijd) en
  **exporteert het logboek** als spreadsheetbestand (CSV).

---

## 10. Als er iets misgaat

- **„Geen feed ingesteld”:** vul een feedadres in ([hoofdstuk 2](#2-aan-de-slag)).
- **„De feed beperkt deze app op dit moment”:** de feed vraagt de app trager te gaan; ze houdt zelf
  afstand. Kies een langer interval als het blijft gebeuren.
- **Na de eerste ronde verschijnt niets:** normaal — bewegingen beginnen bij de tweede ronde.
- **Een beweging is *onzeker*:** het spoor had gaten; de app zegt wat ze zag, meer niet.
- **Meldingen komen niet:** controleer of ze in de app aanstaan, door de telefoon zijn toegestaan en
  of het geen stille uren zijn. De batterijbesparing van de telefoon kan achtergrondrondes
  vertragen: *Instellingen* heeft een rij om de app daarvan uit te zonderen.
- Vragen en ideeën: *Instellingen → Over → Feedback sturen*.
