# Dreambox MP4 Fix - DreamOS 4.5

**Makes 4K MP4 movies playable on Dreambox Two with DreamOS 4.5.**

**Designed by Mardo22** · YouTube: **[SetTvBox4U](https://www.youtube.com/@SetTvBox4U)** · Contact: settvbox4u@gmail.com

MP4 files with several subtitle tracks often stall at 0:00 in the DreamOS movie player.
Dreambox MP4 Fix copies the video and audio **bit for bit** (no re-encoding, no quality loss)
into a verified MKV file that keeps **every audio track, every text subtitle and 5.1 sound** –
and the MKV plays normally on the Dreambox.

| | |
|---|---|
| Receiver | Dreambox Two (`two`), ARM64 |
| Image | DreamOS 4.5 (Gemini 4.2 / OE 2.6, Enigma2 4.5, Python 2.7.13) |
| Package | `enigma2-plugin-extensions-dreamboxmp4fix_3.4.2_arm64.deb` |
| Version | 3.4.2 (closed build) |
| License | Free to use, all rights reserved – see [LICENSE](LICENSE) |

> This package is built **only** for Dreambox Two with DreamOS 4.5. It contains ARM64 machine
> code for Python 2.7 and will not work on other receivers or images (DreamOS 5.0, OpenATV,
> OpenBlackHole, …).

## Video tutorial – how to use the plugin

[![Dreambox MP4 Fix on Dreambox TWO / DreamOS 4.5 – video tutorial](https://img.youtube.com/vi/DQRSgdQDlFE/hqdefault.jpg)](https://www.youtube.com/watch?v=DQRSgdQDlFE)

▶ **[Watch on YouTube: Dreambox MP4 Fix on Dreambox TWO / DreamOS 4.5](https://www.youtube.com/watch?v=DQRSgdQDlFE)** (Arabic voice-over)

The video shows version 3.3; version 3.4.2 is used the same way.
More tutorials on the channel **[SetTvBox4U](https://www.youtube.com/@SetTvBox4U)**.

## Features
- Native Dreambox look: movie list with date, codec and length, movie details card, track summary.
- **Yellow** = Quick MKV (one key) or a 1 / 2 / 3 minute TEST file.
- **Blue** = Menu: Play now, Play from the beginning, Help, Log, About, audio protection on/off.
- All audio tracks and all text subtitles are kept (subtitles become clean SRT in the MKV);
  the Slovak track is selected first when it exists.
- A new MKV starts at 0:00 - with "Play now" and from the normal movie list (an old AJPanel
  resume point of a deleted file with the same name is removed).
- "Play now" is offered 60 s after a full MKV (10 s after a TEST MKV): some hard disks,
  especially SSDs in USB cases, pause for a moment after several GB were written.
- Folders are read in the background – a sleeping hard disk no longer freezes the GUI.
- **Paused audio switch protection**: on DreamOS 4.5 (GStreamer 1.10.4) choosing another
  audio track while a movie is PAUSED freezes the player. For MKVs made by the plugin the movie
  plays for about 1.5 s, the track changes and the pause returns. Can be switched off in Menu.
- Entry in the movie list menu (MENU on a movie > Dreambox MP4 Fix).

## Installation
1. Download `enigma2-plugin-extensions-dreamboxmp4fix_3.4.2_arm64.deb` and `SHA256SUMS.txt`
   from the latest **[Release](../../releases/latest)** and copy the `.deb` to `/tmp` on the
   receiver (FTP, USB stick or network share).
2. Check the file: `sha256sum /tmp/enigma2-plugin-extensions-dreamboxmp4fix_3.4.2_arm64.deb`
   must match `SHA256SUMS.txt`.
3. On the receiver: **MENU > Setup > Software management > Install local extension >
   Internal Flash (/tmp)** > select the package > **Green = Install**.
   Or in a terminal: `dpkg -i /tmp/enigma2-plugin-extensions-dreamboxmp4fix_3.4.2_arm64.deb`
4. **Restart the GUI** (MENU > Standby / Restart > Restart GUI).
5. Open **Plugins > Dreambox MP4 Fix**.

Optional check in a terminal:

```
python /usr/lib/enigma2/python/Plugins/Extensions/DreamboxRemux/check.py
```

The last line must be `MP4FIX_CHECK_OK version=3.4.2`. The check does not convert anything and
does not touch Enigma2, movies or settings.

### Update from an older version
Install the new package the same way – the old version is replaced and your movies and
settings stay untouched.

### Uninstall
In a terminal:
`dpkg -r enigma2-plugin-extensions-dreamboxmp4fix`. Movies and MKV files are never deleted.

## Requirements
- `ffmpeg` (installed on DreamOS 4.5 by default, the package depends on it).
- Free space on the target disk for the new MKV (about the size of the MP4).

## What the plugin does NOT do
- It does not re-encode video and does not change the original MP4.
- It does not install or replace system multimedia libraries.
- It does not delete movies. Test files and unfinished files go to `.Trash` only after you confirm.
- It does not connect to the internet.

## Closed build
Since 3.4.1 the plugin code is compiled to ARM64 machine code. Only three short launchers are
readable: `plugin.py` (registration for Enigma2), `worker.py` (starts the background worker)
and `check.py` (receiver check). Decompiling or modifying the plugin is not allowed – see
[LICENSE](LICENSE).

## Support
YouTube: [SetTvBox4U](https://www.youtube.com/@SetTvBox4U) – tutorials for the plugin, [how to use Dreambox MP4 Fix](https://www.youtube.com/watch?v=DQRSgdQDlFE).

Unofficial plugin. Dreambox and DreamOS are names of their respective owners.
