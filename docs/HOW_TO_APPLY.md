# How to apply the patch

This turns *your own* clean Japanese ROM into the English version. The patch contains only
the changes (the translation) — you supply the game.

## 1. Get the right source ROM

You must dump it from a cartridge you own. The patch is built for one exact file:

| Field | Value |
|---|---|
| Title | Tomodachi Collection (Japan) |
| Game code | `CCUJ` |
| Version | 1.1 (version byte `0x01`) |
| File size | 67,108,864 bytes (64 MB) |
| MD5 | `7AB6ACD97168F6D70E953A9C8057337C` |

If your ROM's MD5 doesn't match, the patch will refuse to apply (or produce a broken file).
Other dumps/revisions won't work — it has to be **v1.1**.

> **How to check a file's MD5**
> - Windows (PowerShell): `Get-FileHash yourfile.nds -Algorithm MD5`
> - macOS: `md5 yourfile.nds`
> - Linux: `md5sum yourfile.nds`

## 2. Apply the patch

### Option A — GUI (recommended for most people)

1. Download **[Delta Patcher](https://github.com/marco-calautti/DeltaPatcher/releases)**.
2. Open it.
3. **Original file** → your clean `Tomodachi Collection (Japan).nds`.
4. **XDelta patch** → `Tomodachi_Collection_EN_v1.0.xdelta` (from this repo).
5. Click **Apply patch**. It writes the English `.nds` next to your original.

### Option B — Command line (xdelta3)

```
xdelta3 -d -s "Tomodachi Collection (Japan).nds" Tomodachi_Collection_EN_v1.0.xdelta Tomodachi_Collection_EN_v1.0.nds
```

- `-d` = decode/apply, `-s` = source (your clean ROM).
- Get xdelta3 from your package manager (`brew install xdelta`, `apt install xdelta3`) or the
  [official releases](https://github.com/jmacd/xdelta-gpl/releases).

## 3. Verify the result

The patched English ROM should be:

| Field | Value |
|---|---|
| File size | 56,917,096 bytes (~56.9 MB) |
| MD5 | `BB0B1D0C6E3FCF427037B1F9CC16E3DE` |

If the MD5 matches, you have a clean, correct English build. If it doesn't, re-check that
your source ROM matched the MD5 in step 1.

## 4. Play it

Copy the patched `.nds` to your flashcart or to your TWiLightMenu `games` (or `roms/nds`)
folder. Saves are compatible with the unpatched Japanese game (same game code), so you can
switch between them.

For real-console specifics and the anti-piracy note, read
**[PLAY_ON_HARDWARE.md](PLAY_ON_HARDWARE.md)**.
