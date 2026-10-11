# SoundMaster — handleiding

*[English](README-en.md) · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · Nederlands*

Geschreven voor SoundMaster 0.1.48 (oktober 2026). Waar deze handleiding en de app iets anders
zeggen, heeft de app gelijk.

---

## 1. Wat SoundMaster is

SoundMaster is een **geluidsmeter**: hij toont in decibel hoe luid het rond je telefoon is. Op
verzoek **neemt** hij ook geluid **op**.

Hij belooft wat een telefoon kan waarmaken, en niets meer:

- **Gekalibreerd** tegen een echte geluidsmeter klopt een meting tot op ongeveer **±3 dB**. Met de
  startwaarde kan ze ongeveer **±10 dB** afwijken.
- Twee metingen op dezelfde telefoon zijn goed te vergelijken (ongeveer ±3 dB), ook zonder
  kalibratie.
- Het bruikbare bereik loopt van ongeveer **30 tot 95 dB**.

Hij beantwoordt *„is deze ruimte luid?”*, nooit *„overtreedt dit een regel?”*: het is geen
instrument van klasse 1 of 2. *Instellingen → Over* bevat de volledige verklaring.

---

## 2. De eerste keer

SoundMaster heeft de **microfoon** nodig. Bij het starten vraagt hij er nooit uit zichzelf om: Meting
toont één zin en een knop **Microfoontoegang toestaan**. Heb je definitief geweigerd, dan zegt Meting
dat en biedt aan de systeeminstellingen te openen.

De microfoon wordt alleen gebruikt zolang de app op het scherm staat. Op de achtergrond wordt niets
gemeten of opgenomen.

---

## 3. Meten

**Meting** is het eerste scherm.

- De **naald** toont het huidige niveau; het grote getal is hetzelfde niveau.
- De twee **markeringen** op de boog, *Min* en *Max*, onthouden het laagste en hoogste naaldniveau
  sinds de app openging of sinds de laatste reset.
