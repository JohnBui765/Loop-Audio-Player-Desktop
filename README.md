# Echo Loop+ Desktop

Echo Loop+ for a computer screen, built for working with coursebook audio: cutting it into the exact sounds you need, looping them, and shuffling them into practice sets you can write down on paper.

Everything Echo Loop+ does is still here: folders, play counts, Repeat One / All / Off, speed changes that keep the speaker's natural pitch, Mark and End, flags with their own speed and repeats, Join into one track, the sleep timer and offline use.

## What's new in version 2

**2.2:**
- **Copies, scattered.** In the Shuffle set dialog, the **×1** beside each flag gives it up to 4 copies (or set every picked flag at once with **Copies of each item**). Copies are spread through the set and never play back to back; if there are too few other items to keep them apart, the dialog says so. **Each copy plays ×2/×3** still repeats a copy back to back.
- **Every play says where it came from.** A set's flags read like **#7 · 2/4**: flag 7 of the original recording, copy 2 of 4 (with **A**, **B**… for each recording when a set mixes them). Their details show the time in the original. The numbers are kept with the set, so Reshuffle keeps them too.
- **Cue sheet.** A set's **⋯ → Save the cue sheet…** saves a text file listing every play: its position, start time, flag, copy and time in the original — your answer key. It pastes straight into a Word or Excel table. It is never put inside the MP3, where any music player would show it.
- **MP3 export.** **Export as an MP3 file…** sits beside every WAV export, for whole recordings and sections: 192 kbps stereo or 128 kbps mono, constant bitrate, about 1.4 MB per minute. It's made in the background with a percentage shown, roughly 3–5 seconds per minute of stereo. The encoder is LAME, in `lame.js`.
- **Flag numbers** stay readable on narrower blocks in the strip above the waveform.

**2.1 (fix):** the sound engine now starts when you open `index.html` straight from a folder on your computer. Before, Chrome refused to start it there and the app wrongly said "use Chrome or Edge".

- **A new sound engine.** The app now plays audio with its own engine instead of the browser's audio player. Loops are seamless and exactly as long as you set them, every start, stop and loop seam gets a tiny fade so nothing clicks, and slowed-down speech keeps its natural pitch.
- **The playhead shows what you hear.** The moving line on the waveform is timed to the sound coming out of your headphones or speakers, allowing for their delay. If it still looks early or late on your equipment, **Sound → Playhead timing** fine-tunes it.
- **Magic wand.** Press **W** (or click the wand in the toolbar) and click a word on the waveform: exactly that block of sound is selected. **Shift+click** adds the next one. **Syllables / Words / Phrases** sets what counts as one sound. Press **V** to go back to dragging across the waveform.
- **Edges that land between sounds.** Section edges snap to the quietest point nearby, so a loop doesn't start or end in the middle of a sound. Hold **Alt** while dragging to place an edge freely. When you're zoomed in closely, ‹ › move an edge by 10 ms instead of 0.1 s.
- **Split into sounds.** Select a stretch and press **K** (or **Split**): it becomes one flag per sound.
- **Crop and cut.** From **⋯** in the section bar (or by right-clicking the waveform): **Crop** makes a new recording of just the section, **Cut out** makes one without it. The original recording is never changed, and flags come along.
- **Shuffle sets.** Click **Shuffle set** at the top. Pick up to 100 flags from any recordings, choose how many times each plays, the pause after it (time to write it down) and the number of rounds. The set becomes a new recording in the "Shuffle sets" folder, with one numbered flag per item. The order comes from your computer's cryptographic random source, every round is a new shuffle, and an item never plays twice in a row. **Reshuffle** plays the same items in a new order.
- **Undo.** **Ctrl+Z** undoes changes to flags (saving, splitting, moving, renaming, deleting); **Ctrl+Shift+Z** or **Ctrl+Y** redoes them. On a Mac, use ⌘.
- **Sound options.** **Even out volume** brings quiet and loud parts closer together; **Clarity** cuts low rumble and lifts speech a little.
- **Export.** Any recording, or just a section, can be saved as a WAV file (from its ⋯ menu).
- **Smoother.** Zooming glides, and waveforms are drawn in the background without holding up the app.

The zoomable waveform, the length lock and the flags from version 1 work as before: scroll the mouse wheel to zoom, drag the box in the strip on top to move around, lock a section's length and drag it along the recording.

## Put it online (GitHub Pages)

**Updating from version 1 or 2:** in your existing `echo-loop-desktop` repository, upload the new `index.html`, `sw.js`, `manifest.webmanifest` and `README.md`, replacing the old ones, plus the new `lame.js` and `lame-LICENSE.txt` (the icons haven't changed). Open the app once while online; it updates itself the next time you open it. Your recordings and flags stay where they are.

**First time:**

1. On the **same GitHub account** as Echo Loop+, create a new public repository, for example `echo-loop-desktop`. Upload every file in this folder and keep the file names as they are.
2. In the repository, open **Settings → Pages** and choose **Deploy from a branch → main → / (root)**. Save.
3. After a minute, open `https://<your-username>.github.io/echo-loop-desktop/` in **Chrome** or **Edge** on your computer.
4. Click **Install app** at the top right of the page, or the install icon at the right end of the address bar. The app opens in its own window and gets a Start-menu entry and a taskbar icon.
5. Open it once while online. When the badge says **Offline ready**, it works without internet.

## Your library comes with you

Your recordings, play counts and flags are stored in the browser on your computer, and nothing is uploaded anywhere. Echo Loop+ and Echo Loop+ Desktop on the same GitHub account count as the same site, so they share one library in that browser. Shuffle sets, crops and cuts are ordinary recordings there, so Echo Loop+ can play them too.

**Keep only one of the two apps open at a time.** An older window left open in the background still holds its old copy of the library and can save it over newer changes.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app |
| `sw.js` | Saves the app for offline use |
| `lame.js` | The MP3 encoder (LAME, LGPL-3.0), loaded only when you export an MP3 |
| `lame-LICENSE.txt` | The encoder's licence |
| `manifest.webmanifest` | App name, icon and colours used when it's installed |
| `icon-180.png`, `icon-192.png`, `icon-512.png` | App icons |
| `make_icons.py` | Script that draws the icons (only needed if you want to change them) |

## Good to know

- **Opening a recording** takes a moment the first time, because the whole recording is read into memory for exact playback. Long recordings are kept at a lower sound quality so they fit: up to about 15 minutes play at full quality, an hour-long lecture at a quality that is still clear for speech.
- **The first click or key press** after opening the app switches the sound on. Browsers don't let a page make sound before you've touched it.
- **Opening it from a folder.** Double-clicking `index.html` works too; the badge at the top then says "Opened from a folder". That copy can't be installed or work offline, and it keeps its own library: recordings you add there don't appear at your GitHub Pages address, and the other way round.
- **Shuffle sets and crops are WAV files**, so they take more space than MP3s: about 5 MB per minute. The WAV stays the master copy; **Export as an MP3 file…** makes a smaller copy to share (about 1.4 MB per minute).
- **Media keys** (play/pause, next, previous) work while the window is in the background.
- **Narrow windows.** When the window is narrower, for example snapped to half the screen, the flags move under the waveform. Below about 880 pixels wide, the library opens from the list button at the top left.
- **Browsers.** Chrome and Edge are the best fit: they install the app, save files where you choose and play MP3, M4A, WAV, FLAC and OGG files.
- **Updating later.** If you change any file, also change `eld-v4` to `eld-v5` (and so on) at the top of `sw.js`. The app picks up the new version the next time it's opened online.
