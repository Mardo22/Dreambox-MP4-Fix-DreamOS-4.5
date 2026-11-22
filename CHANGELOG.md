# Changelog – Dreambox MP4 Fix (Dreambox Two, DreamOS 4.5 and DreamOS 5)

## ⚠️ LEGAL NOTICE · تنبيه قانوني ⚠️

> [!CAUTION]
> **AR:** نحن لا ندعم المشاهدة أو النسخ أو النشر غير القانوني للأفلام أو المحتوى التلفزيوني. هذه الإضافة تحوّل فقط ملفات الفيديو التي تملكها وحصلت عليها بطريقة قانونية، ولا تقوم ببث أي محتوى ولا بفك أي تشفير. هذا الدليل وجميع فيديوهاتنا لأغراض تعليمية فقط.
>
> **EN:** We do not support illegal viewing, copying or distribution of films or TV content. This plugin only converts video files that you own and obtained legally – it does not stream anything and does not decrypt anything. This guide and all our videos are for educational purposes only.
>
> **SK:** Nepodporujeme nelegálne sledovanie, kopírovanie ani šírenie filmov či televízneho obsahu. Plugin prevádza len vaše vlastné, legálne získané video súbory – nič nestreamuje a nič nedekóduje. Tento návod aj všetky naše videá slúžia len na vzdelávacie účely.
>
> **DE:** Wir unterstützen kein illegales Ansehen, Kopieren oder Verbreiten von Filmen oder TV-Inhalten. Dieses Plugin wandelt nur Ihre eigenen, legal erworbenen Videodateien um – es streamt nichts und entschlüsselt nichts. Diese Anleitung und alle unsere Videos dienen nur Lernzwecken.
>
> **GA:** Ní thacaímid le féachaint, cóipeáil ná scaipeadh mídhleathach scannán ná ábhar teilifíse. Ní thiontaíonn an breiseán seo ach comhaid físe atá agat féin agus a fuair tú go dleathach – ní shruthaíonn sé aon rud agus ní dhíchriptíonn sé aon rud. Is chun críocha oideachais amháin atá an treoir seo agus ár bhfíseáin go léir.

## 3.4.3 – 2026-11-21
- Fixed: on DreamOS (seen on DreamOS 5 / Titanium) Enigma2 crashed when the Extensions list
  (long GREEN) was opened. DreamOS reads the menu functions of every plugin with
  `inspect.getargspec()`, which rejected the compiled functions of 3.4.1 / 3.4.2. Since 3.4.3
  `plugin.py` hands Enigma2 plain Python functions; the list opens normally and the plugin
  starts from it.
- `check.py` also checks that the menu entries can be read this way (`MP4FIX_CHECK_OK version=3.4.3`).
- One package for DreamOS 4.5 and DreamOS 5. Tested on Titanium AIO 20261117 (enigma2 5.0.0r2):
  Extensions list, Plugin Browser, a 4K MP4 with 8 subtitle tracks → MKV with 5 chosen subtitles,
  Play now in 4K.
- About now names DreamOS 4.5 and 5. Nothing else changed – conversion, design and
  behaviour are the same as in 3.4.2.

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