- De **boog** kleurt van groen naar rood naarmate het niveau stijgt (rood vanaf 85 dB).
- Onder het getal geeft een alledaags geluid van ongeveer hetzelfde niveau een idee van de schaal.
- De regel onder het getal zegt hoe het niveau wordt berekend: *A-gewogen* of *ongewogen*, *snel* of
  *langzaam* ([hoofdstuk 6](#6-instellingen-die-de-meting-veranderen)).

Sommige toestanden **zijn geen niveaus**, en de app toont ze nooit als getallen:

- **Oversturing** — het geluid is te hard voor de microfoon; het echte niveau is hoger dan alles wat
  getoond wordt.
- **Geen signaal** — de microfoon levert pure stilte (vaak houdt een andere app hem vast).
- *onder het bruikbare bereik* — een stille ruimte, onder ongeveer 30 dB: het getal blijft staan,
  maar vertrouw het minder.

### 3.1 Een meting: een tijdje meten, dan bewaren

De **actiebalk** onderaan werkt op de meting:

1. **Start** (het kleine grafiekpictogram) begint een meting; dezelfde knop stopt haar.
2. Tijdens een meting toont **Deze meting** haar laagste en hoogste niveau en haar **Leq** (de
   gemiddelde energie over de meting), met een lijn van de laatste 60 seconden.
3. **Sessie opslaan** bewaart het resultaat in **Geschiedenis**. *Meting terugzetten* wist de meting
   en de markeringen. **Delen** stuurt de huidige meting als tekst.

De app verlaten pauzeert de meting; ze gaat verder als je terugkomt. De frequentieweging wijzigen, of
een wisseling van microfoonbron, beëindigt de meting, klaar om op te slaan.

### 3.2 Het alarm

Boven de **alarmdrempel** (85 dB tenzij je die wijzigt) wordt Meting rood en toont hoeveel het
erboven zit. Een **hoorbaar alarm** (een korte piep) kan aan; het staat standaard uit omdat de eigen
microfoon van de telefoon de piep hoort. Het alarm is maar zo goed als de kalibratie erachter.

---

## 4. Spectrum

**Spectrum** verdeelt het geluid in tien octaafbanden, van 31,5 Hz tot 16 kHz, en toont welke band
overheerst. De banden zijn **relatief**: ze zeggen welk deel van het geluid het sterkst is, nooit een
niveau in dB per band. *Vastgezet* in het menu ⋮ bevriest het beeld; *Live* start het weer.

---

## 5. Opnemen

De ronde knop **Opnemen**, op **Opname** en op Meting als er geen meting loopt, start een opname;
**Pauze** en **Hervatten** staan ernaast.

- Opnamen staan nieuwste eerst, met hun duur en grootte, en de markeringen *oversturing* en
  *gepauzeerd*. Speel er een af in de lijst zelf.
- Selecteer een opname voor de actiebalk: **verwijderen**, **delen**, **hernoemen** en
  **downloaden** (een kopie in een map naar keuze).
- Opnemen verandert de meting niet: de meter blijft meten.
- Opnamen blijven op de telefoon. Ze zitten niet in de back-up van de app, en een opname stopt als de
  app van het scherm verdwijnt.

### 5.1 Een opname uitschrijven

**Uitschrijven**, in de actiebalk van Opname, zet de spraak van een opname om in tekst **op de
telefoon**, met de spraakherkenning van het systeem. Er wordt niets verstuurd. Het vereist Android 13
of nieuwer en een telefoon waarvan de herkenning offline werkt; is je taal niet geïnstalleerd, dan
biedt het scherm aan die via het systeem te downloaden. De transcriptie kan gekopieerd of gedeeld
worden, en kan fouten bevatten.

---

## 6. Instellingen die de meting veranderen

In [Instellingen](app:settings) → *Meting*:

- **Frequentieweging:** *A-gewogen* (standaard, dicht bij het gehoor) of *Ongewogen*.
- **Tijdweging:** *Snel (125 ms)*, standaard, volgt veranderingen snel; *Langzaam (1 s)* maakt de
  naald rustiger.
- **Alarmdrempel** en **Hoorbaar alarm** ([hoofdstuk 3.2](#32-het-alarm)).
- **Meting starten bij openen:** een meting begint vanzelf bij de eerste meetwaarde na het starten.
- **Kalibratie** ([hoofdstuk 7](#7-kalibratie)).
- **Typische niveaus:** alledaagse geluiden en hun gebruikelijke niveau, de lijst waarmee Meting
  vergelijkt.

---

## 7. Kalibratie

Elke telefoonmicrofoon is anders. **Kalibratie** telt één verschuiving, in dB, bij elke meting op.

1. Zet SoundMaster naast een **echte geluidsmeter**, op dezelfde plek, bij een gelijkmatig geluid.
2. Open *Instellingen → Meting → Kalibratie* en stel de verschuiving in tot beide hetzelfde tonen.

*Startwaarde gebruiken* gaat terug naar +110 dB. Een andere telefoon-app is geen referentie: die
controleert alleen dat er niets grof mis is. Elke opgeslagen sessie bewaart de verschuiving waarmee ze
gemeten is.

---

## 8. Geschiedenis

**Geschiedenis** toont de opgeslagen sessies, nieuwste eerst: datum, duur, Leq, laagste en hoogste
niveau, piek, wegingen, verschuiving en microfoonbron. Een sessie met oversturing markeert haar
cijfers: het zijn ondergrenzen, geen niveaus. Selecteer sessies om ze te verwijderen of te delen.

---

## 9. Een back-up van de app

*Instellingen → Back-up & herstel* bewaart de instellingen en de sessiegeschiedenis in een bestand
(nooit het geluid) en zet ze terug.

- **Automatische back-up** maakt dat bestand elke dag.
- Als je een SyncHub hebt, kan de back-up ook **op de hub** worden bewaard: koppel via het
  back-upscherm, met de code die de hub toont. Die koppeling opent de back-ups van SoundMaster en
  verder niets. Het is de enige keer dat de app het netwerk gebruikt.

---

## 10. Als er iets misgaat

- **„De microfoon kon niet worden geopend”:** misschien houdt een andere app hem vast, of weigert de
  telefoon dit soort opname. Sluit de andere app en kom terug naar SoundMaster.
- **Geen signaal** terwijl de ruimte niet stil is: een andere app of een gesprek houdt de microfoon
  vast.
- **„Je instellingen waren beschadigd en zijn teruggezet”:** de app is opnieuw begonnen, met de
  startverschuiving. **Je sessies en opnamen zijn veilig**; kalibreer opnieuw.
- Vragen en ideeën: *Instellingen → Over → Feedback sturen*.
