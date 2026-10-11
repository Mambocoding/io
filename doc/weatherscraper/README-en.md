# WeatherScraper — user guide

*English · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Written for WeatherScraper 0.1.135 (October 2026). Where this guide and the app disagree, the app is
right.

---

## 1. What WeatherScraper is

WeatherScraper shows a **14-day forecast** for the cities you choose. It has no forecast of its own
and names no weather site: **you** tell it where to read.

- **A forecast page you paste:** the address of a multi-day forecast page from a site you trust.
  The app reads its table of days.
- **A forecast service you configure:** the address of a forecast API you are allowed to use, read
  for a city by its coordinates.

A city can have both, so a page that changes its layout does not leave you without a forecast. The
source of every forecast is always named on screen, by the host you entered.

A new install is empty: no city, no address. A short wizard helps you set them up.

---

## 2. First start

The wizard asks, in order:

1. Which **sources** you want to use: pasted pages, a forecast service, or both.
2. The service **addresses**, if any: the forecast address, and the geocoding address used to find a
   city by its name. Leave a field blank to skip it; everything can be changed later in
   [Settings](app:settings).
3. Your **first city**.
4. Optionally, your **SyncHub** ([section 9](#9-synchub)).

Nothing is saved until you tap *Start*.

---

## 3. Adding cities

Open the menu and tap **+ Add a city**.

- **By name:** type at least two letters; matching places appear with their region. One tap adds the
  city. This needs a geocoding address in the settings.
- **From a page** (*Tools → Extract from a page*, marked experimental):
  1. Paste the **address** of the site's multi-day forecast page (not its home page) and tap
     **Analyse**. The app fetches the page once.
  2. Up to three candidate tables are previewed as forecast rows, each with a confidence: *Looks like
     a forecast*, *Not sure — check the preview*, *Probably wrong*. *Not the right table?* shows the
     next one.
  3. The preview says which daily figures it found (rain, wind, sun) and whether the site has **day
     pages**, which give the hours of a day when you open it.
  4. Name the city and tap **Add city**. If the name matches a place, its coordinates are kept: the
     forecast service takes over if the page stops working.

The extractor respects the site's `robots.txt`, identifies itself honestly, and fetches rarely. If a
page is built by JavaScript or refuses the request, it says so. *Advanced* lets you write the
selectors by hand. The site's terms are yours to respect.

In the menu, each city has a **heart** (your favourites, also shown on the hub's home page), a drag
handle to reorder, and **×** to remove it (its saved forecast is deleted).

---

## 4. Reading the forecast

The home screen shows the selected city. **Swipe sideways** or use the menu to switch city.

- **Three views**, from the overflow menu (⋮): **Now**, **7 days** (the default, cards with
  details) and **14 days** (a dense list). Above both lists, a **temperature chart** shows highs over
  lows.
- Each day reads: weekday and date, an illustration, low / high, then condition · chance of rain ·
  millimetres · wind. A figure the source did not give shows **—**: the app never invents one.
- **The status line** is always there: how old the forecast is, which source it came from (the host
  you entered), and the last failure if a refresh failed. A failed refresh never removes the
  forecast; it stays, labelled with its age.
- Tap a day for its **detail**: hours when the source has them, humidity, and the alert categories
  of the day.
- **Refresh:** pull down, or the refresh icon in the header.
- The **action bar** offers *Share* (a picture of the forecast) and, for a page city, *Open the
  source page*.

### 4.1 A city with two sources

When a city has both a page and coordinates, **Compare sources** (in *Settings*) shows one page per
source plus an **Average** page (mean temperatures, the worse condition of the two). Otherwise, the
**Preferred source** setting decides which source is used first; the other takes over when the first
fails.

---

## 5. Refreshing

- Every morning at 07:00, the app refreshes all your cities.
- When you open a city whose forecast is older than 30 minutes, it refreshes that city.
- **Refresh interval** (off by default) adds a refresh every 1, 3, 6 or 12 hours. You can keep
  background refreshes to Wi-Fi.
- At most two requests per refresh for a page city (the list, then today's page), with growing
  pauses after failures. A site is never hammered.

---

## 6. Alerts and official warnings

### 6.1 Alerts from your forecast

*Settings → Notifications → Alerts* (off by default) watches **today and tomorrow** of your stored forecasts
and tells you once per city, day and kind when one of six things is expected: **frost**, **heat**,
**heavy rain**, **strong wind**, **snow** or a **thunderstorm**. **Sensitivity** (*Low*, *Normal*,
*High*) moves the thresholds; each kind can be turned off, and each city too. A page city usually
gives temperatures and conditions only, so rain and wind alerts come mostly from the forecast
service. These alerts are worked out on the phone from your own forecast: they are not official.

### 6.2 Official warnings

If you enter a **warning feed address** (a feed of official warnings in the CAP format, *Settings →
API address*), the forecast screen shows the warnings that cover the city, quoted as issued, and can
notify them. The app is not an alerting channel: it refreshes on its own schedule, so the issuer's
own page is authoritative. Outside the feed's area, the app shows nothing rather than "no warnings".

---

## 7. Settings for the sources

In [Settings](app:settings):

- **Forecast model:** *Automatic* lets the service choose; five named models can be chosen instead.
  **Per-city model** overrides it for one city. A switch can draw the spread between models on the
  chart.
- **Preferred source** and **Compare sources** ([section 4.1](#41-a-city-with-two-sources)).
- **API address:** the forecast, geocoding and warning-feed addresses, each empty until you fill it.
- **Refresh interval** and mobile data ([section 5](#5-refreshing)).

---

## 8. Widget and car

- **Widget:** place it on the home screen and pick a city and a view; its size decides how much it
  shows. It shows the stored forecast and never fetches by itself.
- **In the car:** with the phone connected to a car's screen, pick a city, then read today and the
  following days, with the source and age in the header. Alerts stay on the phone.

---

## 9. SyncHub

If you run a **SyncHub** at home, the app can share its cities, hearts and settings with it.

1. Open **SyncHub** at the bottom of the menu. The app looks for the hub on your network, or you type
   its address.
2. In the hub's web interface, open **Settings → Devices → Pair a device** and scan the QR code with
   the app.

- **Accuracy** (in the menu) shows, per city with a temperature sensor declared on the hub, how far
  each source's forecast landed from what the sensor measured, by days ahead, over 30, 90 or 365
  days. The first figures come after about a week.
- The sync screen's *Send everything again* resends the app's data if the hub lost it.

---

## 10. When something goes wrong

- **"This page seems to be built by JavaScript":** the app reads only what the page sends; try
  another page of the site, or add the city by name.
- **"robots.txt disallows automated access":** the site asks robots not to read that page; the app
  obeys. Choose another source.
- **The forecast is old:** the status line says why the last refresh failed. The stored forecast
  stays until a refresh succeeds.
- **A figure shows —:** the source did not give it. That is not zero.
- Questions and ideas: *Settings → About → Send feedback*.
