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
- **⭐ Pick your team** (optional) on the Home screen — it's starred everywhere, gets a tag in
  live matches, extra confetti on its goals, and a special message if it wins the cup.
- **🎲 Draw the Groups & Start** — 48 teams are drawn into 12 groups (seeded pots, like the
  real draw; the three hosts USA/Mexico/Canada are seeded).
- **Group stage** — each fixture has **▶ Play** (live) or **Quick** (instant). Or use
  **⚡ Simulate all groups**. Top 2 of every group plus the **8 best third-placed** teams
  advance (32 teams).
- **Knockout** — a full bracket: Round of 32 → R16 → Quarter-finals → Semi-finals → Final,
  plus a 3rd-place playoff. A level tie goes to **extra time**, then a **penalty shootout**.
  Play each tie or simulate the round / the whole bracket.
- **🏆 Champion** — trophy, confetti, and the medal table.

## Features
- **Two languages** — English and **European Portuguese**, switchable any time via the
  **EN / PT** toggle in the header (country names, UI, commentary, and round names are all
  translated). Your choice is remembered.
- **Team editor** — the **Teams** tab lists every team; tap one to see its squad and four
  quality sliders (**Attack / Midfield / Defense / Goalkeeping**) that combine into an
  **Overall** rating. Move the sliders to make a team stronger or weaker — it really changes
  their chances (a maxed-out minnow beats a nerfed favourite ~90% of the time). Goalkeeping
  also swings penalty shootouts. Edits persist. Each team has its own **↺ Reset ratings**
  button, and the Teams tab has an **↺ Reset all teams** button to restore every team's
  defaults at once.
- **Live commentary** during Play matches, with occasional colour between the goals.
- **Stats tab** — Golden Boot top-scorer race, Golden Glove, biggest win, most goals, goals
  per match, and per-team stats on each team's page.
- **Auto save & resume** — your tournament (and any team edits) are saved to the browser
  automatically; close the tab and pick up right where you left off.

## How results are decided
Every team has **Attack / Midfield / Defense / Goalkeeping** ratings (derived from FIFA
rankings plus a little style — Brazil attack-heavy, Italy defense-heavy, Argentina/Belgium/
Morocco strong in goal, etc.). Each match's goals are simulated minute-by-minute: a team's
chances come from **its attack vs the opponent's defense** (defense itself is a blend of
Defense, Midfield and Goalkeeping), weighted but **deliberately compressed** so favourites win
only ~60% of the time. Underdogs win often, so every team has a real shot (across many
simulations, 40+ different teams end up champions). In a penalty shootout, each kicker's
success chance is their team's Overall rating vs the **opposing goalkeeper's Goalkeeping**
rating — a great keeper really can win a shootout.

## Notes
- Player names shown as scorers are well-known real players used for flavour; they're
  illustrative, not official 2026 squad lists.
- Tune the overall feel by editing constants near the top of the script in `index.html`:
  `GOAL_BASE`/`KGOAL` (how much ratings matter), and the `STYLE` map (per-team attack/defense/
  goalkeeping tilt). Kids can adjust individual teams live via the sliders — no code needed.
