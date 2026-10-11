# FlightScraper — user guide

*English · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Written for FlightScraper 0.1.79 (October 2026). Where this guide and the app disagree, the app is
right.

---

## 1. What FlightScraper is

FlightScraper watches **one airport** and keeps a **log of its movements**: every landing and
take-off it observes, with callsign, registration, aircraft type, operator and time. **Watch rules**
can notify you when an aircraft you care about comes.

- It reads **ADS-B positions** — what aircraft broadcast themselves — not a timetable. That is why it
  also sees flights no schedule lists: military, government, ferry, diverted or test flights.
- A movement is an **inference** from positions, so each one carries its confidence: *observed*,
  *inferred* or *uncertain*. A missing field shows **—**, never a guess.
- It shows only what is broadcast around one airport. It is not a flight tracker and not a
  surveillance tool.

The app names no data service: **you** give it the address of a feed.

---

## 2. Getting started

1. **Choose your airport:** *Airports* in the menu → search by name, city or code. The airport book
   ships with the app and works offline; it fills the coordinates, elevation and time zone for you.
   Set the **ring radius** (how far around the airport to look, in km). Several airports can be
   saved; exactly one is watched.
2. **Enter a feed:** [Settings](app:settings) → *Feed*. Paste the address of an ADS-B feed you are
   allowed to use (a community aggregator, or your own receiver). Where the feed takes a circle, use
   `{lat}`, `{lon}` and `{radius_nm}`: the app fills them in. **Test** fetches once and says how many
   aircraft came back.
3. Wait two polls: the **first poll only records what is already there**; movements appear from the
   second poll on.

---

## 3. The movements log

**Movements** is the home screen: newest first, grouped by day.

- Each row: an arrow (arrival or departure), the local time, callsign, type designator and
  description, registration, the rules it matched, and a confidence mark.
- The overflow menu (⋮) filters **Arrivals / Departures / All**, **shows or hides unmatched**
  movements, sorts, and refreshes. The magnifier searches the log.
- **The status line** above the list says when the last successful poll was and how many aircraft
  were in the ring, or why the last poll failed. A failed poll never removes anything.
- Tap a movement for its **detail**: identity, times, confidence with a sentence explaining it, the
  rules it matched, a summary of its track, and **this airframe here** — how often it came before.
- The detail's action bar: **Share** (as text), **Open externally** in a tracker of your choice
  ([section 7](#7-links-to-a-tracker)), **Delete**.

---

## 4. Live and Map

- **Live** lists the aircraft in the ring right now, with distance and altitude, refreshed while the
  screen is open. Its **Expected** section shows aircraft closing on the airport — a prediction,
  labelled, given as a range, and gone once it no longer holds.
- **Map** draws the same aircraft where they are, around the airport and its ring. A background map
  appears only if you enter a map-tile address in *Settings → Map tile source*; the map works without it.

Live and Map poll only while they are on screen.

---

## 5. Watch rules and notifications

**Watch rules** decide which movements matter to you.

- A rule combines criteria: an exact **type** (`A332`), a **type family** (a prefix), **military**,
  a **callsign prefix**, a **registration**, words in the **description** or the **operator**, a
  **first visit** of this airframe or of this type, a **squawk** code. *All* or *any* of them must
  hold.
- Choose arrivals, departures or both, and an importance. Test a rule against the log before it
  alerts: the screen shows which past movements it would have matched.
- **Notifications** are off until you turn them on (*Settings → Notifications*). You are told
  **once** per aircraft, kind and day, whatever the number of rules that match.
- **Quiet hours** (22:00–07:00 at the airport by default) hold notifications until morning; a rule of
  high importance can ignore them.
- A rule can also warn you when a matching aircraft is **inbound**, before it lands.

---

## 6. Polling: how often the app looks

- While Live, Map or Active watch is open: every minute by default (never more often than every 30
  seconds). After failures the app waits longer — 1, 2, 4, then 8 minutes.
- In the background: about every 15 minutes, which still catches an arrival, up to 15 minutes late.
- **Polling schedule** (*Settings → Notifications*): during hours you choose, the background polls
  in short bursts instead.
- **Active watch:** for an evening, keep polling at the foreground pace with the screen off, for a
  duration you set. A notification shows while it runs, with a *Stop* button.

---

## 7. Links to a tracker

FlightScraper names no tracker. In *Settings → Links*, add the address templates of the trackers
you use, with placeholders the app fills from the movement (registration, callsign, hex code…). The
first link is the default for *Open externally*. The app never fetches these addresses itself.

---

## 8. Timetable (experimental)

*Tools → Timetable* shows the watched airport's own arrivals and departures board, read from pages
whose addresses you paste. It stays **beside** the log, never in it: nothing it reads becomes a
movement or triggers an alert. Rows the log probably saw are flagged.

---

## 9. Your data

- *Settings → Data → Back up & restore* saves the log, airports, rules, links and settings into a
  file, and restores it.
- *Settings → Log* sets how long movements are kept (forever by default) and **exports the log** as
  a spreadsheet file (CSV).

---

## 10. When something goes wrong

- **"No feed configured":** enter a feed address ([section 2](#2-getting-started)).
- **"The feed is rate-limiting this app":** the feed asks the app to slow down; it backs off by
  itself. Choose a longer interval if it keeps happening.
- **Nothing appears after the first poll:** normal — movements start with the second poll.
- **A movement says *uncertain*:** the track had gaps; the app says what it saw, no more.
- **Notifications do not come:** check that they are on in the app, allowed by the phone, and that
  you are not in quiet hours. A phone's battery saver can delay background polls: *Settings* has a
  row to exempt the app.
- Questions and ideas: *Settings → About → Send feedback*.
