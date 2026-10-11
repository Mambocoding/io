# NotesManager — Anleitung

*[English](README-en.md) · [Français](README-fr.md) · Deutsch · [Español](README-es.md) · [Nederlands](README-nl.md)*

Geschrieben für NotesManager 0.1.34 (Oktober 2026). Wenn diese Anleitung und die App voneinander
abweichen, hat die App recht.

---

## 1. Was NotesManager ist

NotesManager bewahrt drei Arten von Notizen auf deinem Telefon auf:

- **Notizen** — freier Text, auf Wunsch in Markdown;
- **Checklisten** — Einträge zum Abhaken;
- **Aufgabenlisten** — Einträge mit Fälligkeitsdatum und, wenn du willst, einer Erinnerung.

Deine Notizen liegen auf dem Telefon. Wenn du zu Hause einen **SyncHub** betreibst, gelangen sie über
ihn auch auf deine anderen Geräte ([Abschnitt 7](#7-mit-deinem-synchub-synchronisieren)); ohne Hub
funktioniert die App genauso.

---

## 2. Eine Notiz schreiben

- Tippe auf **+**: eine neue Notiz öffnet sich, bereit zum Schreiben. Kein Typ zu wählen, keine
  Speichern-Taste.
- Was du tippst, wird **laufend gespeichert**, und noch einmal in dem Moment, in dem du die App
  verlässt. Die Titelleiste sagt, wann die Notiz zuletzt gespeichert wurde.
- Der Titel ist freiwillig: ohne Titel wird die erste Zeile der Notiz angezeigt.
- Text, der aus einer anderen App geteilt wird (*Teilen → NotesManager*), wird zu einer neuen Notiz.

### 2.1 Checklisten und Aufgabenlisten

- Im Menü ⋮ einer Notiz macht **Umwandeln** daraus eine **Checkliste** oder eine **Aufgabenliste**,
  und zurück. Jede Zeile einer Notiz wird ein Eintrag; Einträge werden wieder Zeilen. Wird eine
  Aufgabenliste umgewandelt, gehen ihre Fälligkeitsdaten und Erinnerungen verloren, und die App fragt
  vorher.
- Füge einen Eintrag in der letzten Zeile hinzu und drücke Enter; das Feld bleibt für den nächsten
  offen.
- Ziehe einen Eintrag an seinem Griff, um ihn zu verschieben; wische ihn weg, um ihn zu entfernen
  (mit *Rückgängig*).
- Das Menü ⋮ kann abgehakte Einträge ausblenden oder alle Haken entfernen.
- In einer Aufgabenliste bekommt ein Eintrag einen Chip **Fälligkeit**, dann einen Chip
  **Erinnerung**: zur Erinnerungszeit zeigt eine Benachrichtigung den Eintrag; ein Tippen öffnet die
  Notiz. Die erste Erinnerung fragt nach der Erlaubnis für Benachrichtigungen.

---

## 3. Notizen finden

- **Alle Notizen** zeigt deine Notizen als Karten oder als Liste (das Menü ⋮ schaltet um).
  **Angeheftete** Notizen stehen vorne.
- **Wische** eine Karte nach rechts, um sie anzuheften, nach links, um sie zu archivieren. Wischen
  löscht nie.
- **Sortiere** nach letzter Änderung, Erstellung, Titel oder deiner eigenen Reihenfolge innerhalb
  eines Labels.
- **Suchen** (die Lupe) durchsucht Titel, Texte und Einträge, während du tippst — archivierte
  Notizen eingeschlossen. Akzente spielen keine Rolle: *ete* findet *été*. Grenze auf **Text** oder
  **Einträge** ein.

### 3.1 Labels

Eine Notiz kann mehrere **Labels** tragen. Füge eines in der Notiz hinzu (der Chip *+* unter dem
Titel) oder lege Labels im Abschnitt **Labels** des Menüs an. Ein Tippen auf ein Label im Menü zeigt
nur seine Notizen; langes Drücken benennt es um oder löscht es. Ein gelöschtes Label behält seine
Notizen.

---

## 4. Auswählen, archivieren, löschen

- **Langes Drücken** startet eine Auswahl; tippe weitere Notizen an, um sie hinzuzufügen. Die
  Aktionsleiste bietet dann Anheften, Archivieren, Labels, Teilen und Löschen für alle zugleich.
- **Archivieren** nimmt eine Notiz aus *Alle Notizen* und den Labels, ohne sie zu löschen; sie bleibt
  im **Archiv** auffindbar und bearbeitbar.
- **Löschen** schickt Notizen in den **Papierkorb**. Eine Notiz im Papierkorb lässt sich
  **wiederherstellen** oder endgültig löschen.
- Der Papierkorb behält Notizen **30 Tage** und löscht sie dann. Die Frist ist die des Hubs: eine
  länger aufbewahrte Notiz könnte auf deinen anderen Geräten wieder auferstehen.

---

## 5. Wenn zwei Geräte dieselbe Notiz ändern

NotesManager **führt zwei Fassungen des Texts einer Notiz nie stillschweigend zusammen**.

- Wurde der Text einer Notiz auf zwei Geräten geändert, bevor sie synchronisiert haben, **bleiben
  beide Texte erhalten**: der zweite wird eine **Konfliktkopie**, direkt nach dem Original angezeigt.
  Lies beide, behalte, was du willst, lösche die andere.
- Ändert sich eine Notiz auf einem anderen Gerät, **während du tippst**, bleibt dein Text als
  Konfliktkopie erhalten, und die Notiz zeigt den Text des anderen Geräts, mit einer Zeile, wohin deine
  Eingabe gegangen ist.
- In einer Liste werden Einträge einzeln zusammengeführt: Haken, Reihenfolge und Daten folgen der
  letzten Änderung; zwei verschiedene Änderungen am Text desselben Eintrags ergeben zwei Einträge.

---

## 6. Deine Daten: exportieren, importieren, alles löschen

In den [Einstellungen](app:settings) → *Daten*:

- **Notizen exportieren** speichert deine Notizen als Paket von Markdown-Dateien (und Aufgabenlisten
  im üblichen Kalender-Aufgabenformat), das andere Apps öffnen können.
- **Notizen importieren** liest den Export einer anderen Notiz-App: ein Zip mit einer JSON-Datei pro
  Notiz. Die App zeigt, was sie gefunden hat, bevor sie etwas importiert; Labels, angeheftete und
  archivierte Notizen bleiben erhalten.
- **Alle Notizen löschen** entfernt jede Notiz, jedes Label und jeden Eintrag auf diesem Telefon,
  nachdem du einen Bestätigungssatz eingegeben hast. Deine Einstellungen, die App-Sperre und die
  Hub-Kopplung bleiben. Ist das Telefon gekoppelt, behält der Hub seine Kopie und schickt sie bei der
  nächsten Synchronisierung zurück: damit das Löschen bleibt, trenne zuerst den Hub oder lösche die
  Notizen auf dem Hub selbst.

---

## 7. Mit deinem SyncHub synchronisieren

1. Öffne **SyncHub** unten im Menü. Die App sucht den Hub in deinem Heimnetz; findet sie ihn nicht,
   gib seine Adresse ein.
2. Öffne in der Weboberfläche des Hubs **Einstellungen → Geräte → Gerät koppeln** und **scanne** den
   QR-Code mit der App (die Taste *Scannen*). Das Scannen prüft das Zertifikat des Hubs genau.
3. Deine Notizen gehen zum Hub und reisen von da an in beide Richtungen.

- **Synchronisierungsmodus:** *Automatisch* synchronisiert von selbst, kurz nach jeder Änderung und im
  Hintergrund; *Manuell* wartet auf **Jetzt synchronisieren**.
- Der Synchronisierungsbildschirm zeigt, wann der letzte Austausch stattfand und, je Datenart, wie
  viele Änderungen in jede Richtung gingen.
- Ist der Hub lange nicht erreichbar, kann dich die App mit einer Benachrichtigung darauf hinweisen.
- Die Weboberfläche des Hubs zeigt und bearbeitet dieselben Notizen.

---

## 8. Privatsphäre und App-Sperre

- Notizen werden nur auf dem Telefon gespeichert, und auf deinem eigenen Hub, wenn du einen koppelst.
  Die App verbindet sich mit nichts anderem.
- **App-Sperre** (*Einstellungen*): NotesManager verlangt beim Öffnen deinen Fingerabdruck, dein
  Gesicht oder die Displaysperre, und nach der gewählten Frist. Die App-Sperre verbirgt die App; sie
  **verschlüsselt** deine Notizen **nicht**.

---

## 9. Wenn etwas schiefgeht

- **„Deine Einstellungen waren beschädigt und wurden zurückgesetzt“:** die App konnte ihre
  Einstellungen nicht lesen und hat neu begonnen. **Deine Notizen sind sicher.** Die Hub-Kopplung muss
  neu eingerichtet werden; der Hub erhält deine Notizen dann erneut.
- **Eine Notiz ist als *Konfliktkopie* markiert:** zwei Fassungen ihres Texts sind sich begegnet;
  siehe [Abschnitt 5](#5-wenn-zwei-geräte-dieselbe-notiz-ändern).
- **Eine Erinnerung kam nicht:** prüfe, ob Benachrichtigungen für NotesManager erlaubt sind und ob das
  Telefon ihr exakte Wecker erlaubt.
- Fragen und Ideen: *Einstellungen → Über → Feedback senden*.
