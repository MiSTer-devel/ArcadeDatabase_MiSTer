
# Arcade Database for MiSTer

  

The ArcadeDatabase_[MiSTer](https://github.com/MiSTer-devel/Wiki_MiSTer/wiki) repo contains files and lists about the different arcade core MRAs that are available for MiSTer.

  

# How to contribute

To make it easier for users to contribute, we now have automation.

If you want to add or update entries in the database, follow these simple steps:

  

1. Edit `ArcadeDatabase.csv` in the repository **root** (the delimiter is a comma; you can import it into Excel if you prefer).

  

2. Open a pull request with your edited `ArcadeDatabase.csv`.

  

3. **Do not edit anything in the `mad/` folder, or `mad_db.json`.** Those are generated automatically from the CSV by the automation script when your pull request is merged — touching them by hand will conflict with the regeneration.

  

4. Once the pull request is merged, the automation script processes the CSV and updates the database accordingly.

  

# Naming convention

Since it is important to know exactly what version of the game you play, I've decided to go for the following naming convention:

Game Name (Country, Version) [bl/hb].

Country should follow the [Alpha-2](https://www.iban.com/country-codes) country code.

[bl] means Bootleg

[hb] means Homebrew

  

# Preferred version

As you might've noticed, there are different versions/clones of the same game. Sometimes the preferred version is documented, and sometimes it is not. Basic rule of thumb is the following (from MAME doc):

  

```

- Prefer latest release version

- Prefer English language

- Prefer most widespread release

- Prefer most complete version

- Prefer versions that are uncensored, and have story/cutscenes intact

- Prefer versions that keep the original gameplay balance

- Prefer releases from original developers/publishers rather than licensees

- Prefer releases without region-specific notices or warnings

```

  

# rotation and flip

These two fields are the source of most confusion, so the rules are spelled out here. They are independent of each other.

  

**`rotation`** — the original arcade cabinet orientation, taken from MAME / [adb.arcadeitalia.net](https://adb.arcadeitalia.net) (the "ruotato di N°" value on a game's detail page):

  

```

  0°   = horizontal

  90°  = vertical (cw)

  270° = vertical (ccw)

```

  

This is the *original hardware* orientation. It is **not** how the MiSTer core happens to boot or display the game — do not set rotation from what you see on your screen, use MAME. Clones inherit their parent's rotation.

  

**`flip`** — `yes` only if the core provides a **persistent 180° screen flip that the player can reach and that stays applied** (a core OSD "rotate/flip" option, an OSD dipswitch-page toggle, or an in-game service-menu setting stored in NVRAM). It is `no` otherwise. Note:

  

- `flip` is **not** MAME's flip metadata.

- A flip option that merely *exists* is not enough — a toggle that does nothing, or a cocktail-cabinet mirror that doesn't correct the orientation, is `no`.

- Verify flip on real hardware.

  

**The MRA's own `<rotation>` and `<flip>` tags are hints and are sometimes wrong.** When they disagree with the above, MAME wins for `rotation` and hardware wins for `flip`.
