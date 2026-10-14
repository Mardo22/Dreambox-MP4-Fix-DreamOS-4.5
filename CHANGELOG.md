# Changelog – Dreambox MP4 Fix (Dreambox Two, DreamOS 4.5)

## 3.4.2 – 2026-10-14
- "Play now" after a conversion is offered after 60 s (10 s after a TEST MKV). Some hard
  disks – especially SSDs in USB cases – pause for a moment after several GB were written;
  playback started in that moment stalled, and pressing Pause/Play then could freeze the
  DreamOS player. Meanwhile the screen says the MKV is already in the movie list (PVR).
- A new MKV starts at 0:00 also from the normal movie list: the old AJPanel resume point of
  a deleted file with the same name is removed as soon as the MKV is ready.
- Help: new section "PLAY NOW AFTER A CONVERSION".

## 3.4.1 – 2026-10-14 (closed build)
- The plugin code is compiled to ARM64 machine code (Cython 0.29 + GCC 6.4 for Python 2.7).
  Only three short launchers stay readable: `plugin.py`, `worker.py`, `check.py`.
- Functions, design and behaviour are the same as in 3.4.
- Includes the late 3.4 fix: the audio protection no longer writes "not handled" to its log on
  every OK in the audio menu while watching IPTV channels (only files on the disk are checked).
- `check.py` also checks the compiled modules and that no readable source code is left.
- Package architecture is now `arm64` (was `all`).

## 3.4 – 2026-10-12
- Paused audio switch protection: on DreamOS 4.5 (GStreamer 1.10.4) choosing another audio
  track while a movie is PAUSED freezes the player. For MKVs made by the plugin the movie now
  plays for about 1.5 s, the track changes and the pause returns. Active from the start of
  Enigma2, also for movies started from the normal movie list.
- Every hook into the DreamOS audio menu is guarded – an unexpected error is written to
  `/tmp/dreamboxmp4fix-audio.log` and the standard DreamOS behaviour is used.
- Menu (Blue) > "Paused audio switch protection: ON/OFF" – takes effect at once and is
  remembered after a restart.
- Fixed: after STOP > "Restart from the beginning" or "None" the movie was not protected.
- Fixed: Menu on an MP4 that already has an MKV played the MP4 (stalls at 0:00); it now plays the MKV.

## 3.3 – 2026-10-08
- Cleaner plugin list and footer, single-line YouTube channel and QR hint, compact About.

## 3.2.1 – 2026-10-05
- "Play now" starts the new MKV at 0:00 (clears the AJPanel resume point of an old file with the same name).
- Menu: "Play from the beginning" and "Continue at mm:ss".
- Folders are read in the background – a sleeping hard disk no longer freezes the GUI.

## 3.2 – 2026-10-05
- Native Dreambox look: movie details card, track summary, QR code of the SetTvBox4U channel.

## 3.1 – 2026-10-02
- Yellow = Quick MKV / TEST 1-2-3 min, Blue = Menu. Clean subtitles (no `<font>` tags in the MKV).
