# WeatherScraper — Anleitung

*[English](README-en.md) · [Français](README-fr.md) · Deutsch · [Español](README-es.md) · [Nederlands](README-nl.md)*

Geschrieben für WeatherScraper 0.1.135 (Oktober 2026). Wenn diese Anleitung und die App voneinander
abweichen, hat die App recht.

---

## 1. Was WeatherScraper ist

WeatherScraper zeigt eine **14-Tage-Vorhersage** für die Städte deiner Wahl. Es hat keine eigene
Vorhersage und nennt keine Wetterseite: **du** sagst ihm, wo es lesen soll.

- **Eine Vorhersageseite, die du einfügst:** die Adresse einer Mehrtages-Vorhersageseite einer
  Website, der du vertraust. Die App liest ihre Tabelle der Tage.
- **Ein Vorhersagedienst, den du einrichtest:** die Adresse einer Vorhersage-API, die du nutzen
  darfst, abgefragt für eine Stadt über ihre Koordinaten.

Eine Stadt kann beides haben, damit eine Seite mit neuem Layout dich nicht ohne Vorhersage lässt. Die
Quelle jeder Vorhersage wird immer auf dem Bildschirm genannt, mit dem Host, den du eingegeben hast.

Eine neue Installation ist leer: keine Stadt, keine Adresse. Ein kurzer Assistent hilft beim
Einrichten.

---

## 2. Erster Start

Der Assistent fragt der Reihe nach:

1. Welche **Quellen** du nutzen willst: eingefügte Seiten, einen Vorhersagedienst oder beides.
2. Die **Adressen** des Dienstes, falls vorhanden: die Vorhersageadresse und die
   Geokodierungsadresse, mit der eine Stadt per Name gefunden wird. Lass ein Feld leer, um es zu
   überspringen; alles lässt sich später in den [Einstellungen](app:settings) ändern.
