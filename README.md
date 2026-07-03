# 🚩 THE LINESMAN — Offside Career

A soccer offside-judging game built for **iPhone 16 Pro**. You are the
assistant referee. Watch the pass, watch the defensive line, and make the
call — climb the English football pyramid from Sunday League mud all the
way to the Premier League.

## The game

- **First-person, through the linesman's eyes.** You stand on the touchline
  and automatically side-step to stay level with the second-last defender —
  the vertical hairline on the turf is your sight line, exactly how real
  assistant referees work. Drag to glance toward the ball, at the cost of
  taking your eye off the line.
- **Career mode across 7 tiers**: Sunday League → County League → National
  League → League Two → League One → Championship → Premier League.
- Each matchday is a series of offside **decisions**: the attack builds on
  your left, the through-ball is struck (thump + flash), and you must hit
  **FLAG** or **PLAY ON** before the window closes. Flag too early or
  freeze entirely and you're punished either way.
- **Real offside law**: judged at the moment the ball is played, against the
  second-last defender. Level is onside. You can't be offside from a
  backward pass or in your own half — the game throws these trick scenarios
  at you in the higher tiers.
- **Review after every call**: a freeze-frame at the moment of the pass with
  the true offside line painted on the turf, TV-style, and your margin in
  metres.
- Margins tighten and play speeds up as you climb. Pass the assessor's mark
  to get promoted; a shocker can get you **demoted**.
- **Atmosphere scales with the pyramid**: overcast park pitches, hedges and
  mud in Sunday League up to floodlit night stadiums with packed stands in
  the Premier League. Full perspective 3D projection, depth fog, film grain
  and vignette, realistic player proportions with kits and shirt numbers,
  synthesized crowd/whistle/kick audio, haptics where supported. Career
  progress saves on-device (localStorage).

## Play it on your iPhone

The game is a single self-contained web app — no build step, no server code.

1. Host the repo as a static site (easiest: enable **GitHub Pages** on this
   branch, or run `python3 -m http.server` and open it on your phone over
   the local network).
2. Open the URL in Safari on your iPhone.
3. Share → **Add to Home Screen**. It installs as a full-screen app with its
   own icon, works offline (service worker), and respects the Dynamic
   Island / home-indicator safe areas.

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire game (rendering, physics, career logic, audio, UI) |
| `manifest.webmanifest` | PWA manifest (fullscreen, portrait, icons) |
| `sw.js` | Service worker for offline play |
| `icons/` | Home-screen icons |

## How offside is judged (in-game logic)

At the exact frame the pass is struck the game records every position. The
striker is offside only if **all** of these hold:

1. He is in the opponents' half.
2. He is ahead of the ball.
3. He is beyond the **second-last** defender (keeper counts) — dead level
   is onside.

Your call is compared against that truth; the VAR screen shows the line and
the margin so every mistake teaches you something.
