<!-- Source: Mambocoding/FeedScraper, specs/SPEC-055-privacy-policy.md, section *The policy, verbatim — nl*, at commit 82b5037 on dev. Copied verbatim (date filled in, contact linked, language bar added); the source is right if the two ever disagree. -->

# FeedScraper — Privacybeleid

*[English](../) · [Français](../fr/) · [Deutsch](../de/) · [Español](../es/) · Nederlands*

*Laatst bijgewerkt: 2026-11-22*

FeedScraper is een feedlezer die volledig op je apparaat draait.

**Wat er wordt verzameld: niets.** Er is geen account en geen registratie. De app stuurt niemand gebruiksgegevens,
analyses, crashrapporten of een advertentie-ID, en bevat geen bibliotheek die dat zou doen. Niemand, ook de ontwikkelaar
niet, kan zien wat je leest.

**Wat er wordt opgeslagen, en waar.** Je abonnementen, de artikelen die daaruit zijn opgehaald, welke je hebt gelezen of
met een ster hebt gemarkeerd, de kopieën die je hebt bewaard om offline te lezen en je instellingen worden alleen op je
apparaat opgeslagen, in de eigen privéopslag van de app. De app schakelt ook de cloudback-up van het systeem uit voor
haar gegevens, zodat er ook langs die weg niets van het apparaat wordt gekopieerd.

**Wat je apparaat verlaat.** Alleen de verzoeken hieronder, en er zijn vier soorten:

1. **De feeds waarop je bent geabonneerd.** De app haalt elke feed op van het adres dat je hebt opgegeven. Als je een
   artikel opent, het bewaart om offline te lezen of de app de afbeelding van een artikel laat tonen, haalt ze die pagina
   of afbeelding op van de site waarnaar de feed verwijst. Die verzoeken gaan naar de uitgevers van de feeds die je hebt
   gekozen, en elk van hen ziet wat elk webverzoek laat zien: het gevraagde adres en het netwerkadres van waaruit je het
   deed.
2. **Een hub die je hebt gekoppeld, als je er een hebt gekoppeld.** Synchronisatie is optioneel en staat uit totdat je
   die instelt, en de hub is een machine die je zelf beheert — dit project heeft geen enkele server. Als je er een
   koppelt, stuurt de app hem je abonnementen, je markeringen voor gelezen, met ster en bewaard, en je instellingen, en
   ontvangt ze hetzelfde van je andere apparaten. Ze stuurt **niet** de artikelen die op het apparaat zijn bewaard, en ook
   niet haar eigen overzicht van welke feeds niet konden worden opgehaald. De verbinding wordt alleen gemaakt met de
   machine die je hebt gekoppeld, herkend aan een certificaat dat je bij het koppelen hebt bevestigd. Om je te helpen je
   hub te vinden, vraagt het koppelscherm de apparaten in je thuisnetwerk of er een hub is; dat verzoek verlaat je
   thuisnetwerk niet, en je kunt in plaats daarvan het adres van de hub typen. De hub zelf bereiken gaat nooit verder dan
   het adres dat je hebt gekoppeld.
3. **Aankondigingen, tenzij je ze uitschakelt.** Ongeveer één keer per dag, terwijl de app open is, leest ze een openbaar
   bestand met aankondigingen uit de openbare repository van de ontwikkelaar. Het verzoek is anoniem: geen account, geen
   cookie en geen kenmerk van jou of je apparaat. Zoals elk webverzoek toont het het netwerkadres van je apparaat aan de
   host van dat bestand. *Aankondigingen ontvangen*, in de lijst met aankondigingen onder *Instellingen*, stopt het;
   zolang het uit staat, wordt er niets opgevraagd.
