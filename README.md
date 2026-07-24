# ⚽ World Cup 2026 Simulator

A single-page, no-server web game that simulates the **48-team FIFA World Cup 2026** —
the group draw, the group stage, and the full knockout bracket right through to the final.
Built for kids to play: pick any match to **watch the goals go in live** over 90 minutes, or
**skip straight to the score**.

Everything is in one file (`index.html`) — no build step, no backend, no dependencies to
install. The only thing it fetches from the internet is real country flags (from
[flagcdn.com](https://flagcdn.com)), so an internet connection makes it look its best.

## Play it locally
Just double-click `index.html`, or:
```bash
# optional: serve it (any static server works)
python3 -m http.server 8000
# then open http://localhost:8000
```

## Live site
Served via GitHub Pages at **https://www.xavieranguera.com/worldcup**.

This lives in its own repo (`xanguera/worldcup`) but is published under the custom domain of
the user site `xanguera.github.io`. Because that user site owns `www.xavieranguera.com`, this
*project* site is automatically served at `www.xavieranguera.com/worldcup` — the URL path is
simply the repo name, which is why the repo must be named `worldcup`.

### To (re)enable Pages on this repo
1. **Settings → Pages**.
2. **Build and deployment → Source = Deploy from a branch**, branch = `main`, folder =
   `/ (root)`, then **Save**.
3. Wait ~1 minute; then open https://www.xavieranguera.com/worldcup.

## How to play
- **🎲 Draw the Groups & Start** — 48 teams are drawn into 12 groups (seeded pots, like the
  real draw; the three hosts USA/Mexico/Canada are seeded).
- **Group stage** — each fixture has **▶ Play** (live) or **Quick** (instant). Or use
  **⚡ Simulate all groups**. Top 2 of every group plus the **8 best third-placed** teams
  advance (32 teams).
- **Knockout** — a full bracket: Round of 32 → R16 → Quarter-finals → Semi-finals → Final,
  plus a 3rd-place playoff. Draws are decided by a **penalty shootout**. Play each tie or
  simulate the round / the whole bracket.
- **🏆 Champion** — trophy, confetti, and the medal table.

## How results are decided
Each team has a strength rating derived from FIFA rankings. A match's goals are simulated
minute-by-minute, weighted by the two ratings — **but deliberately compressed** so favourites
only win ~58% of the time. Underdogs win often, so every team has a real shot (across many
simulations, 40+ different teams end up champions).

## Notes
- Player names shown as scorers are well-known real players used for flavour; they're
  illustrative, not official 2026 squad lists.
- Tune the feel by editing two constants near the top of the script in `index.html`:
  `DAMP` (higher = favourites win more) and `BASELINE`.
