<!-- Source: Mambocoding/FeedScraper, specs/SPEC-055-privacy-policy.md, section *The policy, verbatim — de*, at commit 82b5037 on dev. Copied verbatim (date filled in, contact linked, language bar added); the source is right if the two ever disagree. -->

# FeedScraper — Datenschutzerklärung

*[English](../) · [Français](../fr/) · Deutsch · [Español](../es/) · [Nederlands](../nl/)*

*Zuletzt aktualisiert: 2026-11-22*

FeedScraper ist ein Feed-Reader, der vollständig auf deinem Gerät läuft.

**Was erhoben wird: nichts.** Es gibt kein Konto und keine Registrierung. Die App sendet niemandem Nutzungsdaten,
Analysedaten, Absturzberichte oder eine Werbe-ID, und sie enthält keine Bibliothek, die das tun würde. Niemand, auch
nicht der Entwickler, kann sehen, was du liest.

**Was gespeichert wird, und wo.** Deine Abonnements, die daraus abgerufenen Artikel, welche davon du gelesen oder mit
einem Stern markiert hast, die zum Offline-Lesen gespeicherten Kopien und deine Einstellungen werden nur auf deinem Gerät
gespeichert, im eigenen privaten Speicher der App. Die App schaltet außerdem die Cloud-Sicherung des Systems für ihre
Daten ab, sodass auch auf diesem Weg nichts davon vom Gerät kopiert wird.

**Was dein Gerät verlässt.** Nur die folgenden Anfragen, und es gibt vier Arten:

1. **Die Feeds, die du abonniert hast.** Die App ruft jeden Feed von der Adresse ab, die du ihr gegeben hast. Wenn du
   einen Artikel öffnest, ihn zum Offline-Lesen speicherst oder die App das Bild eines Artikels anzeigen lässt, ruft sie
   diese Seite oder dieses Bild von der Website ab, auf die der Feed verweist. Diese Anfragen gehen an die Herausgeber der
   Feeds, die du gewählt hast, und jeder von ihnen sieht, was jede Webanfrage zeigt: die angefragte Adresse und die
   Netzwerkadresse, von der aus du sie gestellt hast.
2. **Ein Hub, den du gekoppelt hast, falls du einen gekoppelt hast.** Die Synchronisierung ist optional und aus, bis du
   sie einrichtest, und der Hub ist ein Rechner, den du selbst betreibst — dieses Projekt betreibt keinerlei Server. Wenn
   du einen koppelst, sendet ihm die App deine Abonnements, deine Gelesen-, Stern- und Gespeichert-Markierungen und deine
   Einstellungen und empfängt dasselbe von deinen anderen Geräten. Sie sendet **nicht** die auf dem Gerät gespeicherten
   Artikel und auch nicht ihr eigenes Protokoll darüber, welche Feeds nicht abgerufen werden konnten. Die Verbindung wird
   nur zu dem Rechner aufgebaut, den du gekoppelt hast, erkannt an einem Zertifikat, das du beim Koppeln bestätigt hast.
   Damit du deinen Hub findest, fragt der Kopplungsbildschirm die Geräte in deinem Heimnetz, ob dort ein Hub ist; diese
   Anfrage verlässt dein Heimnetz nicht, und du kannst stattdessen die Adresse des Hubs eingeben. Die Verbindung zum Hub
   selbst geht nie über die Adresse hinaus, die du gekoppelt hast.
3. **Ankündigungen, sofern du sie nicht abschaltest.** Etwa einmal am Tag, solange die App geöffnet ist, liest sie eine
   öffentliche Datei mit Ankündigungen aus dem öffentlichen Repository des Entwicklers. Die Anfrage ist anonym: kein
   Konto, kein Cookie und keine Kennung von dir oder deinem Gerät. Wie jede Webanfrage zeigt sie dem Host dieser Datei die
   Netzwerkadresse deines Geräts. *Ankündigungen erhalten* in der Liste der Ankündigungen unter *Einstellungen* stoppt
   sie; solange es aus ist, wird nichts angefragt.