4. **Een assistentdienst die je hebt ingesteld, als je er een hebt ingesteld.** De assistent staat uit totdat je hem
   inschakelt, accepteert wat hij verstuurt, het adres van een dienst en je eigen sleutel invoert, en een test slaagt.
   Daarna, en alleen als je bij een artikel op *Samenvatten* of *Vertalen* tikt, stuurt de app de titel en tekst van dat
   artikel, en de taal waarin de app wordt getoond, naar het adres dat je hebt ingevoerd — niets anders, nooit op de
   achtergrond. Die dienst verwerkt ze volgens zijn eigen voorwaarden en privacybeleid, die je bij hem hebt
   geaccepteerd, en brengt je rechtstreeks kosten in rekening; de ontwikkelaar ontvangt ze nooit. Je sleutel blijft
   versleuteld op dit apparaat en wordt nooit in een back-up opgenomen of gesynchroniseerd.

Er is geen andere bestemming.

Drie dingen verlaten de app alleen als jij erom vraagt, en alleen naar een app op je telefoon: een artikel delen geeft de
titel en het adres door aan de app die je kiest in het deelmenu van het systeem; een artikel openen in het tabblad van
de ingebouwde browser geeft het adres door aan je browser, die de pagina daarna zelf ophaalt; en een artikel laten
voorlezen geeft de titel en tekst door aan de tekst-naar-spraakengine die op je telefoon is ingesteld, waarvan sommige
online stemmen gebruiken — een keuze die je maakt in de instellingen van je telefoon, niet in deze app. Geen ervan gaat
naar de ontwikkelaar.

**Machtigingen, en waarvoor elk dient.** Internettoegang, om feeds op te halen. Netwerkstatus, om te weten of je een
verbinding met datalimiet gebruikt voordat er afbeeldingen worden gedownload. Wifi-status en wifi-multicast, alleen
gebruikt om de hubs in je thuisnetwerk op te sommen terwijl je er een koppelt of er een zoekt die is verhuisd; het adres
typen werkt ook zonder. Toegang tot het lokale netwerk, op Android 17 en later, gevraagd wanneer een synchronisatie die
voor het eerst nodig heeft, om je eigen hub in je thuisnetwerk te bereiken; als je die weigert, blijven alle feeds op je
telefoon en stopt alleen de synchronisatie. Meldingen, optioneel en alleen gebruikt voor feeds waarover je op de hoogte
wilt worden gehouden. De camera, optioneel, wordt alleen gevraagd op het moment dat je op *Scannen* tikt om een hub te
koppelen, en is nooit nodig — je kunt dezelfde gegevens met de hand typen. Als je de app-vergrendeling inschakelt, vraagt
de app het systeem je vingerafdruk of de pincode van het apparaat te controleren; ze ontvangt of bewaart geen van beide.

**Je gegevens meenemen.** De app kan je abonnementen en instellingen exporteren naar een bestand, op een plek die je zelf
kiest. Het wordt alleen geschreven als je erom vraagt.

**Je gegevens verwijderen.** De app verwijderen wist alles wat ze heeft opgeslagen. Er bestaat nergens anders een kopie
waar je om zou moeten vragen.

**Kinderen.** De app is niet gericht op kinderen, en verzamelt van niemand iets, van welke leeftijd ook.

**Wijzigingen in dit beleid.** Als het gedrag van de app verandert, verandert deze tekst mee, in dezelfde versie, en
verandert de datum hierboven.

**Wie verantwoordelijk is, en je recht om een klacht in te dienen.** De verwerkingsverantwoordelijke voor deze app is
Mambocoding, mambocoding@gmail.com. Omdat de app niets verzamelt en niets naar de ontwikkelaar stuurt, heeft de
ontwikkelaar geen persoonsgegevens over jou om in te zien, te corrigeren of te wissen. Als je vindt dat je gegevens
onrechtmatig zijn verwerkt, heb je het recht een klacht in te dienen bij een toezichthoudende autoriteit voor
gegevensbescherming, met name in het land waar je woont, waar je werkt of waar volgens jou de inbreuk heeft
plaatsgevonden.

**Contact.** Vragen over dit beleid kun je stellen in de [openbare issuetracker](https://github.com/Mambocoding/io/issues) van de openbare repository van de
ontwikkelaar, `Mambocoding/io`, waarnaar wordt gelinkt vanaf de pagina van de app in de store.
