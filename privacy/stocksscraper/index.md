<!-- Source: Mambocoding/StocksScraper, specs/SPEC-021-onboarding-and-about.md, canonical privacy_body wording (D10), at commit faa156b (pull request #163 to dev). Copied verbatim; the source is right if the two ever disagree. -->

# StocksScraper — Privacy policy

*Last updated: 2026-09-29*

StocksScraper collects no personal data. There is no account, no advertising, no analytics and no tracking of any kind, and this project runs no server.

Your watchlist, portfolio, settings and alert history are stored on this device. If Android's own device backup is switched on, it may copy them to your backup account; your API keys and a hub pairing are never included.

The app only contacts the addresses you enter yourself in Settings → Data sources. To fetch prices, charts, currency rates and news, it sends those services an instrument's symbol or ISIN, or a feed request — never a holding or an amount. An instrument page you set up there opens in your browser.

If you pair the app with a hub, that hub is a machine you run yourself, identified by a certificate you confirmed when pairing. The app sends it your watchlist, categories, alert rules, some settings and which articles you have read or saved — and your portfolio only if you switch on Sync my portfolio.

A backup, if you create one, is a file written to a folder you choose. It never leaves your device unless you move it yourself. A plain backup can be read by anyone who has the file and never contains your API keys; an encrypted backup needs your passphrase.

---

**Contact.** Questions about this policy can be raised on the [public issue tracker](https://github.com/Mambocoding/io/issues) of `Mambocoding/io`.
