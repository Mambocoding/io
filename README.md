# Mambocoding — public release feed

This repository exists for one reason: **so that an application you already run can find out whether
a newer version exists, without holding any credential.**

The applications themselves live in private repositories. Their *release notes* are not secret —
they are written for whoever has to install the update. Publishing only that, here, means:

- **nobody mints a token** to be told that a new version is out;
- **no credential is embedded in any image** for someone to extract from it later;
- what becomes public is a version number and the note that goes with it, never a line of source.

## What is in here

```
<product>/latest.json     the newest released version of that product, and what it owes you
```

One directory per product, one file per product:

| path | product | source |
| --- | --- | --- |
| [`synchub/latest.json`](synchub/latest.json) | **SyncHub** — a server you run on your own machine, typically a home NAS, so your apps' data lives with you | `Mambocoding/SyncHub` *(private)* |

And one more kind of public, non-secret text — each application's **privacy policy**, because the
store needs a public address for it and the applications' own repositories are private:

```
privacy/<app>/index.md    that application's privacy policy, served at
                          https://mambocoding.github.io/io/privacy/<app>/
```

| path | application | source |
| --- | --- | --- |
| [`privacy/feedscraper/`](privacy/feedscraper/index.md) | FeedScraper | `specs/SPEC-055-privacy-policy.md` §3 |
| [`privacy/filesmanager/`](privacy/filesmanager/index.md) | FilesManager | the in-app `privacy_body` |
| [`privacy/flightscraper/`](privacy/flightscraper/index.md) | FlightScraper | the in-app `privacy_body` |
| [`privacy/notesmanager/`](privacy/notesmanager/index.md) | NotesManager | the in-app `privacy_body` |
| [`privacy/soundmaster/`](privacy/soundmaster/index.md) | SoundMaster | the in-app `privacy_body` |
| [`privacy/stocksscraper/`](privacy/stocksscraper/index.md) | StocksScraper | the in-app `privacy_body` |
| [`privacy/tennisscraper/`](privacy/tennisscraper/index.md) | TennisScraper | the in-app `privacy_body` |
| [`privacy/weatherscraper/`](privacy/weatherscraper/index.md) | WeatherScraper | the in-app `privacy_body` |

