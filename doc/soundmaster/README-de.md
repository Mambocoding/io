# SoundMaster — Anleitung

*[English](README-en.md) · [Français](README-fr.md) · Deutsch · [Español](README-es.md) · [Nederlands](README-nl.md)*

Geschrieben für SoundMaster 0.1.48 (Oktober 2026). Wenn diese Anleitung und die App voneinander
abweichen, hat die App recht.

---

## 1. Was SoundMaster ist

SoundMaster ist ein **Schallpegelmesser**: er zeigt in Dezibel, wie laut es um dein Telefon herum
ist. Auf Wunsch **nimmt** er auch Ton **auf**.

Er verspricht, was ein Telefon leisten kann, und nicht mehr:

- **Kalibriert** gegen einen echten Schallpegelmesser ist ein Messwert auf etwa **±3 dB** genau. Mit
  dem Ausgangswert kann er um etwa **±10 dB** danebenliegen.
- Zwei Messwerte auf demselben Telefon lassen sich gut vergleichen (etwa ±3 dB), auch ohne
  Kalibrierung.
- Der nutzbare Bereich reicht etwa von **30 bis 95 dB**.

Er beantwortet *„Ist dieser Raum laut?“*, nie *„Verstößt das gegen eine Vorschrift?“*: er ist kein
Gerät der Klasse 1 oder 2. *Einstellungen → Über* enthält die vollständige Aussage.

---

## 2. Erster Start

SoundMaster braucht das **Mikrofon**. Es fragt nie von sich aus beim Start: Messung zeigt einen Satz
und die Taste **Mikrofonzugriff erlauben**. Hast du dauerhaft abgelehnt, sagt Messung das und bietet
an, die Systemeinstellungen zu öffnen.

Das Mikrofon wird nur benutzt, solange die App auf dem Bildschirm ist. Im Hintergrund wird nichts
gemessen und nichts aufgenommen.

---

## 3. Messen

**Messung** ist der erste Bildschirm.

- Die **Nadel** zeigt den aktuellen Pegel; die große Zahl ist derselbe Pegel.
- Die zwei **Marken** auf dem Bogen, *Min* und *Max*, halten den niedrigsten und höchsten
  Nadelpegel seit dem Öffnen der App oder dem letzten Zurücksetzen.
