# SA-1 Root: Contra III

Contra III: The Alien Wars is the third Contra game made by Konami and an amazing
cinematic shooting game.

This SA-1 Root removes all slowdown present on the original game and drastically
reduces the loading times. It also saves the high scores and settings.

## How to Patch

Download the latest Contra III .bps patch file available on the
[Releases](https://github.com/VitorVilela7/SA1-Root/releases) tab.

You can patch it using [beat](https://www.romhacking.net/utilities/893/)
or [FLIPS](https://smwc.me/s/11474), both common .bps patchers.

You can also patch the .asm files directly using
[Asar](https://github.com/RPGHacker/asar).

It works only on the american version of Contra III. Contra Spirits and Super
Probotector does not work because both games were recompiled and its codes are
different compared to the american version. Depending on the demand I might
do them eventually, but they will likely require the same amount of effort as
a new game conversion.

Expected checksums:

### USA Version:
#### Before patching:
* CRC32: XXXX
* SHA256: XXXX

#### After patching
* CRC32: XXXX
* SHA256: XXXX

## Compatibility

It works on both real hardware (sd2snes or SA-1 cart) and emulators (Snes9x and bsnes/higan).

## Technical details

* Remapping mode: Full
* Remapping strategy: Runtime
* SA-1 usage: Aggressive

This game has a very complex data structure. Even more compared compared to Gradius III.
Direct page, indirect addressing and shared ROM/RAM pointers are pretty common on this game.
For that, I had to remap the entire RAM memory to the BW-RAM and for the data structures
that referenced banks 7E/7F were most of the time remapped by runtime for not having
to mine over 950KB of data structures.

SA-1 was used for the maximum time possible and a callback system was used for the SA-1
CPU calling back the SNES CPU when running on routines that it can't handle (APU uploads
and PPU updates mostly).

Because of the strategy used,
**128 kB (1024 Kbit) of BW-RAM is required to the game run** correctly.

## RAM remap

* ``$0000-$1FFF`` -> ``$6000-$7FFF``
* ``$7E:0000-$7F:FFFF`` -> ``$40:0000-$41:FFFF``