Each page is a **verbatim copy** of the text its application owns, and its first line names the
source commit. It is written by hand, the day that text changes (the application's release owes it),
and never edited here first: if a page and its source disagree, the source is right. Nothing on a
page loads or runs. The rule is AppShell's `specs/SPEC-039-privacy-pages.md`.

And each product's **user guide**, for the same reason — the people who install it cannot read the
private repository — and because each application **carries its own copy**, readable offline from
*About → Guide* (AppShell `specs/SPEC-094-in-app-guide.md`):

```
doc/<product>/README-<lang>.md    that product's user guide, one file per language
```

| path | product | languages |
| --- | --- | --- |
| [`doc/feedscraper/`](doc/feedscraper/README-en.md) | FeedScraper | [en](doc/feedscraper/README-en.md) · [fr](doc/feedscraper/README-fr.md) · [de](doc/feedscraper/README-de.md) · [es](doc/feedscraper/README-es.md) · [nl](doc/feedscraper/README-nl.md) |
| [`doc/filesmanager/`](doc/filesmanager/README-en.md) | FilesManager | [en](doc/filesmanager/README-en.md) · [fr](doc/filesmanager/README-fr.md) · [de](doc/filesmanager/README-de.md) · [es](doc/filesmanager/README-es.md) · [nl](doc/filesmanager/README-nl.md) |
| [`doc/flightscraper/`](doc/flightscraper/README-en.md) | FlightScraper | [en](doc/flightscraper/README-en.md) · [fr](doc/flightscraper/README-fr.md) · [de](doc/flightscraper/README-de.md) · [es](doc/flightscraper/README-es.md) · [nl](doc/flightscraper/README-nl.md) |
| [`doc/notesmanager/`](doc/notesmanager/README-en.md) | NotesManager | [en](doc/notesmanager/README-en.md) · [fr](doc/notesmanager/README-fr.md) · [de](doc/notesmanager/README-de.md) · [es](doc/notesmanager/README-es.md) · [nl](doc/notesmanager/README-nl.md) |
| [`doc/soundmaster/`](doc/soundmaster/README-en.md) | SoundMaster | [en](doc/soundmaster/README-en.md) · [fr](doc/soundmaster/README-fr.md) · [de](doc/soundmaster/README-de.md) · [es](doc/soundmaster/README-es.md) · [nl](doc/soundmaster/README-nl.md) |
| [`doc/stocksscraper/`](doc/stocksscraper/README-en.md) | StocksScraper | [en](doc/stocksscraper/README-en.md) · [fr](doc/stocksscraper/README-fr.md) · [de](doc/stocksscraper/README-de.md) · [es](doc/stocksscraper/README-es.md) · [nl](doc/stocksscraper/README-nl.md) |
| [`doc/synchub/`](doc/synchub/README-en.md) | SyncHub | [en](doc/synchub/README-en.md) · [fr](doc/synchub/README-fr.md) · [de](doc/synchub/README-de.md) · [es](doc/synchub/README-es.md) · [nl](doc/synchub/README-nl.md) |
| [`doc/tennisscraper/`](doc/tennisscraper/README-en.md) | TennisScraper | [en](doc/tennisscraper/README-en.md) · [fr](doc/tennisscraper/README-fr.md) · [de](doc/tennisscraper/README-de.md) · [es](doc/tennisscraper/README-es.md) · [nl](doc/tennisscraper/README-nl.md) |
| [`doc/weatherscraper/`](doc/weatherscraper/README-en.md) | WeatherScraper | [en](doc/weatherscraper/README-en.md) · [fr](doc/weatherscraper/README-fr.md) · [de](doc/weatherscraper/README-de.md) · [es](doc/weatherscraper/README-es.md) · [nl](doc/weatherscraper/README-nl.md) |

**This is where a guide is written.** Unlike a privacy page, the guide's source is here: each
application's release copies the files into its own build, verbatim, the first line naming the commit
it copied (`<!-- source: Mambocoding/io doc/<app>/README-<lang>.md @ <commit> -->`). Nothing is fetched
at runtime. A change to an application that leaves its guide behind owes an `owes:` line in that
application's release notes.

**What a guide file is**, so that an application can read it (AppShell SPEC-094 §G3):

1. `# <Product> — <user guide>`, then the language bar (`*English · [Français](README-fr.md) · …*`,
   the current language unlinked), then one line *Written for <Product> <version> (<month year>)*, then
   `---`.
2. One `##` heading per chapter, numbered (`## 3. Pairing a phone`); `###` for sections inside it.
   Chapters are separated by `---`.
3. Markdown only from this subset: paragraphs, `-` and `1.` lists (one nested level), `>` quotes,
   fenced code, `|` tables, `**bold**`, `*italic*`, `` `code` ``. **No images.**
4. Links only to a heading of the same file (`[section 7](#7-folder-sync)`, the GitHub anchor) or to
   one of the application's screens (`[Settings](app:settings)`); an application turns the names it
   knows into links and shows the others as text. No link out of the application.
5. English is required; `fr`, `de`, `es`, `nl` follow it chapter for chapter (same numbering). A
   missing language falls back to English in the application, and says so.
6. The brand rule of this portfolio applies to every word: a guide names what the user sees and does,
   never a third party's product, site or service.

And the portfolio's **announcements** — a short note the developer sends to the people who use the
applications (a new feature, a change to come, a problem being fixed), shown inside each application
it concerns (AppShell `specs/SPEC-107-announcements.md`):

```
announcements/index.json                          the list every reader reads first
announcements/AnnouncementYYYYMMDD-HHMM-<lang>.md one file per language, en required
announcements/AnnouncementYYYYMMDD-HHMM/<n>.<ext> its images (png, jpg, webp; ≤ 1 MiB; ≤ 8)
```

**Written by WatchTower only**, on the developer's *Publish*, as one commit on `dev`; **never edited
afterwards** — a correction is a new announcement. Each language file ends with one HTML comment, the
announcement's metadata, invisible wherever the Markdown is shown:

```
<!-- announcement
apps: feedscraper, notesmanager
title: Sync is back on every phone
from: 2026-10-23T14:30Z
expires: 2026-11-22T14:30Z
versions: feedscraper >=1.4.0 <2.0.0
-->
```

`apps` is `all` or the applications' identifiers (the folder names used here; `synchub` covers the
hub, its desktop clients and the Windows client); `from` may be in the future (readers wait for it);
after `expires` an announcement is never *new* again. `index.json` is the machine copy of those
footers. The text may use what the guides use plus `https:` links and the announcement's own images —
no HTML, no remote image. Read anonymously, at most once a day, at
`https://raw.githubusercontent.com/Mambocoding/io/dev/announcements/` — a path compiled into the
applications, so, like rule 3 below says of the feed, it never moves.

