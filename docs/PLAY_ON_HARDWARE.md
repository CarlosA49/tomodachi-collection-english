# Playing on real hardware (DSi / 3DS / flashcart)

The English ROM runs anywhere the Japanese original does — but Tomodachi Collection ships
with an anti-piracy library called **DS Protect**, and that catches a lot of people. Read
this before you panic at a crash.

## The short version

Use **TWiLightMenu++ with nds-bootstrap v2.16.0 or newer**. Current nds-bootstrap applies
the anti-piracy fix for this game **automatically** — you don't have to do anything special.

## The anti-piracy crash (and why it happens)

If your loader is **out of date**, the game will:

1. Boot fine, let you set the clock, and let you **name your island**…
2. …then **deliberately crash the instant it saves** — typically a red
   `Error: Data Abort! ADDR: 00000000` screen — and wipe the just-made save.

That is **not a bug in the translation.** It's DS Protect detecting that the anti-piracy
check wasn't satisfied (an old or mismatched loader) and intentionally killing the game at
the first save. The same thing happens to the untranslated Japanese ROM on the same setup.

### The fix

**Update your loader.** On a DSi/3DS:

1. Grab the latest **[TWiLightMenu++](https://github.com/DS-Homebrew/TWiLightMenu/releases)**
   (it bundles the matching **[nds-bootstrap](https://github.com/DS-Homebrew/nds-bootstrap/releases)**).
2. Copy its `_nds` folder onto your SD card root, replacing the old one.
3. Delete any existing Tomodachi `.sav` so it starts clean (DS Protect already erased it
   anyway), then relaunch and name the island again.

nds-bootstrap v2.16.0+ recognizes both the Japanese ROM and **modified/translated copies of
it** and patches the anti-piracy check at boot, in memory. Nothing is changed on disk.

## Flashcarts

Behavior varies by cart and firmware. Older AceKard/R4 clones may need their own
anti-piracy handling or a recent kernel (e.g. YSMenu/Wood). If your cart can't satisfy DS
Protect, you'll see the same crash-after-naming. A current DSi/3DS + TWiLightMenu setup is
the most reliable path.

## Saving

Saves use the same format as the unpatched Japanese game (same `CCUJ` game code), so a save
made on the Japanese ROM works on the English one and vice-versa.

## Notes

- Tested via TWiLightMenu++ / nds-bootstrap v2.16.0 on a DSi XL, and in BizHawk 2.10
  (melonDS core). Emulators don't enforce DS Protect, so a translation can look fine in an
  emulator and still hit the anti-piracy crash on real hardware with an old loader — keep
  your loader current.
