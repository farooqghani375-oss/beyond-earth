# Beyond Earth — Space Exploration Experience

An immersive 8-page website built from the "Page-by-page UI/UX design styles" brief
(NASA space hackathon). Next.js 15 · React 19 · TypeScript · Three.js (react-three-fiber).
All planets/spacecraft are generated procedurally — no image or 3D-model downloads needed.

## Run
```bash
npm install
npm run dev      # http://localhost:3000
npm run build && npm start
```
Deploys to Vercel as-is.

## Pages → design styles
| Route | Page | Design styles applied |
|---|---|---|
| `/` | Landing | Cinematic UI, Minimalism, Hero section (3D Earth), Glassmorphism nav, Micro-interactions, Parallax stars |
| `/solar-system` | Solar system explorer | Immersive 3D, Spatial UI (labels in 3D), Glass panels, Card-based planet picker, Hover glow |
| `/moon-mars` | Moon & Mars | Environmental UI, HUD (live coords/telemetry), Glass panels, Parallax layers, Immersive scrolling |
| `/museum` | 3D artifact museum | 3D viewer, Split-screen, Card-based collection, Skeuomorphic zoom dial, Progressive disclosure |
| `/timeline` | Mission timeline | Horizontal timeline, Card-based, Editorial typography, Scroll-triggered animation, Progressive disclosure |
| `/discoveries` | Scientific discoveries | Dashboard UI, SVG data visualisation, Card-based, Information hierarchy, Minimalism |
| `/quiz` | Knowledge quiz | One-question-at-a-time cards, Gamification (points, streaks, badges), Instant feedback, Micro-interactions |
| `/beyond` | Final page | Cinematic UI, Typography-led, Fade transitions, Immersive storytelling |

Responsive Design and Dark Cinematic UI apply everywhere (tokens in `src/app/globals.css`).

## Where to edit content
`src/data/planets.ts` (planets) · `src/data/content.ts` (Moon/Mars chapters, artifacts, milestones, discoveries, quiz).

## Notes
- Exoplanet figures on `/discoveries` are rounded approximations — verify against the
  [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/) before final submission.
- Unofficial project; not affiliated with NASA.

## Narration (Listen buttons)
- **English:** uses the browser's built-in text-to-speech (nothing to set up).
- **Urdu (اردو):** plays pre-generated neural-voice mp3 files from `public/audio/ur/`.
  Chrome on many PCs has no Urdu system voice, so generate the files once (needs internet):
  ```bash
  npm install
  npm run audio:ur              # male voice (Asad)  — add  -- --female  for Uzma, or  -- --force  to redo
  ```
  Commit the generated `public/audio/ur/*.mp3` files so they deploy with the site.
  Scripts live in `src/data/urdu.json` — edit wording there, delete the matching mp3, re-run the command.
  If an mp3 is missing, the site falls back to a browser Urdu voice when the device has one.

## Earth's orbiters
The home-page Earth has a Moon, the ISS and a satellite orbiting it (click them or the chips under the buttons for a fact card with a Listen button).
New Urdu stories `orbit-moon`, `orbit-iss`, `orbit-satellites` were added — run `npm run audio:ur` again to generate just those mp3s (existing ones are skipped).

## Real photos of the spacecraft
Photos appear on the Moon & Mars chapters, the Museum and the Timeline (public-domain NASA images).
Download them once (needs internet):
```bash
npm run images              # saves public/images/<name>.jpg   (add  -- --force  to redo)
```
It looks each spacecraft up in NASA's Image Library (images.nasa.gov) and prints which picture it chose.
Not the right one? Find the picture on images.nasa.gov, copy its ID into `src/data/images.json` (`"nasaId"`) and run again with `--force`.
Until a photo exists the site simply shows no picture for that story. Commit `public/images/*.jpg` so they deploy.
