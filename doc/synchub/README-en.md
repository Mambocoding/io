# SyncHub — user guide

*English · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Written for SyncHub 0.2.216 (October 2026). Where this guide and the hub's own pages disagree, the
hub is right.

---

## 1. What SyncHub is

SyncHub is a small server that you run **on your own machine** — usually a home NAS — so that your
apps' data stays at home instead of in somebody's cloud.

- It keeps the data of several apps (feeds, weather, stocks, notes) for **several people**, each
  account completely separate from the others.
- It **fetches your content around the clock**, so a phone that was switched off misses nothing.
- It gives you a **web interface** in your browser with the same content as your phone.
- It **syncs both ways**: what you star or mark read in the browser shows up on the phone, and the
  reverse.

It is **optional**: an app with no hub configured keeps working exactly as before.

It **never opens itself to the internet**. It answers on your home network only. Reaching it from
outside is your choice, through a VPN or your own reverse proxy (see [section 12](#12-reaching-it-from-outside-home)).

---

## 2. What you need

- A machine that is always on and runs **containers** (a NAS with a container manager, a small Linux
  server, a mini PC). Both `amd64` and `arm64` are supported.
- About **300 MB of memory** to spare and a few hundred MB of disk, plus whatever your files and
  attachments take.
- **Host networking** for the container (Linux). Without it everything still works, except that
  your phone will not find the hub on its own: you type its address instead.
- The machine's **address on your home network**, for example `192.168.1.20`. Your router's list of
  connected devices shows it. Ideally, ask the router to always give that machine the same address.

---

## 3. Installing

### 3.1 Create a folder and two files

Create a folder for SyncHub on the machine (for example `/volume1/docker/synchub` or
`~/synchub`), and put these two files in it.

**`compose.yml`**

```yaml
name: synchub

services:
  synchub:
    image: ghcr.io/mambocoding/synchub:${SYNCHUB_TAG:?set SYNCHUB_TAG in the .env beside this file}
    restart: unless-stopped
    network_mode: host
    cap_drop: [ALL]
    security_opt:
      - no-new-privileges:true
    read_only: true
    tmpfs:
      - /tmp
    volumes:
      - synchub-data:/data
      - launcher-state:/launcher
    environment:
      SYNCHUB_BIND: "0.0.0.0"
      # Your machine's own address on the home network, after synchub.local. Required.
      SYNCHUB_ALLOWED_HOSTS: "synchub.local,192.168.XXX.XXX"
      SYNCHUB_TLS_KEYSTORE_PASSWORD: "${SYNCHUB_TLS_KEYSTORE_PASSWORD:?set it in the .env beside this file}"
      # Your time zone, so dates on the web pages are right.
      TZ: "Europe/Paris"
      # Optional, needed for two-factor sign-in (section 9).
      # SYNCHUB_SECRET_KEY: ""

  # Optional: the launcher, which gives you an "Apply update" button (section 10.2).
  synchub-launcher:
    profiles: ["launcher"]
    image: ghcr.io/mambocoding/synchub-launcher:${SYNCHUB_LAUNCHER_TAG:-latest}
    restart: unless-stopped
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - launcher-state:/state
      - ${SYNCHUB_PROJECT_DIR:-/unset}:${SYNCHUB_PROJECT_DIR:-/unset}
      - ${SYNCHUB_PROJECT_DIR:-/unset}/compose.yml:${SYNCHUB_PROJECT_DIR:-/unset}/compose.yml:ro
    environment:
      SYNCHUB_PROJECT_DIR: "${SYNCHUB_PROJECT_DIR:-}"
      SYNCHUB_COMPOSE_PROJECT: "${SYNCHUB_COMPOSE_PROJECT:-synchub}"
      SYNCHUB_SERVICE: "synchub"
      SYNCHUB_LAUNCHER_POLL_SECONDS: "${SYNCHUB_LAUNCHER_POLL_SECONDS:-10}"

volumes:
  synchub-data:
    name: synchub-data
  launcher-state:
    name: synchub-launcher-state
```

**`.env`** (the name starts with a dot)

```sh
# The SyncHub version to run: three numbers, never "latest".
SYNCHUB_TAG=

# A password protecting the hub's certificate. Choose one now and never change it.
SYNCHUB_TLS_KEYSTORE_PASSWORD=

# Only for the optional launcher (section 10.2): the absolute path of this folder.
SYNCHUB_LAUNCHER_TAG=latest
SYNCHUB_PROJECT_DIR=
```

### 3.2 Fill in four values

| Where | What to write |
| --- | --- |
| `.env` → `SYNCHUB_TAG` | The current version. It is published at <https://raw.githubusercontent.com/Mambocoding/io/main/synchub/latest.json> (the `version` field), for example `0.2.216`. |
| `.env` → `SYNCHUB_TLS_KEYSTORE_PASSWORD` | A long random password. Keep a copy: if it is lost, the hub cannot open its certificate and every phone must be paired again. |
| `compose.yml` → `SYNCHUB_ALLOWED_HOSTS` | Replace `192.168.XXX.XXX` with your machine's address. The hub refuses any request for an address that is not on this list, with a bare *Bad Request*. |
| `compose.yml` → `TZ` | Your time zone (`Europe/Paris`, `Europe/Berlin`, `Europe/Amsterdam`, `America/New_York`…). |

Keep `compose.yml` and `.env` **together** in the same folder: the first one does not start without
the second.

### 3.3 Start it

In that folder:

```sh
docker compose up -d
docker compose logs synchub
```

No account and no password are needed to download the image. Many NAS container managers can also
import a `compose.yml` as a "project"; the result is the same.

In the log, look for these lines:

```
First run: admin account created.
Setup token (use as the admin password): ...
Serving https://192.168.1.20:8443
TLS certificate SHA-256 fingerprint: A1:B2:...
```

Copy the **setup token**: it is the first password of the admin account.

---

## 4. First sign-in

1. In a browser on your home network, open **`https://synchub.local:8443`** or
   **`https://<your machine's address>:8443`**.
2. The browser warns that the connection is not trusted. This is expected the first time; accept
   the warning to continue. [Section 6](#6-a-padlock-in-the-browser) removes the warning for good.
3. Sign in as `admin` with the setup token as the password.
4. A **setup wizard** opens: it walks you through pairing a phone, two-factor sign-in, the address
   your phones will use and the network settings. You can come back to it any time from
   **Settings → Setup**.
5. Change the admin password: **Settings → Account → Change password** (at least 12 characters).

**Turn on the apps you use** in **Settings → Apps** (admin only). Each one switches on or off
instantly, with no restart.

---

## 5. Pairing a phone

1. In the app on your phone, open the hub settings. The app **finds the hub by itself** on your home
   network and offers *SyncHub at 192.168.1.20*. If it does not, type `https://<address>:8443`.
2. In the browser, open **Settings → Devices → Pair a device**. A **QR code** appears, with a code,
   the address and the certificate fingerprint written underneath.
3. **Scan the QR code** with the app. Prefer scanning to typing: the app then checks the
   certificate's fingerprint exactly, character by character.
4. The code is valid for **five minutes** and **once**. If it expires, press *Pair a device* again.

The phone belongs to the account that created the code. Each app (feeds, weather, stocks, notes)
pairs separately and appears as its own line on **Settings → Devices**.

**Read the *Synced* column**, not *Last seen*: *Last seen* only says the phone knocked on the door;
*Synced* says data actually crossed. *Never* means the phone's first real sync has not happened
yet.

---

## 6. A padlock in the browser

The hub's certificate is made by the hub itself, so no browser trusts it out of the box. Your
phone does not care (it remembers the exact certificate at pairing), but the browser warns every
time. To remove the warning, install the hub's **root certificate** once on each computer or
phone you browse from.

### 6.1 Download it

As an admin, open **Settings → Devices**, section **Browser trust**, and press
**Download root certificate**. You get a file named `synchub-ca.crt`.

This root can only vouch for `synchub.local`, `localhost` and your hub's own addresses — nothing
else on the internet.

> **No download button?** The section is shown to **admins only**. If you are an admin and the
> section says the hub holds no root certificate, your hub was installed before this feature
> existed: it keeps its old certificate and will never replace it on its own. The only way to get
> a root is to delete the certificate (`/data/keystore.p12`) and restart, which **makes every paired
> phone re-confirm the new certificate** (Settings → Devices shows a QR for that) or pair again.
> Until then, keep accepting the browser warning.

### 6.2 Install it

**Windows** (Edge, Chrome)
1. Double-click `synchub-ca.crt` → **Install Certificate…**
2. Choose **Current User** → **Next**.
3. Choose **Place all certificates in the following store** → **Browse…** →
   **Trusted Root Certification Authorities** → **OK** → **Next** → **Finish**.
4. Confirm the security warning with **Yes**, then close and reopen the browser.

**macOS** (Safari, Chrome)
1. Double-click `synchub-ca.crt`: Keychain Access opens and adds it to the *login* keychain.
2. Double-click the certificate *SyncHub Local CA* → **Trust** → *When using this certificate*:
   **Always Trust**. Close the window and enter your password.

**Android**
1. Open the phone's **Settings** → **Security & privacy** → **More security settings** →
   **Encryption & credentials** → **Install a certificate** → **CA certificate**.
2. Confirm the warning and pick `synchub-ca.crt` from your downloads.
3. Menu names vary slightly between phone makers; search the settings for "certificate".

**Linux** (Chrome, Chromium) — **Settings → Privacy and security → Security → Manage
certificates**, import the file as a trusted **authority**.

**Firefox** (every system) keeps its own list — **Settings → Privacy & Security → Certificates →
View Certificates… → Authorities → Import…**, then tick **Trust this CA to identify websites**.

Then open `https://synchub.local:8443` again: the padlock is there.

---

## 7. Several people, one hub

- **Each account keeps its own everything**: feeds, read marks, cities, watchlist, notes, settings.
  Nothing is shared between accounts, and no setting shares it.
- A brand-new account is therefore **empty** — that is not data loss.
- An admin creates and deletes accounts and can set a new password for someone who forgot theirs
  (**Settings → Users**), but **can never read** another person's data.
- Roles: every account is a *user*; **admin** manages the hub; **updater** may only apply updates.

---

## 8. Your files

Each account has a private **file area** reachable from any WebDAV client (the file manager of your
computer usually speaks it). Create a token in **Settings → Account**, then connect your client to
`https://<hub>:8443/files/` with your account name and that token — never your password.

---

## 9. Two-factor sign-in

Two-factor sign-in adds a six-digit code from an authenticator app to your password. It is
optional on a hub that stays at home, and **strongly advised** if you reach the hub from outside.

**Before the first account turns it on**, the hub needs a secret key:

1. Generate one: `openssl rand -base64 32`.
2. Put it in `compose.yml` → `SYNCHUB_SECRET_KEY: "<the key>"` (remove the `#`), then
   `docker compose up -d`.
3. **Keep a copy of that key somewhere safe and never change it.** If it is lost, every account
   that uses two-factor sign-in needs an admin reset, and restoring a backup needs the same key.

Then, each person: **Settings → Account**, scan the QR with an authenticator app, confirm with a
code, and **save the ten recovery codes** shown once.

As long as the key is not set, the log says `SYNCHUB_SECRET_KEY is not set: two-factor enrolment
is refused until it is.` — harmless if you do not use it.

---

## 10. Updating

The hub checks once a day whether a new version exists and tells an admin on **Settings → About**,
with what the new version requires of you (usually nothing).

### 10.1 By hand — three steps

1. In `.env`, set `SYNCHUB_TAG` to the new version.
2. `docker compose pull`
3. `docker compose up -d`

Without step 1, the pull fetches the version you already run.

### 10.2 With a button — the launcher (optional)

The launcher is a second, small container that applies an update when an admin presses
**Apply update** on **Settings → About**, and records every time the hub stopped and why.

1. In `.env`, set `SYNCHUB_PROJECT_DIR` to the absolute path of your SyncHub folder.
2. `docker compose --profile launcher up -d`

**Know what you allow**: the launcher holds the container engine's socket, which amounts to full
control of the machine. It takes no instruction from the hub other than "go", and only ever
installs an official SyncHub release. If that is too much for you, update by hand.

---

## 11. Backups

- **Every day at 03:30**, the hub saves a snapshot of its **configuration** (accounts, paired
  devices, tokens, settings). **Settings → Backup** lists them, takes one on demand
  (**Take a snapshot now**), downloads, uploads and restores them (**Restore…**).
- Your **data** (articles, notes, watchlists…) is not in a snapshot: it lives on your phones as
  well and comes back from them.
- Snapshots sit on the same disk as the data by default. Copy them elsewhere with your NAS's backup
  tool — **point it at the snapshot folder**, not at the live database, which cannot be copied
  safely while the hub runs.
- Apps can also store their own backups on the hub: **Settings → Backups** lists yours.

Restoring on a new machine: install the hub, use **the same `SYNCHUB_SECRET_KEY`**, and pick
*Restore a snapshot* on the first setup step. Each phone then re-confirms the new certificate once.

---

## 12. Reaching it from outside home

SyncHub never opens a door to the internet by itself. If you want to reach it away from home, use a
**VPN** to your home network — the simplest and safest way. If you use a reverse proxy instead:

- add the address your phone dials to `SYNCHUB_ALLOWED_HOSTS`;
- turn on **two-factor sign-in** for every account first.

---

## 13. Reading the startup log

`docker compose logs synchub` shows what the hub did when it started. What the usual lines mean:

| Line | Meaning | What to do |
| --- | --- | --- |
| `SLF4J(W): No SLF4J providers were found` and `WARNING: A restricted method… sqlite-jdbc` | Messages from libraries inside the hub. | Nothing. |
| `Applied migration V…` | The database was upgraded to the new version. | Nothing. |
| `First run: admin account created.` + `Setup token…` | The hub started on an **empty** data volume. | On a real first install: sign in with the token. **After an update: your data volume was not kept** — see [section 14](#14-when-something-goes-wrong). |
| `SYNCHUB_SECRET_KEY is not set…` | Two-factor sign-in is unavailable. | Nothing, or [section 9](#9-two-factor-sign-in). |
| `Data directory: /data — docker volume "synchub-data"` | Where your data lives. | Check it names the **same** volume after every update. |
| `Allowed Host headers: [synchub.local, 192.168.1.20]` | The addresses the hub answers to. | The address your phone and browser use must be in the list. |
| `TLS: adopted the existing keystore…` | The hub kept its certificate. Normal on every start after the first. | Nothing. |
| `TLS keystore … is readable by group or others` | The file holding the certificate's private key is readable by others on the machine. | Once: `docker compose exec synchub chmod 600 /data/keystore.p12`, then restart. Nothing else changes. |
| `Serving https://192.168.1.20:8443` | The address to open. It is also announced on your network, so phones find it. | Nothing. If you see *not advertising*, the same line says why. |
| `TLS handshake refused by 192.168.1.42 — the peer rejected this hub's certificate` | The device at that address refused the hub's certificate. | If it is a **computer**: its browser does not trust the hub yet, see [section 6](#6-a-padlock-in-the-browser). If it is a **paired phone**: its certificate is outdated, scan the QR on **Settings → Devices**. |
| `RSS: N subscription(s) … scraped on the phone — not fetched here` | Feeds that your phone reads itself and the hub leaves alone. | Nothing. |
| `Stocks: N instrument(s) … with no symbol any role speaks` | The hub cannot fetch prices for these instruments. | Check the addresses on the stocks settings page; if it persists, report it. |
| `sync: …` | One line per sync with a phone. | Useful to see whether a phone really syncs. |

---

## 14. When something goes wrong

**The browser shows only *Bad Request*.** The address you typed is not in `SYNCHUB_ALLOWED_HOSTS`.
Add it to `compose.yml`, then `docker compose up -d`. Once the hub has stored this value, change it
from **Settings → Setup** instead.

**After an update, the log shows a new setup token and every phone asks to be paired again.** The
hub started on an **empty** data volume: your data was not deleted, it is in another volume. Run
`docker volume ls` and check that `/data` points at `synchub-data`. In your NAS's container form,
the volume line must never be left empty.

**Never run `docker compose down -v`** (nor `docker volume prune`): `-v` **deletes** the data
volume — database, certificate and every pairing. `docker compose up -d`, `restart` and `down`
without `-v` are safe.

**The phone says *the hub's certificate has changed since pairing*.** The hub has a new
certificate. Open **Settings → Devices** and scan the QR shown there with the app: the phone keeps
its pairing and trusts the new certificate. If the hub also lost its data, pair again with
**Pair a device** instead.

**The phone says *unreachable*.** Check, in order: the hub is running; the phone is on the home
network; the address the phone uses is in `SYNCHUB_ALLOWED_HOSTS` (log line `Allowed Host
headers`); open the same `https://…` address in the phone's browser.

**A device is green on Settings → Devices but nothing shows.** Look at *Synced*: *Never* means no
data has crossed yet. **Settings → Sync** shows, collection by collection, what the hub holds for
your account.

**`https://synchub.local:8443` does not open on an Android phone.** Android browsers do not resolve
`.local` names. Use the address instead (`https://192.168.1.20:8443`). The app is not affected: it
finds the hub another way.

---

*Questions: open an issue in this repository. Privacy policies of the apps: [`privacy/`](../../privacy/).*
