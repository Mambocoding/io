<!-- Source: Mambocoding/FeedScraper, specs/SPECPrivacyPolicy.md, section 3, at commit 16c2750 on dev. Copied verbatim (date filled in, contact linked); the source is right if the two ever disagree. -->

# FeedScraper — Privacy policy

*Last updated: 2026-09-27*

FeedScraper is a feed reader that runs entirely on your device.

**What is collected: nothing.** There is no account and no sign-up. The application sends no
usage data, no analytics, no crash reports and no advertising identifier to anyone, and it
contains no library that would do so. Nobody, including the developer, can see what you read.

**What is stored, and where.** Your subscriptions, the articles fetched from them, which ones
you have read or starred, the copies you saved to read offline, and your settings are stored on
your device only, in the application's own private storage. The application also switches off
the system's cloud backup for its data, so none of it is copied off the device that way either.

**What leaves your device.** Only requests you asked for, and there are three kinds:

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
   when you paired it.
3. **Nothing else.** There is no third destination.

**Permissions, and what each is for.** Internet access, to fetch feeds. Network state, to tell
whether you are on a metered connection before downloading images. Notifications, which are
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

**Contact.** Questions about this policy can be raised on the [public issue tracker](https://github.com/Mambocoding/io/issues) of the
developer's public repository, `Mambocoding/io`, which is linked from the application's page in the
store.