- Der **Bogen** wechselt von Grün nach Rot, wenn der Pegel steigt (rot ab 85 dB).
- Unter der Zahl gibt ein Alltagsgeräusch ähnlichen Pegels ein Gefühl für die Größenordnung.
- Die Zeile unter der Zahl sagt, wie der Pegel berechnet wird: *A-bewertet* oder *unbewertet*,
  *schnell* oder *langsam* ([Abschnitt 6](#6-einstellungen-die-den-messwert-ändern)).

Manche Zustände **sind keine Pegel**, und die App zeigt sie nie als Zahlen:

- **Übersteuerung** — der Schall ist zu laut für das Mikrofon; der wahre Pegel liegt höher als alles
  Angezeigte.
- **Kein Signal** — das Mikrofon liefert reine Stille (oft hält eine andere App es fest).
- *unter dem nutzbaren Bereich* — ein ruhiger Raum unter etwa 30 dB: die Zahl bleibt, aber vertraue
  ihr weniger.

### 3.1 Eine Messung: eine Weile messen, dann speichern

Die **Aktionsleiste** unten wirkt auf die Messung:

1. **Start** (das kleine Diagramm-Symbol) beginnt eine Messung; dieselbe Taste beendet sie.
2. Während einer Messung zeigt **Diese Messung** ihren niedrigsten und höchsten Pegel und ihren
   **Leq** (die mittlere Energie über die Messung), mit einer Kurve der letzten 60 Sekunden.
3. **Sitzung speichern** legt das Ergebnis im **Verlauf** ab. *Messung zurücksetzen* löscht die
   Messung und die Marken. **Teilen** sendet den aktuellen Messwert als Text.

Verlässt du die App, pausiert die Messung; sie läuft weiter, wenn du zurückkommst. Eine Änderung der
Frequenzbewertung oder ein Wechsel der Mikrofonquelle beendet die Messung, bereit zum Speichern.

### 3.2 Der Alarm

Über dem **Alarmschwellenwert** (85 dB, sofern du ihn nicht änderst) wird Messung rot und zeigt die
Überschreitung. Ein **akustischer Alarm** (ein kurzer Piepton) lässt sich einschalten; er ist
standardmäßig aus, weil das eigene Mikrofon des Telefons den Ton hört. Der Alarm ist nur so gut wie
die Kalibrierung dahinter.

---

## 4. Spektrum

**Spektrum** teilt den Schall in zehn Oktavbänder von 31,5 Hz bis 16 kHz und zeigt, welches Band
überwiegt. Die Bänder sind **relativ**: sie sagen, welcher Teil des Schalls am stärksten ist, nie
einen Pegel in dB pro Band. *Gehalten* im Menü ⋮ friert das Bild ein; *Live* startet es wieder.

---

## 5. Aufnehmen

Die runde Taste **Aufnehmen**, unter **Aufnahme** und auf Messung, wenn keine Messung läuft, startet
eine Aufnahme; **Pause** und **Fortsetzen** stehen daneben.

- Aufnahmen werden neueste zuerst gelistet, mit Dauer und Größe und den Markierungen *übersteuert*
  und *pausiert*. Spiele eine direkt in der Liste ab.
- Wähle eine Aufnahme für die Aktionsleiste: **löschen**, **teilen**, **umbenennen** und
  **herunterladen** (eine Kopie in einem Ordner deiner Wahl).
- Aufnehmen ändert den Messwert nicht: der Messer misst weiter.
- Aufnahmen bleiben auf dem Telefon. Sie sind nicht in der Sicherung der App, und eine Aufnahme
  endet, wenn die App den Bildschirm verlässt.

### 5.1 Eine Aufnahme transkribieren

**Transkribieren** in der Aktionsleiste von Aufnahme wandelt die Sprache einer Aufnahme **auf dem
Telefon** in Text um, mit der Spracherkennung des Systems. Es wird nichts irgendwohin gesendet. Nötig
sind Android 13 oder neuer und ein Telefon, dessen Erkennung offline arbeitet; ist deine Sprache
nicht installiert, bietet der Bildschirm an, sie vom System herunterzuladen. Das Transkript lässt
sich kopieren oder teilen und kann Fehler enthalten.

---

## 6. Einstellungen, die den Messwert ändern

In den [Einstellungen](app:settings) → *Messung*:

- **Frequenzbewertung:** *A-bewertet* (Standard, nah am Gehör) oder *Unbewertet*.
- **Zeitbewertung:** *Schnell (125 ms)*, Standard, folgt Änderungen rasch; *Langsam (1 s)* beruhigt
  die Nadel.
- **Alarmschwellenwert** und **Akustischer Alarm** ([Abschnitt 3.2](#32-der-alarm)).
- **Messung beim Öffnen starten:** eine Messung beginnt von selbst beim ersten Messwert nach dem
  Start.
- **Kalibrierung** ([Abschnitt 7](#7-kalibrierung)).
- **Typische Pegel:** Alltagsgeräusche und ihr üblicher Pegel, die Liste, mit der Messung vergleicht.

---

## 7. Kalibrierung

Jedes Telefonmikrofon ist anders. Die **Kalibrierung** addiert einen Versatz in dB zu jedem
Messwert.

1. Stelle SoundMaster neben einen **echten Schallpegelmesser**, am selben Ort, bei gleichmäßigem
   Schall.
2. Öffne *Einstellungen → Messung → Kalibrierung* und stelle den Versatz ein, bis beide dasselbe
   anzeigen.

*Ausgangswert verwenden* kehrt zu +110 dB zurück. Eine andere Telefon-App ist keine Referenz: sie
prüft nur, dass nichts grob falsch ist. Jede gespeicherte Sitzung hält den Versatz fest, mit dem sie
gemessen wurde.

---

## 8. Verlauf

Der **Verlauf** listet die gespeicherten Sitzungen, neueste zuerst: Datum, Dauer, Leq, niedrigster
und höchster Pegel, Spitze, Bewertungen, Versatz und Mikrofonquelle. Eine übersteuerte Sitzung
markiert ihre Zahlen: es sind Untergrenzen, keine Pegel. Wähle Sitzungen aus, um sie zu löschen oder
zu teilen.

---

## 9. Die App sichern

*Einstellungen → Sichern & wiederherstellen* speichert die Einstellungen und den Sitzungsverlauf in
einer Datei (nie den Ton) und stellt sie wieder her.

- **Automatische Sicherung** erstellt diese Datei jeden Tag.
- Wenn du einen SyncHub hast, kann die Sicherung auch **auf dem Hub** liegen: koppel über den
  Sicherungsbildschirm, mit dem Code, den der Hub zeigt. Diese Kopplung öffnet die Sicherungen von
  SoundMaster und sonst nichts. Es ist das einzige Mal, dass die App das Netzwerk nutzt.

---

## 10. Wenn etwas schiefgeht

- **„Das Mikrofon konnte nicht geöffnet werden“:** vielleicht hält eine andere App es, oder das
  Telefon verweigert diese Art der Aufnahme. Schließe die andere App und kehre zu SoundMaster zurück.
- **Kein Signal**, obwohl der Raum nicht still ist: eine andere App oder ein Anruf hält das Mikrofon.
- **„Ihre Einstellungen waren beschädigt und wurden zurückgesetzt“:** die App hat neu begonnen, mit
  dem Ausgangsversatz. **Deine Sitzungen und Aufnahmen sind sicher**; kalibriere erneut.
- Fragen und Ideen: *Einstellungen → Über → Feedback senden*.
