# StocksScraper — Anleitung

*[English](README-en.md) · [Français](README-fr.md) · Deutsch · [Español](README-es.md) · [Nederlands](README-nl.md)*

Geschrieben für StocksScraper 0.2.175 (Oktober 2026). Wenn diese Anleitung und die App voneinander
abweichen, hat die App recht.

---

## 1. Was StocksScraper ist

StocksScraper verfolgt eine **Beobachtungsliste** — Aktien, ETFs, Rohstoffe und Kryptowährungen — und
**benachrichtigt dich, wenn sich eine davon bewegt**, um ±5 % (oder die Schwelle deiner Wahl). Es ist
für den persönlichen Gebrauch: alles wird auf deinem Telefon berechnet, ohne Server und ohne Konto.

- Die **Beobachtungsliste** ist kostenlos, vollständig und unbegrenzt.
- Das **Portfolio** — was du besitzt, was es wert ist, ob du im Plus bist — ist der Premium-Teil, ein
  einmaliger Kauf. Es ist mit einem Funken sichtbar, bevor du es hast.
- Keine Kursquelle ist eingebaut: **du** gibst der App die Adressen der Quellen, die du nutzt.

---

## 2. Datenquellen

[Einstellungen](app:settings) → *Datenquellen* enthält eine Adresse pro **Rolle**, jede benannt nach
der Form dessen, was sie liefert: eine Kursreihe ohne Schlüssel (die Hauptquelle), ein Kurs-Snapshot
und eine Zeitreihe (beide mit einem Schlüssel, den du eingibst), ein CSV-Kurs und ein Kryptopreis.
Eine Rolle ohne Adresse ruht.

- Jede Instrumentart hat ihre eigene **Ausweichkette**: scheitert die erste Quelle, wird die nächste
  gefragt. Du musst nie von Hand wählen.
- *Status* auf demselben Bildschirm sagt, welche Quelle zuletzt geantwortet hat und was die Kette tut.
- Ohne jede Quelle sagt die Liste das, statt auf jeder Zeile einen Fehler zu zeigen.
- Wer eine Adresse eingibt, verantwortet die Bedingungen dieses Dienstes.

---

## 3. Die Beobachtungsliste

- **Füge** ein Instrument mit **+** hinzu (oder *Suchen / hinzufügen* im Menü): suche nach Name oder
  Kürzel; lokale Börsennotierungen werden auch gefunden.
- **Kategorien:** gruppiere deine Favoriten unter eigenen Überschriften, klappe sie ein und ziehe sie
  in die gewünschte Reihenfolge (*Neu anordnen*).
- Jede Zeile zeigt die Art des Instruments, seinen Kurs und — nach deiner Wahl im Menü ⋮ — seine
  Zahlen oder eine Trendlinie. Ein **Punkt** sagt, ob der Markt offen ist: ein lebender oder ein
  eingefrorener Kurs.
- Beim Öffnen zeigt die App sofort die zuletzt bekannten Kurse, abgeblendet und datiert, und
  aktualisiert sie dann.
- Tippe auf ein Instrument für sein **Detail**: ein Kursdiagramm über mehrere Zeiträume, der
  Marktstatus, seine News, Links und seine eigenen Alarme.
- Das **Herz** an einem Instrument bestimmt, ob es auf der Startseite deines SyncHub erscheint.

---

## 4. Alarme

- Ein Alarm kommt, wenn sich ein Instrument um die **Schwelle** (standardmäßig 5 %) gegenüber dem
  Vortagesschluss bewegt. Die App prüft standardmäßig stündlich, im Hintergrund.
- *Einstellungen → Benachrichtigungen* legt die Schwelle fest, wie oft geprüft wird, wie viele Alarme
  pro Instrument und Tag (standardmäßig einer), einen optionalen **Wochen**-Bewegungsalarm
  (standardmäßig aus) und **Nachts stummschalten**: ein Alarm, der in das Fenster fällt, wird an
  dessen Ende gezeigt, wenn er noch gilt.
- In den **Alarmen** eines Instruments: seine eigene Schwelle, **Kursmarken** (lösen einmal aus, wenn
  sie überschritten werden) und **Stumm** für 1 Tag, 1 Woche oder bis du es wieder einschaltest.
