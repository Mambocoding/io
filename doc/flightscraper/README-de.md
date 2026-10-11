# FlightScraper — Anleitung

*[English](README-en.md) · [Français](README-fr.md) · Deutsch · [Español](README-es.md) · [Nederlands](README-nl.md)*

Geschrieben für FlightScraper 0.1.79 (Oktober 2026). Wenn diese Anleitung und die App voneinander
abweichen, hat die App recht.

---

## 1. Was FlightScraper ist

FlightScraper beobachtet **einen Flughafen** und führt ein **Protokoll seiner Bewegungen**: jede
Landung und jeden Start, den es beobachtet, mit Rufzeichen, Kennzeichen, Luftfahrzeugtyp, Betreiber
und Uhrzeit. **Beobachtungsregeln** können dich benachrichtigen, wenn ein Luftfahrzeug kommt, das
dich interessiert.

- Es liest **ADS-B-Positionen** — was Luftfahrzeuge selbst aussenden —, keinen Flugplan. Deshalb sieht
  es auch Flüge, die in keinem Plan stehen: militärische, staatliche, Überführungs-, umgeleitete oder
  Testflüge.
- Eine Bewegung ist eine **Schlussfolgerung** aus Positionen, daher trägt jede ihre Sicherheit:
  *beobachtet*, *erschlossen* oder *unsicher*. Ein fehlendes Feld steht als **—**, nie geraten.
- Es zeigt nur, was rund um einen Flughafen ausgesendet wird. Es ist weder ein Flugverfolger noch ein
  Überwachungswerkzeug.

Die App nennt keinen Datendienst: **du** gibst ihr die Adresse eines Feeds.

---

## 2. Loslegen

1. **Wähle deinen Flughafen:** *Flughäfen* im Menü → suche nach Name, Stadt oder Code. Das
   Flughafenverzeichnis ist in der App enthalten und funktioniert offline; es füllt Koordinaten,
   Höhe und Zeitzone für dich aus. Stelle den **Radius** ein (wie weit rund um den Flughafen geschaut
   wird, in km). Mehrere Flughäfen lassen sich speichern; genau einer wird beobachtet.
2. **Gib einen Feed ein:** [Einstellungen](app:settings) → *Feed*. Füge die Adresse eines ADS-B-Feeds
   ein, den du nutzen darfst (ein gemeinschaftlicher Aggregator oder dein eigener Empfänger). Nimmt
   der Feed einen Kreis an, verwende `{lat}`, `{lon}` und `{radius_nm}`: die App füllt sie aus.
   **Testen** fragt einmal ab und sagt, wie viele Luftfahrzeuge zurückkamen.
3. Warte zwei Abfragen ab: die **erste Abfrage hält nur fest, was schon da ist**; Bewegungen
   erscheinen ab der zweiten.

---

## 3. Das Bewegungsprotokoll

**Bewegungen** ist der Startbildschirm: neueste zuerst, nach Tagen gruppiert.

- Jede Zeile: ein Pfeil (Ankunft oder Abflug), die Ortszeit, das Rufzeichen, Typkennung und
  Beschreibung, das Kennzeichen, die passenden Regeln und eine Sicherheitsmarke.
- Das Menü ⋮ filtert **Ankünfte / Abflüge / Alle**, **zeigt oder verbirgt nicht zugeordnete**
  Bewegungen, sortiert und aktualisiert. Die Lupe durchsucht das Protokoll.
- **Die Statuszeile** über der Liste sagt, wann die letzte erfolgreiche Abfrage war und wie viele
  Luftfahrzeuge im Kreis waren, oder warum die letzte scheiterte. Eine gescheiterte Abfrage entfernt
  nie etwas.
- Tippe auf eine Bewegung für ihr **Detail**: Identität, Zeiten, Sicherheit mit einem erklärenden
  Satz, passende Regeln, eine Zusammenfassung der Spur und **dieses Luftfahrzeug hier** — wie oft es
  schon kam.
