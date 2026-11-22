<!-- Source: Mambocoding/FeedScraper, specs/SPEC-055-privacy-policy.md, section *The policy, verbatim*, at commit 82b5037 on dev. Copied verbatim (date filled in, contact linked, language bar added); the source is right if the two ever disagree. -->

# FeedScraper — Privacy policy

*English · [Français](fr/) · [Deutsch](de/) · [Español](es/) · [Nederlands](nl/)*

*Last updated: 2026-11-22*

FeedScraper is a feed reader that runs entirely on your device.

**What is collected: nothing.** There is no account and no sign-up. The application sends no
usage data, no analytics, no crash reports and no advertising identifier to anyone, and it
contains no library that would do so. Nobody, including the developer, can see what you read.

**What is stored, and where.** Your subscriptions, the articles fetched from them, which ones
you have read or starred, the copies you saved to read offline, and your settings are stored on
your device only, in the application's own private storage. The application also switches off
the system's cloud backup for its data, so none of it is copied off the device that way either.

**What leaves your device.** Only the requests below, and there are four kinds:

1. **The feeds you subscribed to.** The application fetches each feed from the address you gave
   it. When you open an article, save it to read offline, or have the application show an
   article's picture, it fetches that page or image from the site the feed points at. Those
   requests go to the publishers whose feeds you chose, and each of them sees what any web
   request shows them: the address requested, and the network address you made it from.
2. **A hub you paired, if you paired one.** Syncing is optional and off until you set it up, and
   the hub is a machine you run yourself — this project operates no server of any kind. When you
   pair one, the application sends it your subscriptions, your read, starred and saved marks,
   and your settings, and receives the same from your other devices. It does **not** send the
   articles it has saved on the device, nor its own record of which feeds failed to fetch. The
   connection is made only to the machine you paired, identified by a certificate you confirmed
   when you paired it. To help you find your hub, the pairing screen asks the devices on your home network whether a
   hub is there; the request does not leave your home network, and you can type the hub's address instead. Reaching
   the hub itself never goes further than the address you paired.
3. **Announcements, unless you turn them off.** About once a day, while the application is open, it reads a public
   file of announcements from the developer's public repository. The request is anonymous: no account, no cookie and
   no identifier of you or your device. Like any web request it shows your device's network address to the host of that
   file. *Receive announcements*, in the announcements list under *Settings*, stops it; nothing is requested while it is
   off.
4. **An assistant service you set up, if you set one up.** The assistant is off until you turn it on, accept what
   it sends, enter the address of a service and your own key, and a test succeeds. After that, and only when you
   tap *Summarise* or *Translate* on an article, the application sends that article's title and text, and the
   language the application is shown in, to the address you entered — nothing else, never in the background. That
   service handles them under its own terms and privacy policy, which you accepted with it, and bills you
   directly; the developer never receives them. Your key stays on this device, encrypted, and is never backed up
   or synced.

There is no other destination.

Three things leave the application only when you ask, and only to an app on your phone: sharing an article hands its
title and address to the app you pick in the system's share sheet; opening an article in the in-app browser tab hands
its address to your browser, which then fetches the page itself; and reading an article aloud hands its title and text
to the text-to-speech engine set on your phone, some of which use online voices, a choice made in your phone's
settings, not in this application. None of them goes to the developer.

**Permissions, and what each is for.** Internet access, to fetch feeds. Network state, to tell
whether you are on a metered connection before downloading images. Wi-Fi state and Wi-Fi multicast, used only to
list the hubs on your home network while you pair one or look for one that moved; typing the address works without
them. Local network access, on Android 17 and later, asked the first time a sync needs it, to reach your own hub on
your home network; refusing it keeps every feed on your phone and only stops syncing. Notifications, which are
optional and used only for feeds you have asked to be told about. The camera, which is optional,
is requested only at the moment you tap *Scan* to pair a hub, and is never needed — you can type
the same details by hand. If you switch on the app lock, the application asks the system to
verify your fingerprint or device PIN; it never receives or stores either.

**Taking your data with you.** The application can export your subscriptions and settings to a
file, in a location you choose. It is written only when you ask for it.

**Deleting your data.** Uninstalling the application deletes everything it stored. There is no
copy anywhere else to ask about.

**Children.** The application is not directed at children, and it collects nothing from anyone,
of any age.

**Changes to this policy.** If the application's behaviour changes, this text changes with it,
in the same release, and the date above changes.

**Who is responsible, and your right to complain.** The controller responsible for this application is
Mambocoding, mambocoding@gmail.com. Because the application collects nothing and sends nothing to the developer,
the developer holds no personal data about you to access, correct or erase. If you believe your data has been
handled unlawfully, you have the right to lodge a complaint with a data protection supervisory authority, in
particular in the country where you live, where you work, or where you believe the infringement took place.

**Contact.** Questions about this policy can be raised on the [public issue tracker](https://github.com/Mambocoding/io/issues) of the
developer's public repository, `Mambocoding/io`, which is linked from the application's page in the
store.