- **Alarme** im Menü beantwortet *Was habe ich verpasst?*: jeder ausgelöste Alarm über die ganze
  Liste, neueste zuerst; das Menü ⋮ filtert Kursmarken oder prozentuale Bewegungen.
- Ein Alarm betrifft die heutige Sitzung und sagt, wann die Bewegung stattfand. Ein Tippen öffnet das
  Instrument.

---

## 5. Portfolio (Premium)

- **Positionen:** was du hältst, bewertet in einer **Referenzwährung** (*Einstellungen → Portfolio*),
  mit Gewinn pro Zeile und insgesamt, und einer Wertkurve über den gewählten Zeitraum.
- **Eine Position sind ihre Transaktionen:** öffne eine Position, um Käufe, Verkäufe und Dividenden
  hinzuzufügen; Menge und durchschnittlicher Einstandspreis ergeben sich daraus.
- **Barbestände** und **Unterportfolios** (eines pro Konto etwa): der Titel wechselt zwischen ihnen.
- **Sparplan:** ein Dauerkaufauftrag — wöchentlich, monatlich, zweimal im Monat oder vierteljährlich —
  bucht seine Käufe an den geplanten Tagen selbst.
- **Import / Export:** füge eine Bestandsliste (CSV) ein oder wähle sie, oder importiere den Auszug
  einer Bank — eine Bestandsaufstellung oder ein datiertes Journal —, dessen Format von selbst
  erkannt wird.
- Das Portfolio wird nie irgendwohin gesendet, außer du schaltest *Mein Portfolio synchronisieren*
  ein ([Abschnitt 7](#7-synchub)).

---

## 6. News und Widget

- **News** sammelt Artikel zu deiner Liste; das Detail eines Instruments zeigt seine eigenen. Lesen,
  mit Stern markieren, für offline speichern oder das Original öffnen.
- Das **Widget** zeigt deine Liste auf dem Startbildschirm, mit den zuletzt bekannten Kursen; es ruft
  nie selbst ab.

---

## 7. SyncHub

Wenn du zu Hause einen **SyncHub** betreibst, hält die App deine Liste, Kategorien, Alarme und
Einstellungen auf mehreren Telefonen und in der Weboberfläche des Hubs gleich.

1. Öffne **SyncHub** im Menü. Die App sucht den Hub in deinem Netz, oder du gibst seine Adresse ein.
2. Öffne in der Weboberfläche des Hubs **Einstellungen → Geräte → Gerät koppeln** und scanne den
   QR-Code. Die App vertraut dem Hub erst, wenn der Fingerabdruck seines Zertifikats bestätigt ist.

- Das **Portfolio** reist nur, wenn du **Mein Portfolio synchronisieren** (Premium) einschaltest,
  nach einer Bestätigung.
- **Alles erneut senden** füllt einen Hub wieder auf, der seine Daten verloren hat.
- Ist der Hub lange nicht erreichbar, sagt dir die App das.

---

## 8. Sicherheit und Sicherungen

- *Einstellungen → Sicherheit → App-Sperre*: schütze die ganze App oder nur das Portfolio mit
  Fingerabdruck, Gesicht oder Displaysperre. Die Sperre verbirgt; sie **verschlüsselt nicht**.
- *Einstellungen → Sichern & wiederherstellen* speichert Liste, Alarme und Einstellungen in einer
  Datei — das Portfolio nur, wenn du es ankreuzt — und stellt sie wieder her. API-Schlüssel kommen nie
  in eine unverschlüsselte Sicherung.

---

## 9. Wenn etwas schiefgeht

- **„Keine Datenquelle konfiguriert“:** gib mindestens die Adresse der Hauptquelle ein
  ([Abschnitt 2](#2-datenquellen)).
- **Ein Kurs wirkt alt:** Punkt und Alterszeile sagen, ob der Markt geschlossen ist oder die Quelle
  nicht geantwortet hat; *Datenquellen → Status* sagt, welche Quelle zuletzt geantwortet hat.
- **Ein Alarm kam nicht:** prüfe Schwelle und Tageszahl, ob das Instrument stumm ist, die nächtliche
  Stummschaltung und ob das Telefon die Benachrichtigungen der App erlaubt.
- Fragen und Ideen: *Einstellungen → Über → Feedback senden*.