Nothing else belongs in this repository: no code, no configuration, no build output, and — rule 2
below — no credentials.

## The file

```json
{
  "schema": 1,
  "version": "0.2.128",
  "publishedAt": "2026-09-20T07:10:09Z",
  "notes": "owes: a forward-only migration (V025, schema version 25) adds one table …",
  "releaseUrl": "https://github.com/Mambocoding/io/blob/main/synchub/notes/v0.2.128.md"
}
```

| field | what it is |
| --- | --- |
| `schema` | the format's own version. A reader that does not recognise it stops and says so, rather than guessing at the rest. |
| `version` | the newest **released** version: three integers, no `v` prefix. This is what a running application compares against itself. |
| `publishedAt` | when that release was published (RFC 3339, UTC). |
| `notes` | what this version owes the person installing it — a migration, a configuration key that changed, a rollback that stops working — or `owes: none`. It is that release's own entry, verbatim. |
| `releaseUrl` | the release itself, for a human who wants the whole story. |

Applications read `version` and `notes`. The other two fields are for people.

## How it is read

Anonymously, over HTTPS, about once a day, by the application itself:

```sh
curl -s https://raw.githubusercontent.com/Mambocoding/io/main/synchub/latest.json
```

No account, no token, no API key — that is the entire point of this repository existing.

## How it is written

By each product's own release workflow, **after** that release's image has been published and never
before, with a token that can write here and nowhere else.

**Not by hand.** The only hand-written file this repository ever sees is the first one, seeding a new
product's path; from then on the workflow owns it.

## Four rules, and why each one is here

1. **Never announce a version that does not exist yet.** A `version` naming a release with no
   published image turns every installed instance's *Apply update* into a download that cannot
   succeed. The workflow writes only after the image push succeeds, and a hand-written seed names the
   version that is *currently released* — never the next one.
2. **Never put a credential in this repository.** Everything here is public, permanently, and reading
   this feed requires nothing. GitHub also scans public repositories and revokes its own token
   formats when it finds them, so a token committed here would be both world-readable and dead within
   hours.
3. **Never move or rename a path.** A running application holds its feed URL as a constant compiled
   into it; there is no way to tell an already-installed copy about a new location. A path published
   once is published forever.
4. **`version` is three integers.** Never `latest`, never a branch name, never a build number — a
   floating tag makes *which version am I running?* unanswerable, which is the question this whole
   mechanism exists to answer.

---

*Questions about a privacy policy or a guide belong in this repository's issues, the contact every
policy names — the products' own repositories are private. Everything else belongs with each product.
This one holds no code — only the answer to "is there a newer version, and what will it cost me?",
what each application does with your data, and how to use it.*
