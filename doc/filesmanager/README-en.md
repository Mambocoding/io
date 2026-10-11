# Files Manager — user guide

*English · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Written for Files Manager 1.2.329 (October 2026). Where this guide and the app disagree, the app is
right.

---

## 1. What Files Manager is

Files Manager is a file explorer for your phone and your TV. It browses the phone's storage, an SD
card or a USB stick, and the servers on your home network, and it copies, backs up and synchronises
folders between all of them.

- Everything stays on your devices: there is no account and no cloud of ours.
- The base is free and has no advertising. Some features belong to the premium tier; they carry a
  gold sparkle (see [section 13](#13-free-and-premium)).
- On a TV, the same app browses the same places with the remote.

---

## 2. First start

1. A short wizard asks you to accept the terms of use, then lets you pick the **app mode** and a
   theme. The mode can be changed later in [Settings](app:settings) → *Interface*:
   - **File manager** (the default) opens on your files;
   - **Photo viewer** opens on your photos, as a gallery.
2. Android then asks for access to your files. Choose **Grant access** to browse the whole storage,
   or **Choose a folder instead** to give access to one folder only.
3. The first time you open a connection to your home network, Android may ask for **local network
   access**. Allow it: without it, every connection to your network simply times out. You can turn it
   on later in the app's permissions.

---

## 3. Browsing

- The **path** at the top is a row of chips: tap one to go back to that folder. The folder you just
  left stays as a faded chip, so you can go forward again.
- **Layouts:** detailed list, grid or large grid, from the overflow menu (⋮), or pinch the list.
- **Sorting:** by name, date, size or type, ascending or descending; folders can stay first.
- **Search:** tap the magnifier; results replace the list as soon as you type. The search looks in
  the current folder and below; an icon in the search bar widens it to the whole device.
- **Recent:** the clock icon on the *Internal storage* row of the menu shows the files you opened
  lately (7 or 30 days). *Clear recent history* forgets the app's own list.
- **Remember last location** (on by default) reopens the last folder you visited.
- **Split screen:** on a wide screen (a tablet, or a phone in landscape) two panes stand side by
  side, so you can copy from one to the other. It can be turned off in *Settings → Interface*.

### 3.1 Favorites

At the top of your internal storage, tiles lead to **Photos**, **Music** and **Downloads**. Tap
**+ Add** to pin any folder; long-press a tile to remove it (only the shortcut goes, never the
folder). Each connection and each SD card has favorites of its own. The panel folds with its arrow,
or disappears with *Settings → Interface → Show favorites*.

---

## 4. Working with files

- **Select** with a long press, then tap more files; *Select all* is in the action bar.
- The **action bar** (the floating pill) holds what you can do with the selection: copy, move,
  rename, delete, share, compress… Its position (floating, top or bottom) and its buttons are set in
  *Settings → Interface → Action bar*.
- **Copy and move:** after *Copy* or *Move*, go to the destination and paste. If a name already
  exists, the app asks before anything moves: **Replace** or **Duplicate** (`name (1)`), with *For
  all conflicts* to answer once.
- A paste of more than three files continues in the background, with its progress in a
  notification and in **Tools → Transfers**.
- **Delete:** on internal storage a deleted file goes to the **Trash** first
  ([section 10](#10-free-up-space-and-the-trash)). On a network share or an SD card reached through
  Android's picker, deleting is permanent, and the confirmation says so.
- **Properties** show size, dates and location; for a selection, the total size.
- **Zip:** open a `.zip` to browse it, extract it, or compress a selection into a new archive.
- **Text editor:** text files open in a built-in editor with find and replace.

---

## 5. Photos, documents and media

- **Image viewer:** swipe to the next or previous picture, pinch or double-tap to zoom. The title
  shows when the photo was taken. A tap hides or shows the bars.
- The viewer's pill holds **Share · Edit · Details · Use as… · Slideshow · Print · Delete**. Deleting
  shows the next picture in its place.
- **Photo editor:** crop, rotate, flip and straighten are free; resize, colours, filters,
  annotations, cutout and erase are premium.
- **PDF:** PDF files open in the app, with search and page jumps. Files Manager can also be chosen
  as the phone's PDF reader.
- **Player:** music and videos play in the app, also straight from a network share.
- A file on a connection opens in the app directly; another app receives a temporary copy.

---

## 6. Network connections

Files Manager reaches the servers of your home network as if they were folders on the phone.

1. Open the menu, then **Connections → Add connection**.
2. Choose the type: **SMB** (a computer's shared folders and most NAS, free), **FTP/FTPS**, **SFTP**, **WebDAV**
   or **S3** (premium).
3. Enter the server's address, your user name and password, and optionally a starting folder. The
   password is stored encrypted on the phone.
4. The connection appears in the menu with its free space. Tap it to browse.

The first time a server shows a certificate the app has not seen, it asks you to trust it; from then
on, a different certificate is refused.

### 6.1 Your SyncHub's file area

If you run a SyncHub at home, its file area is a **WebDAV** connection: the hub's address, your
account name as the user name and the hub's application token as the password.

---

## 7. Folder sync

**Tasks** copy folders from one place to another, again and again, with one tap or on a schedule.

1. Open **Tasks** in the menu and create a task. The wizard asks:
   - **What kind of sync?** **Back up** (copy new and changed files; nothing is deleted),
     **Mirror** (make the target an exact copy), **Move**, **Download** or **Two-way**;
   - the **source** and the **target** folders, on the phone or on a connection;
   - the options: filters, what to do on a conflict, notifications, and whether to run
     automatically.
2. Run it with the play button, in the task list or in the menu. **Run all tasks** at the bottom of
   the list runs them one after the other.
3. A task's page shows its progress, its last result and its history; it can be paused, stopped,
   edited or disabled.

Free: a manual **Back up** to the phone or to an SMB share — also straight from the explorer with
*Back up to remote…*. Premium: the other kinds, schedules, live sync and the advanced options.

An automatic task runs every 1, 3, 6, 12 or 24 hours, only on Wi-Fi unless you allow mobile data,
and optionally only while charging.

---

## 8. Sending files to a nearby device

**Send to device** exchanges files with phones and computers on the same Wi-Fi, without a cable or a
cloud.

- To **receive**, open *Send to device* and turn on **Make me visible**. You stay visible only while
  this screen is open.
- An incoming offer always asks first: **Accept**, **Decline** or **Block**, and where to save it.
  Nothing is received before you accept.
- To **send**, pick a device in the list, then the files; or use *Share* from another app and choose
  *Share to device*.
- A device that is not found can be added by its address or by scanning its QR code.

Transfers on the same Wi-Fi are not encrypted: use it at home, not on a public network.

---

## 9. Share this device (premium)

A computer on the same Wi-Fi browses and downloads the phone's files in its web browser, with
nothing to install.

1. **Connections → Share this device**, choose the shared folder, and decide whether the browser
   may also upload and delete (*Allow uploads and deletes from the browser*, off by default).
2. **Start sharing:** the screen shows an address, a QR code and a six-digit PIN.
3. Open the address on the computer and type the PIN.

Sharing stops with *Stop*, or by itself after 30 minutes without use. After five wrong PINs it stops
answering. The connection is not encrypted, and the screen says so: use it only at home.

---

## 10. Free up space and the Trash

- **Tools → Free up space** sorts big and old files into categories. Nothing is pre-selected: you
  review each file, then **Move to Trash**.
- **Tools → Trash** lists what was deleted from internal storage. **Restore** puts a file back where
  it was; **Empty** deletes everything for good.
- In *Settings → Trash*, choose whether deleting goes to the Trash or deletes directly, and how long
  the Trash keeps files (until emptied, or 5, 15, 30 or 90 days).

---

## 11. Privacy: app lock and vault

- **App lock** (free, *Settings → Privacy*): Files Manager asks for your fingerprint, face or screen
  lock when it opens, and after a delay you choose when you leave it. Its content is hidden in the
  recent-apps screen.
- **Vault** (premium): a private, encrypted space. Files moved there (*Move to vault*) are encrypted
  on the phone and hidden from the gallery and other apps. The vault opens with your screen lock.
  - When you create it, the app shows a **recovery code**. Write it down and keep it away from the
    phone: it is the only way back in if the screen lock is removed, the phone is reset or you change
    phones. Nobody can reset it for you; without it, the vault's files are lost for good.
  - *Save a copy out* writes a decrypted copy of a file outside the vault.

---

## 12. Backing up the app

*Settings → Backup* saves the app itself — connections, tasks, favorites, themes and settings — into
one encrypted file protected by a passphrase you choose, and restores it on a new phone.

- **Automatic backup** makes that file every day by itself.
- If you have a SyncHub, the backup can also be kept **on the hub**: pair the app with it from the
  backup screen. That pairing opens Files Manager's backups and nothing else.

Your files themselves are not in this backup: copy them with a task ([section 7](#7-folder-sync)).

---

## 13. Free and premium

Free, for good: browsing, file operations, favorites, gallery, viewers and player, the Trash and
*Free up space*, zip, SMB connections, manual backup to SMB or to the phone, *Send to device*, the app
lock, and the automatic backup of the app.

Premium: the other connection types (FTP/FTPS, SFTP, WebDAV, S3), every sync beyond a manual backup,
schedules and live sync, the advanced photo editing tools, processing profiles, the vault and *Share
this device*.

A premium feature is visible everywhere with a gold sparkle; tapping it opens the premium screen.
A task that uses a premium option is skipped, never half-run.

---

## 14. When something goes wrong

- Error messages say what happened in plain words. **Details** under a message shows the technical
  cause, which you can copy into a feedback mail (*Settings → About → Send feedback*).
- **A connection times out:** check that *local network access* is allowed for the app, that the
  phone is on the same Wi-Fi as the server, and the server's address.
- **"Your settings were damaged and have been reset":** the app could not read its settings and
  started fresh. Your files are safe; connections, tasks and favorites need to be set again, or
  restored from a backup ([section 12](#12-backing-up-the-app)).
- **A task stopped:** open it in *Tasks*; its page says why. Transient network problems resume by
  themselves; a paused task waits for you.
