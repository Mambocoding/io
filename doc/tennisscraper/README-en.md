# Tennis Scraper — user guide

*English · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Written for Tennis Scraper 0.1.140 (October 2026). Where this guide and the app disagree, the app is
right.

---

## 1. What Tennis Scraper is

Tennis Scraper follows professional singles tennis — the men's and women's tours — and **notifies
you when a match you follow starts**, while it is played and when it ends.

- Everything runs on your phone: no account, no server of ours. Notifications are worked out by the
  phone itself.
- The app ships no data address: **you** enter the address of the data source you use
  ([section 8](#8-data-source-and-status)). Until then, the screens stay empty and say so.
- You follow **players**, whole **tournaments** from a round you choose, or a single **match**.
- **One match, one notification** of each kind, however many reasons you have to follow it.

---

## 2. Today

**Today** is the home screen, made of blocks you choose: **matches**, **news**, **rankings** and the
**calendar**.

- The matches block shows your favourites' and followed matches in one timeline, with day
  separators: upcoming with their time, **live** with the score and a pulsing dot, finished with the
  result. A match between two of your favourites appears once.
- Tap a block's title to open its screen; edit the page to add, remove or reorder blocks.
- **Anti-spoiler mode** (overflow menu ⋮) hides the news and every score and *Won* / *Lost* on Today,
  for a match you will watch later. Live rows keep their *LIVE* mark.
- Pull down to refresh. Today also refreshes itself in the background, so it opens on fresh data.
- The overflow menu also filters by tour: **All**, or one of the two tours. The filter applies on
  every screen and never changes what is downloaded.

---

## 3. Players and following

- **Players** shows your favourites, grouped by tour. Type in the search field to find any player;
  the star adds or removes a favourite.
- A favourite's **bell** mutes it: it stays a favourite, but its matches no longer notify (unless
  another reason you follow the match still holds).
- **Follow a tournament** (from its header in Matches or Calendar): choose from which round — main
  draw, quarter-finals, semi-finals or the final. Every match of that tournament from that round then
  notifies.
- **Follow this match** (on a match's detail): its alerts come even if you follow neither player. The
  follow expires by itself after the match.

---

## 4. Matches, calendar, draws, rankings

- **Matches** lists a day's matches by tournament, with qualifiers, tier and round. Tap a match for
  its **detail**: players, score by set, round, and the actions below.
- **Calendar** lists the tournaments by week; open one for its **draw**, round by round. *Official
  site* opens the tournament's own page when the app knows it.
- **Rankings** shows each tour's current ranking; tap a player for their detail.
- On a match's detail:
  - **Share** sends the match as text;
  - **Add to calendar** (upcoming match with a start time) hands it to your calendar app;
  - **Watch** (live or about to start) opens the match on a streaming search page — only if you set a
    *Watch search address* in [Settings](app:settings).

---

## 5. Notifications

[Settings](app:settings) → *Notifications* holds every switch:

- **Match alerts:** *Starting soon* (on, with how long before), *Match start* (on), *Live score*
  (off) and *Result* (on).
- **Every day:** a **daily summary** of your favourites' matches, one notification per player, at the
  time you choose; and a notice when a followed tournament starts.
- **Quiet hours** (off by default, 23:00–08:00 when turned on): alerts that fall inside are dropped.
- **Muted players** lists the favourites you muted.

Tapping a notification opens the match.

---

## 6. News

If you enter a **news feed address** (an RSS or Atom feed, in *Settings*), **News** lists the latest
articles, and Today can show *news about your favourites*. **Mark all as read** sits in the action bar.
With no address, news is hidden entirely and nothing is downloaded.

---

## 7. Widget and car

- **Widget:** up to three of today's followed matches on the home screen — live first, then upcoming,
  then finished. A tap opens Today.
- **In the car:** with the phone connected to a car's screen, match alerts can be read aloud, and
  today's favourites and schedule can be browsed.

---

## 8. Data source and status

- *Settings → Data source* chooses where matches come from: a **scoreboard** source (no key) or a
  **keyed fixture list** (a key required), each by an address you enter. Whoever enters an address
  answers for that service's terms. Favourites are kept per source.
- *Settings → Status* says what the app did last: the source in use, the last successful and the last
  failed fetch, and the caches. It is the place to look when a notification did not come.

---

## 9. Backing up the app

*Settings → Back up & restore* saves your favourites, follows and settings into a file, and restores
them on a new phone.

---

## 10. When something goes wrong

- **A notification did not come:** check *Settings → Status* for the last fetch, that the alert is on,
  that the player is not muted, that you were not in quiet hours, and that the phone allows
  notifications and does not put the app to sleep.
- **A live score seems stuck:** the score shown is the last one the source gave; pull to refresh.
- **No news:** the news feed address is blank, or the feed did not answer.
- Questions and ideas: *Settings → About → Send feedback*.
