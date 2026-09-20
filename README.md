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

Nothing else belongs in this repository: no code, no configuration, no build output, and — rule 2
below — no credentials.

## The file

```json
{
  "schema": 1,
  "version": "0.2.128",
  "publishedAt": "2026-09-20T07:10:09Z",
  "notes": "owes: a forward-only migration (V025, schema version 25) adds one table …",
  "releaseUrl": "https://github.com/Mambocoding/SyncHub/releases/tag/v0.2.128"
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

*Issues and discussion belong in each product's own repository. This one holds no code — only the
answer to "is there a newer version, and what will it cost me?"*
