# FeedScraper — Anleitung

*[English](README-en.md) · [Français](README-fr.md) · Deutsch · [Español](README-es.md) · [Nederlands](README-nl.md)*

Geschrieben für FeedScraper 0.1.252 (Oktober 2026). Wenn diese Anleitung und die App voneinander
abweichen, hat die App recht.

---

## 1. Was FeedScraper ist

FeedScraper ist ein **Feed-Reader**: du abonnierst die Feeds der Websites, denen du folgst (RSS, Atom,
RDF oder JSON Feed), und ihre neuen Artikel kommen auf dein Telefon.

- Alles wird auf dem Telefon abgerufen und gespeichert: kein Konto, kein Server von uns.
- Lesen, mit Stern markieren, für offline speichern, suchen und Neues im Hintergrund erhalten.
- Wenn du zu Hause einen **SyncHub** betreibst, können dir deine Feeds und dein Gelesenes auf andere
  Telefone und in die Weboberfläche des Hubs folgen
  ([Abschnitt 8](#8-mit-deinem-synchub-synchronisieren)). Ohne Hub ist die App ein einfacher Reader.

---

## 2. Feeds hinzufügen

- **Feed hinzufügen** (im Menü): füge die Adresse eines Feeds ein, oder einfach der Website — bietet
  die Seite mehrere Feeds an, wählst du einen. Der Titel wird aus dem Feed übernommen; ändere ihn,
  wenn du willst, und wähle eine Kategorie.
- **Aus einer Datei importieren** (OPML, die Standard-Abonnementliste, in den *Einstellungen*): holt
  die Feeds eines anderen Readers. Der Import fügt nur hinzu; er entfernt oder ordnet deine Feeds nie
  um. **In eine Datei exportieren** macht das Umgekehrte.
- **Feed aus einer Seite extrahieren** (*Werkzeuge*): für eine Website ohne Feed schlägt die App eine
  Regel vor, die die Artikel aus der Seite herausholt, und wendet sie bei jeder Aktualisierung an.
  Das ist experimentell.

---

## 3. Lesen

- **Ansichten** im Menü: **Alle Feeds**, **Favoriten** (markierte Artikel), **Gespeichert
  (offline)** und eine **Feeds**-Übersicht mit einer Schaltfläche pro Feed. Jeder Feed und jede
  Kategorie ist ebenfalls eine Ansicht.
- Die Liste bleibt still, während du liest: Artikel, die während eines Besuchs eintreffen, warten
  hinter einer Pille *neue Artikel* oben. Scrolle ans Ende, um ältere zu laden.
- **Wische** eine Zeile, um sie als gelesen oder ungelesen zu markieren oder sie mit Stern zu
  versehen. **Langes Drücken** wählt einen Artikel aus, und die Aktionsleiste zeigt, was du damit tun
  kannst.
- **Alle als gelesen markieren** leert eine Ansicht auf einmal.
- Öffne einen Artikel, um ihn zu lesen; wische oder nutze die Pfeile für den vorigen und den nächsten.
  Die Aktionsleiste bietet Stern, Teilen, Offline speichern und Im Browser öffnen. Textgröße und
  Zeilenabstand lassen sich einstellen.
- Die Lupe **sucht** in der aktuellen Ansicht; ein Tippen erweitert auf alle Feeds.
- Auf einem breiten Bildschirm stehen Liste und geöffneter Artikel nebeneinander.

---

## 4. Offline lesen

**Offline speichern** behält einen Artikel mit Text und Bildern, lesbar ohne Netz; **Feed offline
speichern** tut das für alle ungelesenen Artikel eines Feeds. Gespeicherte Artikel stehen unter
**Gespeichert (offline)**. Die *Einstellungen* zeigen, wie viel Platz sie belegen, können sie nach dem
Lesen mit einer Frist entfernen und Bilder aufs WLAN beschränken.

---

## 5. Feeds ordnen

- **Feeds und Kategorien bearbeiten** (im Menü) sortiert Feeds und Kategorien um, verschiebt Feeds
  zwischen Kategorien, führt Kategorien zusammen oder löscht sie.
- Einen Feed bearbeiten ändert seine Adresse, seinen Titel und seine Kategorie, deaktiviert ihn oder
  **kündigt das Abo**. *Artikel ausblenden, deren Titel enthält* blendet Artikel per Stichwort aus
  (ein Begriff pro Zeile); sie werden nicht gelöscht, und das Entfernen des Begriffs bringt sie zurück.
- Ein **Herz** an einem Feed macht ihn zum Favoriten; mit einem Hub nutzt der Hub es, um zu sagen, was
  neu ist.
- Ein Feed, der immer wieder scheitert, wird im Menü markiert, mit einem Link zu seinem
  **Abrufprotokoll**. Gibt es die Adresse eines Feeds nicht mehr, schlägt die App die Feeds vor, die
  die Website jetzt anbietet.

---

## 6. Aktualisierung und Benachrichtigungen

- Feeds aktualisieren sich im Hintergrund, laden nur, was sich geändert hat, und halten Abstand von
  Feeds, die scheitern. Die *Einstellungen* legen fest, wie oft, ob mobile Daten genutzt werden dürfen
  und ob beim Öffnen der App jeder Feed aktualisiert wird.
- Zieh in einer Ansicht nach unten, um sie sofort zu aktualisieren.
- **Benachrichtigungen bei neuen Artikeln** sind standardmäßig aus und werden pro Feed gewählt.
- **Gelesene Artikel löschen, die älter sind als** (standardmäßig aus) hält die Datenbank klein.

---

## 7. Einstellungen und Privatsphäre

In den [Einstellungen](app:settings): **Beim Start öffnen** (wo du aufgehört hast, die Feed-Übersicht
oder deine Favoriten), Anzeige, Aktualisierung, Benachrichtigungen, Offline-Speicher, Sicherungen und
die App-Sperre.

- Artikel werden vor der Anzeige bereinigt: kein Skript aus einem Artikel läuft je.
- Die **App-Sperre** (standardmäßig aus) verlangt Fingerabdruck oder Displaysperre; sie verbirgt, sie
  verschlüsselt nicht.
- *Sichern & wiederherstellen* speichert deine Feeds, Kategorien, den Lesestand und die Einstellungen
  in einer Datei und stellt sie wieder her.

---

## 8. Mit deinem SyncHub synchronisieren

Die Synchronisierung mit einem Hub ist das, was ein einmaliger Kauf freischaltet; alles andere ist
kostenlos.

1. Öffne **SyncHub** im Menü. Die App sucht den Hub in deinem Netz, oder du gibst seine Adresse ein.
2. Öffne in der Weboberfläche des Hubs **Einstellungen → Geräte → Gerät koppeln** und scanne den
   QR-Code mit der App.
3. Vergleiche den Fingerabdruck des Zertifikats, wenn du gefragt wirst: die App vertraut dem Hub erst,
   wenn du ihn bestätigst.

- Feeds, Kategorien, Herzen, Gelesen- und Stern-Status und Einstellungen reisen dann in beide
  Richtungen; der Hub ruft deine Feeds weiter ab, während dein Telefon schläft.
- Ändert sich das Zertifikat des Hubs, stoppt die Synchronisierung, bis du entscheidest. Nichts wird
  stillschweigend wieder vertraut.
- Ist der Hub lange nicht erreichbar, sagt dir die App das. Der Punkt im Menü zeigt den
  Synchronisierungsstand auf einen Blick.

---

## 9. Wenn etwas schiefgeht

- **„… wurde nicht aktualisiert — diagnostizieren“:** öffne das Abrufprotokoll des Feeds; es sagt,
  was die Website geantwortet hat.
- **„… weist uns immer wieder ab“:** die Website sperrt automatische Reader; höflich kann die App da
  nichts tun.
- **Ein Artikel zeigt kein Bild:** manche Websites verweigern Apps die Bilder; der Artikel lässt sich
  trotzdem lesen.
- **Die Synchronisierung stoppte nach einer Änderung am Hub:** vergleiche den neuen Fingerabdruck auf
  den Seiten des Hubs, bevor du ihm wieder vertraust.
- Fragen und Ideen: *Einstellungen → Über → Feedback senden*.
