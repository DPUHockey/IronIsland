# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Iron Island Fight League (IIFL) — a browser-based, text/HTML prototype of a career-progression
combat-sports sim (think GTA-style free roam + Blood Bowl-style play-by-play + a deep league sim
underneath). It's the pre-production phase before any real-art investment; the full design intent
lives in `iron_island_gdd.md` — read it before making systems-level changes (calendar/season
structure, disciplines, weight classes, league/draft rules, career roles, etc.), since the code is
the implementation of that document, not the other way around.

## Running the game

There is no build step, package manager, or server. Each `.html` file is a fully self-contained
page (inline `<style>` and `<script>`, no external JS/CSS files, no bundler). Just open a file
directly in a browser, or serve the directory statically if you need `fetch`/relative-path behavior
to match production hosting:

```
python -m http.server 8000   # then visit http://localhost:8000/
```

`index.html` is a pure redirect (`window.location.replace('iifl_home.html')`) plus a marketing/tools
landing page — it is not part of the play loop.

There are no tests, linters, or CI in this repo. Verify changes by opening the relevant page in a
browser and exercising the flow by hand.

## Architecture

### One save = one localStorage namespace

All persistent state lives in `localStorage`. The core mechanism is `sk()` (save-key), defined
identically in every file: it wraps every storage key with the *active save's* id so each save is a
fully independent world (own clock, roster, field pools, fight results). `sk(ROSTER_KEY)` resolves to
`iifl_save_<id>__iifl_roster_v1`. A few keys are deliberately **not** save-namespaced because they're
global: `iifl_save_registry_v1` (the registry of saves + which one is active) and
`iifl_created_fighters_v1` (the catalog of fighters built in the Character Creator, independent of
any save until explicitly added to one — see `iifl_home.html` around the `SAVE_REGISTRY_KEY` /
`CREATED_FIGHTERS_KEY` block for the full model).

When adding new persistent state, always read/write it through `sk(SOME_KEY)`, never a raw key,
unless it's genuinely meant to be shared across every save.

### Every file is self-contained by design — logic is duplicated, not shared

There is no shared JS module, no `<script src>` include between files, and no build step to
de-duplicate code. Helpers like `rand()`, `pick()`, `clamp()`, the calendar/season math
(`resolveTierSeason`, `tierKeyDates`, etc.), and even fight-simulation logic are **copy-pasted into
each file that needs them**, by explicit intent (see the comment at the top of `iifl_home.html`'s
script block: "mirrored from iifl_fight_pit.html so this file is fully self-contained, same pattern
used across every other file in the game").

Concretely, fight resolution is implemented independently in at least three places —
`simulateFight()` in `iifl_fight_engine.html`, `simulateBout()`/`quickSimBout()` in
`iifl_fight_pit.html`, and `runFightCardSim()` in `iifl_junior_league.html` — and they are **not**
guaranteed to be in sync. `iifl_fight_engine.html` is the reference/prototype engine; it is linked
from `index.html`'s tools list but not invoked by the other pages.

**Implication for changes:** if you fix a bug or tune a formula in shared logic (calendar math, a
discipline matchup calc, a stat-roll formula, `sk()`/save-registry helpers, etc.), you almost always
need to port the same fix into every other file that has its own copy, not just the one you're
looking at. Grep across all `.html` files for the function/constant name before assuming a one-file
fix is complete. Several comments call this out explicitly where it's most error-prone (e.g.
`iifl_home.html`'s `leagueSeasonOpenDay`/`jrSeasonFirstThursday` comment: "Mirrors ... in
iifl_junior_league.html — same math, kept in sync manually").

### Page map / navigation flow

- `iifl_home.html` — hub/dashboard: active save's fighter status, career tier, calendar, mode links.
- `iifl_character_creator.html` — fighter creation + the "Sequencing Event" stat-roll flow.
- `iifl_free_roam.html` — the weekly point-budget city loop (train, walk, socialize, mini-games).
- `iifl_junior_league.html` — Junior League tier: draft, schedule, standings, playoffs.
- `iifl_fight_pit.html` — Juvenile/Amateur fight-pit loop and card simulation.
- `iifl_fight_engine.html` — standalone reference fight-simulation engine/tool.
- `index.html` — redirect to `iifl_home.html` + a tools landing page (not part of play flow).

Navigation between pages is plain `window.location.href` to another `.html` file (sometimes with a
query string, e.g. `iifl_junior_league.html?screen=league-night`) — there is no client-side router.

### The island calendar

One shared, save-scoped clock (`CLOCK_KEY`, day-number based, `GAME_EPOCH` = Monday, March 3 1958 =
Day 1). Each career tier (juvenile/junior/amateur/pro) has its own annual regular-season + playoff
window defined in `TIER_SEASON_CONFIG` and resolved *statelessly* from the day number via
`resolveTierSeason()` / `tierKeyDates()` — there is no separately stored "current season phase" to
drift out of sync; a given day number always recomputes the same season/phase. When touching
calendar logic, preserve this derive-don't-store approach and keep the mirrored copies (see above)
in sync.

### Versioning convention

Each page carries its own independent version badge in-page (e.g. `FREE ROAM · V95 · 2026-07-21`,
`FIGHT PIT · V52 · 2026-07-21`) — files version independently, not as a single app version. When you
make a meaningful change to a page, bump that page's own badge/date rather than inventing a
repo-wide version.

## Provincial Flags / settlementmaps

`Provincial Flags/*.jpg` and `settlementmaps/*.png` are static art assets referenced by the province
and settlement data described in `iron_island_gdd.md` §2. Settlement lists/names in the GDD are
explicitly flagged as placeholders in several provinces — don't treat names/populations there as
final without checking the GDD's own "Open item" notes in §2.1 and §15.