3. Deine **erste Stadt**.
4. Auf Wunsch deinen **SyncHub** ([Abschnitt 9](#9-synchub)).

Nichts wird gespeichert, bevor du auf *Starten* tippst.

---

## 3. Städte hinzufügen

Öffne das Menü und tippe auf **+ Stadt hinzufügen**.

- **Per Name:** tippe mindestens zwei Buchstaben; passende Orte erscheinen mit ihrer Region. Ein
  Tippen fügt die Stadt hinzu. Dafür braucht es eine Geokodierungsadresse in den Einstellungen.
- **Aus einer Seite** (*Werkzeuge → Aus einer Seite extrahieren*, als experimentell markiert):
  1. Füge die **Adresse** der Mehrtages-Vorhersageseite der Website ein (nicht ihre Startseite) und
     tippe auf **Analysieren**. Die App ruft die Seite einmal ab.
  2. Bis zu drei Kandidaten-Tabellen werden als Vorhersagezeilen gezeigt, jede mit einer
     Einschätzung: *Sieht nach einer Vorhersage aus*, *Unsicher — prüfen Sie die Vorschau*,
     *Wahrscheinlich falsch*. *Nicht die richtige Tabelle?* zeigt die nächste.
  3. Die Vorschau sagt, welche Tageswerte gefunden wurden (Regen, Wind, Sonne) und ob die Website
     **Tagesseiten** hat, die beim Öffnen eines Tages dessen Stunden liefern.
  4. Benenne die Stadt und tippe auf **Stadt hinzufügen**. Passt der Name zu einem Ort, werden seine
     Koordinaten behalten: der Vorhersagedienst übernimmt, wenn die Seite nicht mehr funktioniert.

Der Extraktor beachtet die `robots.txt` der Website, gibt sich ehrlich zu erkennen und ruft selten
ab. Ist eine Seite mit JavaScript gebaut oder lehnt sie die Anfrage ab, sagt er es. *Erweitert*
erlaubt, die Selektoren von Hand zu schreiben. Die Bedingungen der Website einzuhalten ist deine
Sache.

Im Menü hat jede Stadt ein **Herz** (deine Favoriten, auch auf der Startseite des Hubs gezeigt),
einen Griff zum Umsortieren und **×** zum Entfernen (ihre gespeicherte Vorhersage wird gelöscht).

---

## 4. Die Vorhersage lesen

Der Startbildschirm zeigt die gewählte Stadt. **Wische seitwärts** oder nutze das Menü, um die Stadt
zu wechseln.

- **Drei Ansichten** im Menü ⋮: **Jetzt**, **7 Tage** (Standard, Karten mit Details) und **14 Tage**
  (eine dichte Liste). Über beiden Listen zeigt ein **Temperaturdiagramm** die Höchst- über den
  Tiefstwerten.
- Jeder Tag zeigt: Wochentag und Datum, eine Illustration, Tief / Hoch, dann Wetterlage ·
  Regenwahrscheinlichkeit · Millimeter · Wind. Ein Wert, den die Quelle nicht geliefert hat, steht als
  **—**: die App erfindet nie einen.
- **Die Statuszeile** ist immer da: wie alt die Vorhersage ist, woher sie kommt (der eingegebene Host)
  und der letzte Fehler, falls eine Aktualisierung scheiterte. Eine gescheiterte Aktualisierung
  entfernt die Vorhersage nie; sie bleibt, mit ihrem Alter.
- Tippe auf einen Tag für sein **Detail**: Stunden, wenn die Quelle sie hat, Luftfeuchtigkeit und die
  Warnkategorien des Tages.
- **Aktualisieren:** nach unten ziehen oder das Aktualisieren-Symbol in der Kopfzeile.
- Die **Aktionsleiste** bietet *Teilen* (ein Bild der Vorhersage) und für eine Seiten-Stadt *Die
  Quellseite öffnen*.

### 4.1 Eine Stadt mit zwei Quellen

Hat eine Stadt eine Seite und Koordinaten, zeigt **Quellen vergleichen** (in den *Einstellungen*) eine
Seite pro Quelle plus eine Seite **Durchschnitt** (mittlere Temperaturen, die schlechtere Wetterlage
der beiden). Sonst entscheidet die Einstellung **Bevorzugte Quelle**, welche Quelle zuerst genutzt
wird; die andere übernimmt, wenn die erste scheitert.

---

## 5. Aktualisieren

- Jeden Morgen um 7:00 Uhr aktualisiert die App alle deine Städte.
- Öffnest du eine Stadt, deren Vorhersage älter als 30 Minuten ist, wird sie aktualisiert.
- **Aktualisierungsintervall** (standardmäßig aus) fügt alle 1, 3, 6 oder 12 Stunden eine
  Aktualisierung hinzu. Hintergrund-Aktualisierungen lassen sich aufs WLAN beschränken.
- Höchstens zwei Anfragen pro Aktualisierung für eine Seiten-Stadt (die Liste, dann die Seite von
  heute), mit wachsenden Pausen nach Fehlern. Eine Website wird nie überlastet.

---

## 6. Warnungen und amtliche Warnungen

### 6.1 Warnungen aus deiner Vorhersage

*Einstellungen → Benachrichtigungen → Warnungen* (standardmäßig aus) beobachtet **heute und morgen**
in deinen gespeicherten Vorhersagen und meldet sich einmal pro Stadt, Tag und Art, wenn eines von
sechs Ereignissen erwartet wird: **Frost**, **Hitze**, **Starkregen**, **starker Wind**, **Schnee**
oder ein **Gewitter**. Die **Empfindlichkeit** (*Niedrig*, *Normal*, *Hoch*) verschiebt die
Schwellen; jede Art lässt sich abschalten, jede Stadt auch. Eine Seiten-Stadt liefert meist nur
Temperaturen und Wetterlagen, daher kommen Regen- und Windwarnungen vor allem vom Vorhersagedienst.
Diese Warnungen werden auf dem Telefon aus deiner eigenen Vorhersage berechnet: sie sind nicht amtlich.

### 6.2 Amtliche Warnungen

Gibst du eine **Adresse des Warnungs-Feeds** ein (ein Feed amtlicher Warnungen im CAP-Format,
*Einstellungen → API-Adresse*), zeigt der Vorhersagebildschirm die Warnungen, die die Stadt betreffen,
so zitiert, wie sie herausgegeben wurden, und kann sie melden. Die App ist kein Warnkanal: sie
aktualisiert nach ihrem eigenen Takt, maßgeblich ist die Seite des Herausgebers. Außerhalb des
Gebiets des Feeds zeigt die App nichts statt „keine Warnungen“.

---

## 7. Einstellungen der Quellen

In den [Einstellungen](app:settings):

- **Vorhersagemodell:** *Automatisch* lässt den Dienst wählen; stattdessen lassen sich fünf benannte
  Modelle wählen. **Modell pro Stadt** überschreibt es für eine Stadt. Ein Schalter kann die
  Streuung zwischen den Modellen im Diagramm zeigen.
- **Bevorzugte Quelle** und **Quellen vergleichen**
  ([Abschnitt 4.1](#41-eine-stadt-mit-zwei-quellen)).
- **API-Adresse:** die Adressen für Vorhersage, Geokodierung und Warnungs-Feed, jede leer, bis du sie
  ausfüllst.
- **Aktualisierungsintervall** und mobile Daten ([Abschnitt 5](#5-aktualisieren)).

---

## 8. Widget und Auto

- **Widget:** lege es auf den Startbildschirm und wähle eine Stadt und eine Ansicht; seine Größe
  entscheidet, wie viel es zeigt. Es zeigt die gespeicherte Vorhersage und ruft nie selbst ab.
- **Im Auto:** mit dem Telefon am Bildschirm eines Autos wählst du eine Stadt und liest heute und die
  folgenden Tage, mit Quelle und Alter in der Kopfzeile. Warnungen bleiben auf dem Telefon.

---

## 9. SyncHub

Wenn du zu Hause einen **SyncHub** betreibst, kann die App ihre Städte, Herzen und Einstellungen mit
ihm teilen.

1. Öffne **SyncHub** unten im Menü. Die App sucht den Hub in deinem Netz, oder du gibst seine Adresse
   ein.
2. Öffne in der Weboberfläche des Hubs **Einstellungen → Geräte → Gerät koppeln** und scanne den
   QR-Code mit der App.

- **Treffsicherheit** (im Menü) zeigt für jede Stadt mit einem auf dem Hub angegebenen
  Temperatursensor, wie weit die Vorhersage jeder Quelle von dem abwich, was der Sensor gemessen hat,
  nach Vorlauf in Tagen, über 30, 90 oder 365 Tage. Erste Zahlen nach etwa einer Woche.
- *Alles erneut senden* auf dem Synchronisierungsbildschirm schickt die Daten der App erneut, falls
  dem Hub etwas fehlt.

---

## 10. Wenn etwas schiefgeht

- **„Diese Seite scheint von JavaScript aufgebaut zu werden“:** die App liest nur, was die Seite
  sendet; versuche eine andere Seite der Website oder füge die Stadt per Name hinzu.
- **„Die robots.txt dieser Seite untersagt den automatisierten Zugriff“:** die Website bittet Roboter,
  diese Seite nicht zu lesen; die App gehorcht. Wähle eine andere Quelle.
- **Die Vorhersage ist alt:** die Statuszeile sagt, warum die letzte Aktualisierung scheiterte. Die
  gespeicherte Vorhersage bleibt, bis eine Aktualisierung gelingt.
- **Ein Wert zeigt —:** die Quelle hat ihn nicht geliefert. Das ist nicht null.
- Fragen und Ideen: *Einstellungen → Über → Feedback senden*.
