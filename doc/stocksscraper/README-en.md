# StocksScraper — user guide

*English · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Written for StocksScraper 0.2.175 (October 2026). Where this guide and the app disagree, the app is
right.

---

## 1. What StocksScraper is

StocksScraper follows a **watchlist** — stocks, ETFs, commodities and crypto — and **notifies you
when one moves** by ±5 % (or the threshold you choose). It is for personal use: everything is worked
out on your phone, with no server and no account.

- The **watchlist** is free, whole and unlimited.
- The **portfolio** — what you own, what it is worth, whether you are up — is the premium part, a
  one-time purchase. It is visible, with a sparkle, before you have it.
- No price source is built in: **you** give the app the addresses of the sources you use.

---

## 2. Data sources

[Settings](app:settings) → *Data sources* holds one address per **role**, each named for the shape
of what it answers: a keyless chart series (the main source), a quote snapshot and a time series (both
need a key you enter), a CSV quote and a coin price. A role with no address is dormant.

- Each kind of instrument has its own **fallback chain**: if the first source fails, the next one is
  asked. You never have to choose by hand.
- *Status* on the same screen says which source answered last and what the chain is doing.
- With no source at all, the watchlist says so instead of showing errors on every row.
- Whoever enters an address answers for that service's terms.

---

## 3. The watchlist

- **Add** an instrument with **+** (or *Search / add* in the menu): search by name or ticker; local
  listings are found too.
- **Categories:** group your favourites under your own headings, fold them, and drag them into order
  (*Reorder*).
- Each row shows the instrument's kind, its price, and — your choice in the overflow menu (⋮) — its
  figures or a trend line. A **dot** says whether the market is open: a live price or a frozen one.
- When the app opens, it shows the last known prices at once, dimmed and dated, then refreshes them.
- Tap an instrument for its **detail**: a price chart with several periods, the market status, its
  news, links, and its own alerts.
- The **heart** on an instrument chooses whether it appears on your SyncHub's home page.

---

## 4. Alerts

- An alert comes when an instrument moves by the **threshold** (5 % by default) against the previous
  close. The app checks every hour by default, in the background.
- *Settings → Notifications* sets the threshold, how often to check, how many alerts per instrument
  per day (one by default), an optional **weekly** move alert (off by default), and **Silence
  overnight**: an alert that falls in the window is shown after it ends, if it still stands.
- On an instrument's **Alerts**: its own threshold, **price levels** (fire once when crossed), and
  **Mute** for 1 day, 1 week or until you turn it back on.
- **Alerts** in the menu answers *what did I miss?*: every alert that fired, across the watchlist,
  newest first; the overflow menu filters price levels or percent moves.
- An alert is about today's session and says when the move happened. Tapping it opens the
  instrument.

---

## 5. Portfolio (premium)

- **Positions:** what you hold, valued in one **reference currency** (*Settings → Portfolio*), with
  gain per line and in total, and a value curve over the period you choose.
- **A position is its transactions:** open a position to add buys, sells and dividends; quantity and
  average cost follow from them.
- **Cash** balances and **sub-portfolios** (one per account, say): the title switches between them.
- **Investment plan:** a standing buy order — weekly, monthly, twice a month or quarterly — posts its
  own buys on the planned days.
- **Import / export:** paste or pick a list of holdings (CSV), or import a bank's statement — a
  holdings snapshot or a dated journal — whose format is recognised by itself.
- The portfolio is never sent anywhere unless you turn on *Sync my portfolio*
  ([section 7](#7-synchub)).

---

## 6. News and widget

- **News** gathers articles about your watchlist; an instrument's detail shows its own. Read, star,
  save for offline reading, or open the original.
- The **widget** shows your watchlist on the home screen, from the last known prices; it never
  fetches by itself.

---

## 7. SyncHub

If you run a **SyncHub** at home, the app keeps your watchlist, categories, alerts and settings the
same on several phones and in the hub's web interface.

1. Open **SyncHub** in the menu. The app looks for the hub on your network, or you type its address.
2. In the hub's web interface, open **Settings → Devices → Pair a device** and scan the QR code. The
   app trusts the hub only once its certificate's fingerprint is confirmed.

- The **portfolio** travels only if you turn on **Sync my portfolio** (premium), after a
  confirmation.
- **Send everything again** refills a hub that lost its data.
- If the hub cannot be reached for a long time, the app tells you.

---

## 8. Security and backups

- *Settings → Security → App lock*: protect the whole app, or only the portfolio, with your
  fingerprint, face or screen lock. The lock hides; it does **not** encrypt.
- *Settings → Back up & restore* saves the watchlist, alerts and settings into a file — the portfolio
  only if you tick it — and restores them. API keys never go into a plain backup.

---

## 9. When something goes wrong

- **"No data source configured":** enter at least the main source's address
  ([section 2](#2-data-sources)).
- **A price looks old:** the dot and the age line say whether the market is closed or the source did
  not answer; *Data sources → Status* says which source answered last.
- **An alert did not come:** check the threshold and the per-day count, whether the instrument is
  muted, the overnight silence, and that the phone allows the app's notifications.
- Questions and ideas: *Settings → About → Send feedback*.