4. **Ein Assistenzdienst, den du eingerichtet hast, falls du einen eingerichtet hast.** Der Assistent bleibt aus, bis du
   ihn einschaltest, akzeptierst, was er sendet, die Adresse eines Dienstes und deinen eigenen Schlüssel eingibst und ein
   Test gelingt. Danach, und nur wenn du bei einem Artikel auf *Zusammenfassen* oder *Übersetzen* tippst, sendet die App
   Titel und Text dieses Artikels sowie die Sprache, in der die App angezeigt wird, an die Adresse, die du eingegeben
   hast — sonst nichts, nie im Hintergrund. Dieser Dienst verarbeitet sie nach seinen eigenen Bedingungen und seiner
   eigenen Datenschutzerklärung, die du bei ihm akzeptiert hast, und rechnet direkt mit dir ab; der Entwickler erhält sie
   nie. Dein Schlüssel bleibt verschlüsselt auf diesem Gerät und wird nie gesichert oder synchronisiert.

Es gibt kein anderes Ziel.

Drei Dinge verlassen die App nur, wenn du es willst, und nur an eine App auf deinem Telefon: Das Teilen eines Artikels
übergibt seinen Titel und seine Adresse an die App, die du im Teilen-Menü des Systems wählst; das Öffnen eines Artikels
im Tab des In-App-Browsers übergibt seine Adresse an deinen Browser, der die Seite dann selbst abruft; und das Vorlesen
eines Artikels übergibt seinen Titel und Text an die auf deinem Telefon eingestellte Sprachausgabe, von denen manche
Online-Stimmen nutzen — eine Wahl, die in den Einstellungen deines Telefons getroffen wird, nicht in dieser App. Nichts
davon geht an den Entwickler.

**Berechtigungen, und wofür jede dient.** Internetzugriff, um Feeds abzurufen. Netzwerkstatus, um vor dem Herunterladen
von Bildern zu erkennen, ob du eine getaktete Verbindung nutzt. WLAN-Status und WLAN-Multicast, nur verwendet, um die
Hubs in deinem Heimnetz aufzulisten, während du einen koppelst oder einen umgezogenen suchst; die Eingabe der Adresse
funktioniert auch ohne sie. Zugriff auf das lokale Netzwerk, ab Android 17, angefragt, wenn eine Synchronisierung ihn zum
ersten Mal braucht, um deinen eigenen Hub in deinem Heimnetz zu erreichen; wenn du ihn verweigerst, bleiben alle Feeds
auf deinem Telefon und nur die Synchronisierung hält an. Benachrichtigungen, optional und nur für Feeds verwendet, über
die du informiert werden möchtest. Die Kamera, optional, wird nur in dem Moment angefragt, in dem du zum Koppeln eines
Hubs auf *Scannen* tippst, und ist nie nötig — du kannst dieselben Angaben von Hand eingeben. Wenn du die App-Sperre
einschaltest, bittet die App das System, deinen Fingerabdruck oder die Geräte-PIN zu prüfen; sie erhält oder speichert
keines von beiden.

**Deine Daten mitnehmen.** Die App kann deine Abonnements und Einstellungen in eine Datei an einem Ort deiner Wahl
exportieren. Sie wird nur geschrieben, wenn du darum bittest.

**Deine Daten löschen.** Das Deinstallieren der App löscht alles, was sie gespeichert hat. Es gibt nirgendwo sonst eine
Kopie, nach der du fragen müsstest.

**Kinder.** Die App richtet sich nicht an Kinder, und sie erhebt von niemandem etwas, in keinem Alter.

**Änderungen dieser Erklärung.** Wenn sich das Verhalten der App ändert, ändert sich dieser Text mit ihm, in derselben
Version, und das Datum oben ändert sich.

**Wer verantwortlich ist, und dein Beschwerderecht.** Verantwortlicher für diese App ist Mambocoding,
mambocoding@gmail.com. Da die App nichts erhebt und dem Entwickler nichts sendet, hat der Entwickler keine
personenbezogenen Daten über dich, die einzusehen, zu berichtigen oder zu löschen wären. Wenn du der Ansicht bist, dass
deine Daten rechtswidrig verarbeitet wurden, hast du das Recht, Beschwerde bei einer Datenschutz-Aufsichtsbehörde
einzulegen, insbesondere in dem Land, in dem du wohnst, in dem du arbeitest oder in dem der Verstoß nach deiner
Auffassung stattgefunden hat.

**Kontakt.** Fragen zu dieser Erklärung kannst du im [öffentlichen Issue-Tracker](https://github.com/Mambocoding/io/issues) des öffentlichen Repositorys des
Entwicklers, `Mambocoding/io`, stellen, das auf der Seite der App im Store verlinkt ist.
