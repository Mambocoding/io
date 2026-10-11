# FeedScraper — user guide

*English · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Written for FeedScraper 0.1.252 (October 2026). Where this guide and the app disagree, the app is
right.

---

## 1. What FeedScraper is

FeedScraper is a **feed reader**: you subscribe to the feeds of the sites you follow (RSS, Atom, RDF
or JSON Feed), and their new articles come to your phone.

- Everything is fetched and stored on the phone: no account, no server of ours.
- Read, star, save for offline reading, search, and get the news in the background.
- If you run a **SyncHub** at home, your feeds and what you read can follow you to other phones and
  to the hub's web interface ([section 8](#8-sync-with-your-synchub)). Without a hub, the app is a
  plain reader.

---

## 2. Adding feeds

- **Add a feed** (in the menu): paste the address of a feed, or simply of the site — if the page
  offers several feeds, you choose one. The title is taken from the feed; change it if you like, and
  pick a category.
- **Import from a file** (OPML, the standard subscription list, in *Settings*): brings in the feeds of
  another reader. Importing only adds; it never removes or rearranges your feeds. **Export to a file**
  does the reverse.
- **Extract a feed from a page** (*Tools*): for a site with no feed, the app proposes a rule that picks
  the articles out of the page, and applies it at every refresh. It is experimental.

---

## 3. Reading

- **Views** in the menu: **All feeds**, **Favourites** (starred articles), **Saved (offline)**, and
  a **Feeds** summary with one button per feed. Each feed and each category is a view too.
- The list keeps still while you read: articles that arrive during a visit wait behind a *new
  articles* pill at the top. Scroll to the end to load older ones.
- **Swipe** a row to mark it read or unread, or to star it. A **long press** selects an article and the
  action bar shows what you can do with it.
- **Mark all read** clears a view in one go.
- Open an article to read it; swipe or use the arrows for the previous and next one. The action bar
  offers star, share, save offline, and open in the browser. Text size and line spacing can be
  adjusted.
- The magnifier **searches** the current view; one tap widens it to every feed.
- On a wide screen, the list and the open article stand side by side.

---

## 4. Saving for offline reading

**Save offline** keeps an article with its text and images, readable with no network; **Save feed
offline** does it for a feed's whole unread backlog. Saved articles are in **Saved (offline)**.
*Settings* shows how much space they take, can remove them once read after a delay, and can keep
images to Wi-Fi.

---

## 5. Organising your feeds

- **Edit feeds and categories** (in the menu) reorders feeds and categories, moves feeds between
  categories, merges or deletes categories.
- Editing a feed changes its address, title and category, disables it, or
  **unsubscribes**. *Hide articles whose title contains* hides articles by keyword (one term per
  line); they are not deleted, and clearing the term brings them back.
- A **heart** on a feed marks it as a favourite; with a hub, the hub uses it to say what is new.
- A feed that keeps failing is flagged in the menu, with a link to its **fetch log**. If a feed's
  address no longer exists, the app proposes the feeds the site now advertises.

---

## 6. Refresh and notifications

- Feeds refresh in the background, downloading only what changed and backing off feeds that fail.
  *Settings* sets how often, whether mobile data may be used, and whether to refresh every feed when
  the app opens.
- Pull down in a view to refresh it now.
- **New-article notifications** are off by default and chosen per feed.
- **Delete read articles older than** (off by default) keeps the database small.

---

## 7. Settings and privacy

In [Settings](app:settings): **Open on launch** (where you left off, the feed summary or your
favourites), display, refresh, notifications, offline storage, backups, and the app lock.

- Articles are cleaned before they are shown: no script from an article ever runs.
- The **app lock** (off by default) asks for your fingerprint or screen lock; it hides, it does not
  encrypt.
- *Back up & restore* saves your feeds, categories, read state and settings into a file, and restores
  it.

---

## 8. Sync with your SyncHub

Syncing with a hub is the part a one-time purchase unlocks; everything else is free.

1. Open **SyncHub** in the menu. The app looks for the hub on your network, or you type its address.
2. In the hub's web interface, open **Settings → Devices → Pair a device**, and scan the QR code with
   the app.
3. Compare the certificate fingerprint when asked: the app trusts the hub only once you confirm it.

- Feeds, categories, hearts, read and starred state and settings then travel both ways; the hub keeps
  fetching your feeds while your phone sleeps.
- If the hub's certificate changes, sync stops until you decide. Nothing is re-trusted silently.
- If the hub cannot be reached for a long time, the app tells you. The menu's dot shows the sync
  state at a glance.

---

## 9. When something goes wrong

- **"… didn't refresh — diagnose":** open the feed's fetch log; it says what the site answered.
- **"… keeps refusing us":** the site blocks automated readers; there is nothing the app can do
  politely.
- **An article shows no image:** some sites refuse image requests from apps; the article still reads.
- **Sync stopped after the hub changed:** compare the new fingerprint on the hub's pages before
  trusting it again.
- Questions and ideas: *Settings → About → Send feedback*.