- Die Aktionsleiste des Details: **Teilen** (als Text), **Extern öffnen** in einem Flugverfolger
  deiner Wahl ([Abschnitt 7](#7-links-zu-einem-flugverfolger)), **Löschen**.

---

## 4. Live und Karte

- **Live** listet die Luftfahrzeuge, die gerade im Kreis sind, mit Entfernung und Höhe, aktualisiert,
  solange der Bildschirm offen ist. Sein Abschnitt **Erwartet** zeigt Luftfahrzeuge, die sich dem
  Flughafen nähern — eine Vorhersage, als solche gekennzeichnet, als Spanne angegeben und
  verschwunden, sobald sie nicht mehr gilt.
- **Karte** zeichnet dieselben Luftfahrzeuge dort, wo sie sind, um den Flughafen und seinen Kreis.
  Eine Hintergrundkarte erscheint nur, wenn du unter *Einstellungen → Kartenkachelquelle* eine
  Kacheladresse eingibst; die Karte funktioniert auch ohne.

Live und Karte fragen nur ab, solange sie auf dem Bildschirm sind.

---

## 5. Beobachtungsregeln und Benachrichtigungen

**Beobachtungsregeln** entscheiden, welche Bewegungen für dich zählen.

- Eine Regel verbindet Kriterien: einen genauen **Typ** (`A332`), eine **Typfamilie** (ein Präfix),
  **militärisch**, ein **Rufzeichen-Präfix**, ein **Kennzeichen**, Wörter in der **Beschreibung**
  oder beim **Betreiber**, einen **ersten Besuch** dieses Luftfahrzeugs oder dieses Typs, einen
  **Squawk**-Code. *Alle* oder *eines* davon müssen zutreffen.
- Wähle Ankünfte, Abflüge oder beides und eine Wichtigkeit. Teste eine Regel am Protokoll, bevor sie
  alarmiert: der Bildschirm zeigt, auf welche früheren Bewegungen sie gepasst hätte.
- **Benachrichtigungen** sind aus, bis du sie einschaltest (*Einstellungen → Benachrichtigungen*). Du
  wirst **einmal** pro Luftfahrzeug, Richtung und Tag benachrichtigt, egal wie viele Regeln passen.
- **Ruhezeiten** (standardmäßig 22:00–07:00 am Flughafen) halten Benachrichtigungen bis zum Morgen
  zurück; eine Regel hoher Wichtigkeit kann sie ignorieren.
- Eine Regel kann dich auch warnen, wenn ein passendes Luftfahrzeug **im Anflug** ist, bevor es
  landet.

---

## 6. Abfragen: wie oft die App schaut

- Solange Live, Karte oder Aktive Beobachtung offen ist: standardmäßig jede Minute (nie öfter als alle
  30 Sekunden). Nach Fehlern wartet die App länger — 1, 2, 4, dann 8 Minuten.
- Im Hintergrund: etwa alle 15 Minuten, was eine Ankunft noch erfasst, bis zu 15 Minuten verspätet.
- **Abfrageplan** (*Einstellungen → Benachrichtigungen*): zu Zeiten deiner Wahl fragt der
  Hintergrund stattdessen in kurzen Schüben ab.
- **Aktive Beobachtung:** für einen Abend weiter im Vordergrundtakt abfragen, bei ausgeschaltetem
  Bildschirm, für eine Dauer, die du festlegst. Solange sie läuft, zeigt eine Benachrichtigung sie
  an, mit einer Taste *Stopp*.

---

## 7. Links zu einem Flugverfolger

FlightScraper nennt keinen Flugverfolger. Füge unter *Einstellungen → Links* die Adressvorlagen der
Verfolger hinzu, die du nutzt, mit Platzhaltern, die die App aus der Bewegung füllt (Kennzeichen,
Rufzeichen, Hex-Code…). Der erste Link ist der Standard für *Extern öffnen*. Die App ruft diese
Adressen nie selbst ab.

---

## 8. Flugplan (experimentell)

*Werkzeuge → Flugplan* zeigt die Ankunfts- und Abflugtafel des beobachteten Flughafens, gelesen aus
Seiten, deren Adressen du einfügst. Sie bleibt **neben** dem Protokoll, nie darin: nichts, was sie
liest, wird zu einer Bewegung oder löst einen Alarm aus. Zeilen, die das Protokoll wahrscheinlich
gesehen hat, werden markiert.

---

## 9. Deine Daten

- *Einstellungen → Daten → Sichern & wiederherstellen* speichert Protokoll, Flughäfen, Regeln, Links
  und Einstellungen in einer Datei und stellt sie wieder her.
- *Einstellungen → Protokoll* legt fest, wie lange Bewegungen behalten werden (standardmäßig für
  immer), und **exportiert das Protokoll** als Tabellendatei (CSV).

---

## 10. Wenn etwas schiefgeht

- **„Keine Datenquelle eingerichtet“:** gib eine Feed-Adresse ein ([Abschnitt 2](#2-loslegen)).
- **„Der Feed drosselt diese App gerade“:** der Feed bittet die App, langsamer zu werden; sie hält
  von selbst Abstand. Wähle ein längeres Intervall, wenn es sich wiederholt.
- **Nach der ersten Abfrage erscheint nichts:** normal — Bewegungen beginnen mit der zweiten Abfrage.
- **Eine Bewegung ist *unsicher*:** die Spur hatte Lücken; die App sagt, was sie sah, nicht mehr.
- **Benachrichtigungen kommen nicht:** prüfe, ob sie in der App eingeschaltet und vom Telefon erlaubt
  sind und ob gerade Ruhezeit ist. Der Energiesparmodus des Telefons kann Hintergrundabfragen
  verzögern: die *Einstellungen* haben eine Zeile, um die App davon auszunehmen.
- Fragen und Ideen: *Einstellungen → Über → Feedback senden*.
