# Eglantine-MKW-DynamicFPS
Eglantine - unofficial build with Mario Kart World dynamic FPS
==============================================================

BASED ON: Eglantine build-64 (+ PR #82)
GAME VERSION: Mario Kart World 1.8.0 (tested). 1.0.0 should work (same code found),
              but dynamic FPS was not tested on it.

Based on Eglantine (https://github.com/Djihads80/Eglantine), branch nx2, build-64 + PR #82,
commit 20262163d1, with the changes in SOURCE-CHANGES.patch (source code of this build, GPL-3.0).

What's new (Graphics > Advanced, all off by default, take effect at the next game launch):
- "Mario Kart World: dynamic FPS (experimental)": no more slow motion below 60 fps, and never
  faster than 60. The game uses its own dynamic frame-rate mode and skips a vblank on slow
  frames to keep normal speed. Tested on MKW 1.8.0 in real races: same fps as without it, but
  97-100% game speed instead of 57-82%. Takes precedence over the 30 FPS mode.
  It does not raise your fps: it only keeps the game at the right speed.
- "Mario Kart World: 30 FPS mode": keeps the game in its own 30 fps mode.
- "Mario Kart World: smoother 30 FPS (experimental)": with the 30 FPS mode, one more frame
  ahead (fewer drops to 20 fps, about 33 ms more input delay). Turn it off if the game freezes.
- Fix for a crash on corrupt GPU command lists (invalid syncpoint id).
- Small GPU thread optimizations; Release build with LTO and AVX2 (needs a CPU with AVX2).

How to install and use
----------------------
1. Unzip the folder anywhere (for example on your desktop).
2. Run eglantine.exe. If Windows SmartScreen warns you: "More info" > "Run anyway".
3. First time only: install your own keys and firmware (Tools > Install decryption keys /
   Install firmware), then add your game folder, like with any Eden/Eglantine build.
   Already use Eglantine? You can copy your old "user" folder next to eglantine.exe to keep
   your keys, saves and settings.
4. Right-click Mario Kart World > Configure Game (or Emulation > Configure > Graphics),
   tab "Advanced", tick "Mario Kart World: dynamic FPS (experimental)".
5. Start (or restart) the game. That's it: below 60 fps the game keeps its normal speed.
   Don't tick the 30 FPS mode at the same time (dynamic FPS takes precedence anyway).

!! STILL EXPERIMENTAL: you might get lower fps than before on your PC.
   If you do, just untick the option.

Having issues? Send your log:
1. Reproduce the problem (play until it happens), then close the game.
2. In Eglantine: File > Open Eglantine Folders > Log Folder.
   (Or by hand: the "user\log" folder next to eglantine.exe, or %APPDATA%\eden\log
   if you have no "user" folder.)
3. Take the file eden_log.txt (do NOT relaunch the game first, it gets replaced on each launch).
4. Open an issue on the GitHub repo where you downloaded this build: describe the problem
   (game version, circuit, your CPU/GPU, fps) and attach eden_log.txt.

Requirements: Windows 10/11 64-bit, a CPU with AVX2, a Vulkan GPU, your own dumps.

Recommended per-game settings for Mario Kart World:
  GPU accuracy: Low, ASTC recompression: BC3, Async shaders: on, Async presentation: on,
  Reactive flushing: off, Force max clocks: on.

Not included: keys, firmware, games, Lossless Scaling. Use your own dumps.
