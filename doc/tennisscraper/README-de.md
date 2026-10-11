# Tennis Scraper — Anleitung

*[English](README-en.md) · [Français](README-fr.md) · Deutsch · [Español](README-es.md) · [Nederlands](README-nl.md)*

Geschrieben für Tennis Scraper 0.1.140 (Oktober 2026). Wenn diese Anleitung und die App voneinander
abweichen, hat die App recht.

---

## 1. Was Tennis Scraper ist

Tennis Scraper verfolgt Profitennis im Einzel — die Touren der Männer und der Frauen — und
**benachrichtigt dich, wenn ein Spiel beginnt, dem du folgst**, während es läuft und wenn es endet.

- Alles läuft auf deinem Telefon: kein Konto, kein Server von uns. Die Benachrichtigungen berechnet
  das Telefon selbst.
- Die App bringt keine Datenadresse mit: **du** gibst die Adresse der Datenquelle ein, die du nutzt
  ([Abschnitt 8](#8-datenquelle-und-status)). Bis dahin bleiben die Bildschirme leer und sagen es.
- Du verfolgst **Spieler**, ganze **Turniere** ab einer Runde deiner Wahl oder ein einzelnes
  **Spiel**.
- **Ein Spiel, eine Benachrichtigung** jeder Art, egal aus wie vielen Gründen du es verfolgst.

---

## 2. Heute

**Heute** ist der Startbildschirm, aus Blöcken deiner Wahl: **Spiele**, **News**, **Rangliste** und
**Kalender**.

- Der Spiele-Block zeigt die Spiele deiner Favoriten und die verfolgten Spiele auf einer Zeitleiste,
  mit Tagestrennern: anstehende mit ihrer Uhrzeit, **live** mit Spielstand und pulsierendem Punkt,
  beendete mit dem Ergebnis. Ein Spiel zwischen zwei deiner Favoriten erscheint einmal.
- Tippe auf den Titel eines Blocks, um seinen Bildschirm zu öffnen; bearbeite die Seite, um Blöcke
  hinzuzufügen, zu entfernen oder umzusortieren.
- Der **Anti-Spoiler-Modus** (Menü ⋮) verbirgt auf Heute die News und jeden Spielstand und
  *Gewonnen* / *Verloren*, für ein Spiel, das du später schaust. Live-Zeilen behalten ihr *LIVE*.
- Zum Aktualisieren nach unten ziehen. Heute aktualisiert sich auch im Hintergrund und öffnet sich so
  mit frischen Daten.
- Das Menü ⋮ filtert auch nach Tour: **Alle** oder eine der beiden Touren. Der Filter gilt auf jedem
  Bildschirm und ändert nie, was heruntergeladen wird.

---

## 3. Spieler und Verfolgen

- **Spieler** zeigt deine Favoriten, nach Tour gruppiert. Tippe ins Suchfeld, um jeden Spieler zu
  finden; der Stern fügt einen Favoriten hinzu oder entfernt ihn.
- Die **Glocke** eines Favoriten schaltet ihn stumm: er bleibt Favorit, aber seine Spiele melden sich
  nicht mehr (außer ein anderer Grund, dem Spiel zu folgen, gilt weiter).
- **Dieses Turnier verfolgen** (über seinen Kopf in Spiele oder Kalender): wähle ab welcher Runde —
  Hauptfeld, Viertelfinale, Halbfinale oder Finale. Jedes Spiel des Turniers ab dieser Runde meldet
  sich dann.
- **Dieses Spiel verfolgen** (im Detail eines Spiels): seine Benachrichtigungen kommen, auch wenn du
  keinem der beiden Spieler folgst. Das Verfolgen endet von selbst nach dem Spiel.

---

## 4. Spiele, Kalender, Tableaus, Rangliste

- **Spiele** listet die Spiele eines Tages nach Turnier, mit Qualifikanten, Kategorie und Runde.
  Tippe auf ein Spiel für sein **Detail**: Spieler, Spielstand je Satz, Runde und die Aktionen unten.
- **Kalender** listet die Turniere nach Woche; öffne eines für sein **Tableau**, Runde für Runde.
  *Offizielle Website* öffnet die eigene Seite des Turniers, wenn die App sie kennt.
- **Rangliste** zeigt die aktuelle Rangliste jeder Tour; tippe auf einen Spieler für sein Detail.
- Im Detail eines Spiels:
  - **Teilen** sendet das Spiel als Text;
  - **Zum Kalender hinzufügen** (anstehendes Spiel mit Startzeit) übergibt es deiner Kalender-App;
  - **Ansehen** (live oder kurz vor Beginn) öffnet das Spiel auf einer Suchseite für Übertragungen —
    nur wenn du in den [Einstellungen](app:settings) eine *Adresse der Ansehen-Suche* angegeben hast.

---

## 5. Benachrichtigungen

[Einstellungen](app:settings) → *Benachrichtigungen* enthält jeden Schalter:

- **Spielmeldungen:** *Beginnt bald* (an, mit der Vorlaufzeit), *Spielbeginn* (an), *Live-Spielstand*
  (aus) und *Ergebnis* (an).
- **Jeden Tag:** eine **Tageszusammenfassung** der Spiele deiner Favoriten, eine Benachrichtigung pro
  Spieler, zur gewählten Uhrzeit; und ein Hinweis, wenn ein verfolgtes Turnier beginnt.
- **Ruhezeiten** (standardmäßig aus, eingeschaltet 23:00–08:00): Meldungen, die hineinfallen, werden
  verworfen.
- **Stummgeschaltete Spieler** listet die stummgeschalteten Favoriten.

Ein Tippen auf eine Benachrichtigung öffnet das Spiel.

---

## 6. News

Gibst du eine **Adresse des News-Feeds** ein (ein RSS- oder Atom-Feed, in den *Einstellungen*), listet
**News** die neuesten Artikel, und Heute kann *News zu deinen Favoriten* zeigen. **Alle als gelesen
markieren** steht in der Aktionsleiste. Ohne Adresse sind die News ganz verborgen und es wird nichts
heruntergeladen.

---

## 7. Widget und Auto

- **Widget:** bis zu drei verfolgte Spiele des Tages auf dem Startbildschirm — live zuerst, dann
  anstehende, dann beendete. Ein Tippen öffnet Heute.
- **Im Auto:** mit dem Telefon am Bildschirm eines Autos lassen sich Spielmeldungen vorlesen und die
  Favoriten und der Spielplan des Tages durchsehen.

---

## 8. Datenquelle und Status

- *Einstellungen → Datenquelle* wählt, woher die Spiele kommen: eine **Ergebnisdienst**-Quelle (kein
  Schlüssel) oder eine **schlüsselbasierte Spielliste** (Schlüssel nötig), jede über eine Adresse,
  die du eingibst. Wer eine Adresse eingibt, verantwortet die Bedingungen dieses Dienstes. Favoriten
  werden je Quelle gespeichert.
- *Einstellungen → Status* sagt, was die App zuletzt getan hat: die genutzte Quelle, der letzte
  erfolgreiche und der letzte gescheiterte Abruf, und die Zwischenspeicher. Hier schaust du nach,
  wenn eine Benachrichtigung nicht kam.

---

## 9. Die App sichern

*Einstellungen → Sichern & wiederherstellen* speichert deine Favoriten, Verfolgungen und
Einstellungen in einer Datei und stellt sie auf einem neuen Telefon wieder her.

---

## 10. Wenn etwas schiefgeht

- **Eine Benachrichtigung kam nicht:** prüfe unter *Einstellungen → Status* den letzten Abruf, ob die
  Meldung eingeschaltet ist, ob der Spieler nicht stummgeschaltet ist, ob gerade Ruhezeit war, und ob
  das Telefon Benachrichtigungen erlaubt und die App nicht schlafen legt.
- **Ein Live-Spielstand scheint festzuhängen:** gezeigt wird der letzte Stand, den die Quelle lieferte;
  zum Aktualisieren nach unten ziehen.
- **Keine News:** die Adresse des News-Feeds ist leer, oder der Feed hat nicht geantwortet.
- Fragen und Ideen: *Einstellungen → Über → Feedback senden*.
