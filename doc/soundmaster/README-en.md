# SoundMaster — user guide

*English · [Français](README-fr.md) · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Written for SoundMaster 0.1.48 (October 2026). Where this guide and the app disagree, the app is
right.

---

## 1. What SoundMaster is

SoundMaster is a **sound level meter**: it shows, in decibels, how loud it is around your phone. It
also **records** sound when you ask it to.

It claims what a phone can deliver, and no more:

- **Calibrated** against a real sound level meter, a reading is good to about **±3 dB**. With the
  starting value, it can be off by about **±10 dB**.
- Two readings on the same phone compare well (about ±3 dB), even without calibration.
- The useful range is roughly **30 to 95 dB**.

It answers *"is this room loud?"*, never *"does this break a regulation?"*: it is not a class 1 or
class 2 instrument. *Settings → About* carries the full statement.

---

## 2. First start

SoundMaster needs the **microphone**. It never asks on its own at launch: Measure shows one sentence
and an **Allow microphone access** button. If you refused for good, Measure says so and offers to
open the system settings.

The microphone is used only while the app is on screen. Nothing is measured or recorded in the
background.

---

## 3. Measuring

**Measure** is the first screen.

- The **needle** shows the current level; the large number is the same level.
- The two **markers** on the arc, *Min* and *Max*, hold the lowest and highest needle level since the
  app opened or since the last reset.
- The **arc** turns from green to red as the level rises (red from 85 dB).
- Under the number, an everyday sound of about the same level gives a sense of scale.
- The line under the number says how the level is computed: *A-weighted* or *unweighted*, *fast* or
  *slow* ([section 6](#6-settings-that-change-the-reading)).

Some states are **not levels**, and the app never shows them as numbers:

- **Clipping** — the sound is too loud for the microphone; the true level is higher than anything
  shown.
- **No signal** — the microphone delivers pure silence (often another app holds it).
- *below useful range* — a quiet room, under about 30 dB: the number is kept, but trust it less.

### 3.1 A run: measure for a while, then save

The **action bar** at the bottom acts on the run:

1. **Start** (the small chart icon) begins a run; the same button stops it.
2. While a run goes on, **This run** shows its lowest and highest level and its **Leq** (the average
   energy over the run), with a trace of the last 60 seconds.
3. **Save session** keeps the result in **History**. *Reset the run* clears the run and the
   markers. **Share** sends the current reading as text.

Leaving the app pauses the run; it goes on when you come back. Changing the frequency weighting, or
the microphone source changing, ends the run, ready to save.

### 3.2 The alert

Above the **alert threshold** (85 dB unless you change it), Measure turns red, with how far above it
is. An **audible alert** (a short beep) can be turned on; it is off by default because the phone's
own microphone hears the beep. The alert is only as good as the calibration behind it.

---

## 4. Spectrum

**Spectrum** splits the sound into ten octave bands, from 31.5 Hz to 16 kHz, and shows which band
dominates. The bands are **relative**: they say which part of the sound is strongest, never a level
in dB per band. *Held* in the overflow menu (⋮) freezes the picture; *Live* starts it again.

---

## 5. Recording

The round **Record** button, on **Record** and on Measure when no run is active, starts a
recording; **Pause** and **Resume** sit beside it.

- Recordings are listed newest first, with their duration and size, and marks for *clipped* and
  *paused*. Play one in place.
- Select a recording for the action bar: **delete**, **share**, **rename** and **download** (a copy
  in a folder you choose).
- Recording does not change the reading: the meter keeps measuring.
- Recordings stay on the phone. They are not in the app's backup, and a recording ends when the app
  leaves the screen.

### 5.1 Transcribing a recording

**Transcribe**, in Record's action bar, turns a recording's speech into text **on the phone**, with
the system's own speech recognition. Nothing is sent anywhere. It needs Android 13 or later and a
phone whose recognizer works offline; if your language is not installed, the screen offers to
download it from the system. The transcript can be copied or shared, and may contain errors.

---

## 6. Settings that change the reading

In [Settings](app:settings) → *Measurement*:

- **Frequency weighting:** *A-weighted* (the default, close to how the ear hears) or *Unweighted*.
- **Time weighting:** *Fast (125 ms)*, the default, follows changes quickly; *Slow (1 s)* steadies
  the needle.
- **Alert threshold** and **Audible alert** ([section 3.2](#32-the-alert)).
- **Start a run on opening:** a run begins by itself at the first reading after launch.
- **Calibration** ([section 7](#7-calibration)).
- **Typical levels:** everyday sounds and their usual level, the list Measure compares with.

---

## 7. Calibration

Every phone's microphone is different. **Calibration** adds one offset, in dB, to every reading.

1. Put SoundMaster next to a **real sound level meter**, in the same place, with a steady sound.
2. Open *Settings → Measurement → Calibration* and adjust the offset until both read the same.

*Use the starting value* goes back to +110 dB. Another phone app is not a reference: it only checks
that nothing is badly wrong. Every saved session records the offset it was measured with.

---

## 8. History

**History** lists the saved sessions, newest first: date, duration, Leq, lowest and highest level,
peak, weightings, offset and microphone source. A clipped session marks its figures: they are
floors, not levels. Select sessions to delete or share them.

---

## 9. Backing up the app

*Settings → Back up & restore* saves the settings and the session history into a file (never the
audio), and restores it.

- **Automatic backup** makes that file every day.
- If you have a SyncHub, the backup can also be kept **on the hub**: pair from the backup screen,
  with the code the hub shows. That pairing opens SoundMaster's backups and nothing else. It is the
  only time the app uses the network.

---

## 10. When something goes wrong

- **"The microphone could not be opened":** another app may hold it, or the phone refuses this kind
  of capture. Close the other app and come back to SoundMaster.
- **No signal** while the room is not silent: another app or a call holds the microphone.
- **"Your settings were damaged and have been reset":** the app started fresh, with the starting
  offset. **Your sessions and recordings are safe**; calibrate again.
- Questions and ideas: *Settings → About → Send feedback*.
