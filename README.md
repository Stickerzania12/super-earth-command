# Super Earth Command

A Helldivers 2 loadout terminal: randomized loadouts that respect the game's real
stratagem restrictions, a browsable Warbond library, and equipment ownership tracking.

**Live site:** https://__USER__.github.io/super-earth-command/

## What it does

- **Standard randomizer** — one primary, one secondary, one grenade, one body armor and
  four stratagems, drawn only from equipment you own. Pick which categories roll.
- **Democracy Roulette** — the same legal generator wrapped in a Ministry broadcast with
  a mission directive.
- **Squad Roulette** — up to four Helldivers; the pool is restricted to equipment every
  selected member owns, and unmet categories are named explicitly.
- **Warbond library** — all released Warbonds in release order plus the Superstore, with
  page-by-page browsing, item files and unlock status.
- **Ownership** — per-item unlocks, per-Warbond bulk unlock, purchase tracking kept
  separate from unlocks, multiple profiles, saved in local storage on your device.

### Stratagem rules enforced in code

1. At most one support weapon per loadout.
2. At most one backpack per loadout.
3. Support weapons that carry their own backpack count against both limits.
4. Remaining slots take any eligible stratagem.
5. A loadout may contain no support weapon and no backpack.
6. No duplicate stratagems.

Generation is rejection-sampled against those rules, then verified again before display,
so an illegal loadout cannot be presented as legal.

## Data

- 26 Warbonds plus the Superstore, in release order
- 721 reward entries, 204 of them randomizable equipment
- 97 stratagems: 49 unrestricted, 25 support weapons, 13 backpacks, 10 support weapons
  that include their own backpack
- 752 equipment images

Everything that could not be confirmed against a source is tagged **UNVERIFIED** in the
Dossier section rather than presented as fact.

## Testing

- 28 logic tests, including 20,000 generated loadouts with zero slot-rule violations
- 61 scripted UI tests in real Chrome: ownership filtering, squad intersection,
  persistence, jar page-flip navigation, routing, share codes
- Layout audited at 1440, 1180, 768 and 390px wide

## Notes and credits

Fan project. Not affiliated with, endorsed by, or sponsored by Arrowhead Game Studios or
Sony Interactive Entertainment. Helldivers and Helldivers 2 are trademarks of their owners.

Equipment and Warbond artwork comes from the community wiki at
[helldivers.wiki.gg](https://helldivers.wiki.gg), used here for a non-commercial fan tool
with attribution. If you own rights to an asset and want it removed, open an issue.

Single self-contained `index.html`: no build step, no tracking, no network calls at
runtime. Open it and it runs.
