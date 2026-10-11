# NotesManager — user guide

*English · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Written for NotesManager 0.1.34 (October 2026). Where this guide and the app disagree, the app is
right.

---

## 1. What NotesManager is

NotesManager keeps three kinds of notes on your phone:

- **Notes** — free text, written in Markdown if you like;
- **Checklists** — items you tick off;
- **To-do lists** — items with a due date and, if you want, a reminder.

Your notes live on the phone. If you run a **SyncHub** at home, they also travel to your other
devices through it ([section 7](#7-sync-with-your-synchub)); without a hub, the app works exactly
the same.

---

## 2. Writing a note

- Tap **+**: a new note opens, ready to type. There is no type to choose and no Save button.
- What you type is **saved as you go**, and again the moment you leave the app. The title bar says
  when the note was last saved.
- The title is optional: an empty title shows the first line of the note instead.
- Text shared from another app (*Share → NotesManager*) becomes a new note.

### 2.1 Checklists and to-do lists

- In a note's overflow menu (⋮), **Convert** turns it into a **Checklist** or a **To-do list**, and
  back. Each line of a note becomes an item; items become lines again. Converting a to-do list away
  drops its due dates and reminders, and the app asks before doing so.
- Add an item in the last row and press return; the field stays open for the next one.
- Drag an item by its handle to reorder it; swipe it away to remove it (with *Undo*).
- The overflow menu can hide checked items or uncheck them all.
- In a to-do list, an item gets a **due date** chip, then a **reminder** chip: at the reminder's
  time, a notification shows the item; tapping it opens the note. The first reminder asks for
  permission to post notifications.

---

## 3. Finding notes

- **All notes** shows your notes as cards or as a list (the overflow menu switches). **Pinned**
  notes come first.
- **Swipe** a card to the right to pin it, to the left to archive it. A swipe never deletes.
- **Sort** by last change, creation, title, or your own order inside a label.
- **Search** (the magnifier) looks through titles, texts and items as you type — archived notes
  included. Accents do not matter: *ete* finds *été*. Narrow it to **Body** or **Items**.

### 3.1 Labels

A note can wear several **labels**. Add one from the note (the *+* chip under the title) or create
labels in the menu's **Labels** section. Tapping a label in the menu shows only its notes; a long
press renames or deletes it. Deleting a label keeps its notes.

---

## 4. Selecting, archiving, deleting

- A **long press** starts a selection; tap more notes to add them. The action bar then offers pin,
  archive, labels, share and delete for all of them at once.
- **Archive** hides a note from *All notes* and labels without deleting it; it stays searchable and
  editable in **Archive**.
- **Delete** sends notes to the **Trash**. A note in the Trash can be **restored**, or deleted for
  good.
- The Trash keeps notes for **30 days**, then deletes them. The delay matches the hub's: a note kept
  longer could come back to life on your other devices.

---

## 5. When two devices edit the same note

NotesManager **never merges two versions of a note's text in silence**.

- If a note's text was changed on two devices before they synced, **both texts are kept**: the
  second one becomes a **Conflict copy**, shown right after the original. Read both, keep what you
  want, delete the other.
- If a note changes on another device **while you are typing**, your text is kept as a conflict copy
  and the note shows the other device's text, with a line saying where your typing went.
- In a list, items are merged one by one: ticks, order and dates follow the latest change; two
  different edits of the same item's text are kept as two items.

---

## 6. Your data: export, import, delete all

In [Settings](app:settings) → *Data*:

- **Export notes** saves your notes as a bundle of Markdown files (and to-do lists in the common
  calendar-task format) that other apps can open.
- **Import notes** reads the export bundle of another notes app: a zip holding one JSON file per
  note. The app shows what it found before importing anything; labels, pins and archived notes are
  kept.
- **Delete all notes** erases every note, label and item on this phone, after you type a confirmation
  phrase. Your settings, the app lock and the hub pairing stay. If the phone is paired, the hub keeps
  its copy and sends it back on the next sync: to make the deletion stick, unpair the hub first, or
  delete the notes on the hub itself.

---

## 7. Sync with your SyncHub

1. Open **SyncHub** at the bottom of the menu. The app looks for the hub on your home network; if it
   does not find it, type its address.
2. In the hub's web interface, open **Settings → Devices → Pair a device** and **scan** the QR code
   with the app (the *Scan* button). Scanning checks the hub's certificate exactly.
3. Your notes are sent to the hub, and from then on travel both ways.

- **Sync mode:** *Automatic* syncs by itself, a little after each change and in the background;
  *Manual* waits for **Sync now**.
- The sync screen shows when the last round happened and, per kind of data, how many changes went
  each way.
- If the hub cannot be reached for a long time, the app can tell you with a notification.
- The hub's web interface shows and edits the same notes.

---

## 8. Privacy and the app lock

- Notes are stored on the phone only, and on your own hub if you pair one. The app connects to
  nothing else.
- **App lock** (*Settings*): NotesManager asks for your fingerprint, face or screen lock when it
  opens, and after the delay you choose. The app lock hides the app; it does **not** encrypt your
  notes.

---

## 9. When something goes wrong

- **"Your settings were damaged and have been reset":** the app could not read its settings and
  started fresh. **Your notes are safe.** The hub pairing has to be done again; the hub then receives
  your notes again.
- **A note is marked *Conflict copy*:** two versions of its text met; see
  [section 5](#5-when-two-devices-edit-the-same-note).
- **A reminder did not ring:** check that notifications are allowed for NotesManager, and that the
  phone allows it to set exact alarms.
- Questions and ideas: *Settings → About → Send feedback*.
