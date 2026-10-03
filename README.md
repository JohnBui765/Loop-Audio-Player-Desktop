# Echo Loop+ Desktop

Echo Loop+ rebuilt for a computer screen. Everything Echo Loop+ does is still here: folders, play counts, Repeat One / All / Off, speed changes that keep the speaker's natural pitch, Mark and End with snapping to pauses, flagged sections with their own speed and repeats, Join into one track, the sleep timer and offline use. It now fills the whole window, with the library on the left, a large waveform in the middle and your flags on the right.

What's new:

- **A waveform you can zoom like in Audacity.** Scroll the mouse wheel over the waveform to zoom in or out at the pointer. You can go from the whole recording down to single sound waves (2/100 of a second across the screen). Shift + wheel, or a sideways swipe on a touchpad, scrolls left and right. The strip above the waveform always shows the whole recording, with a box around the part you're looking at: drag the box to move around, or double-click the strip to see everything. **Follow** keeps the playhead in the middle while it plays, so the waveform scrolls past it.
- **Select by dragging.** Drag across the waveform to loop that part. Double-click a phrase to loop it from the pause before it to the pause after it. You can still press **M** as a phrase starts and again as it ends. Drag A or B to trim; click inside the section to play on from that point.
- **Lock the length and move it.** Press **Lock length** (or **L**). Then drag the section, or click anywhere on the waveform, to move it along the recording without changing its length. ‹ › move it 0.1 s. The double arrows (or **[** and **]**) jump by one whole length, so you can work through a recording in equal pieces. Click the length (for example "2.00 s") to type an exact length. If you move a saved flag, the flag stays where it was; press Save to keep the new place as another flag.
- **Flags on screen.** Flags are listed on the right (as chips under the waveform in narrower windows) and drawn in a lane under the waveform. Click one, or press **1–9**, to loop it. Right-click a flag to rename it, delete it or move it to the current section.
- **Keyboard shortcuts** for everything. The list is in the right-hand panel and behind the **?** button.

## Put it online (GitHub Pages)

1. On the **same GitHub account** as Echo Loop+, create a new public repository, for example `echo-loop-desktop`. Upload every file in this folder and keep the file names as they are.
2. In the repository, open **Settings → Pages** and choose **Deploy from a branch → main → / (root)**. Save.
3. After a minute, open `https://<your-username>.github.io/echo-loop-desktop/` in **Chrome** or **Edge** on your computer.
4. Click **Install app** at the top right of the page, or the install icon at the right end of the address bar. The app opens in its own window and gets a Start-menu entry and a taskbar icon. You can install it alongside Echo Loop+.
5. Open it once while online. When the badge says **Offline ready**, it works without internet.

## Your library comes with you

Your recordings, play counts and flags are stored in the browser on your computer. Echo Loop+ and Echo Loop+ Desktop on the same GitHub account count as the same site, so they share one library in that browser. Everything you added in the Echo Loop+ window on this computer is already there when Desktop opens, and changes go both ways. Your iPhone keeps its own library, and nothing is uploaded anywhere.

**Keep only one of the two apps open at a time.** An older window left open in the background still holds its old copy of the library and can save it over newer changes. Desktop picks up changes made in the other app whenever you switch back to its window, but Echo Loop+ doesn't.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app |
| `sw.js` | Saves the app for offline use |
| `manifest.webmanifest` | App name, icon and colours used when it's installed |
| `icon-180.png`, `icon-192.png`, `icon-512.png` | App icons (a deeper blue than Echo Loop+, so you can tell them apart on the taskbar) |
| `make_icons.py` | Script that draws the icons (only needed if you want to change them) |

## Good to know

- **The first waveform** of a recording takes a second or two to draw; after that it's saved and opens instantly. Very long recordings (well over an hour) may show no waveform. Playback, sections and flags still work for them.
- **Media keys** (play/pause, next, previous) work while the window is in the background.
- **Narrow windows.** When the window is narrower, for example snapped to half the screen, the flags move under the waveform. Below about 880 pixels wide, the library opens from the list button at the top left.
- **Browsers.** Chrome and Edge can install the app and play MP3, M4A (including Voice Memos), WAV, FLAC and OGG files. Other browsers run it in a normal tab.
- **Updating later.** If you change any file, also change `eld-v1` to `eld-v2` (and so on) at the top of `sw.js`. The app picks up the new version the next time it's opened online.
