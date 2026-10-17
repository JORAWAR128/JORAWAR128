# Updating your existing profile repository

Your profile README lives in the repository named exactly like your username: `JORAWAR128/JORAWAR128`. You do not need a new repository or a fresh clone.

## Steps (using your existing local clone)

1. Open your existing local `JORAWAR128` folder.
2. **Replace** these files with the ones in this folder:
   - `README.md`
   - `preview.html` (optional, local preview only)
3. **Delete** the old `assets/` folder contents, then copy in this folder's `assets/` (all `.svg` files).
   The old `id-dashboard.svg` is obsolete and is not used any more.
4. Optional: copy `assets/static/` too. It holds PNG snapshots of the main graphics (see "Fallbacks" below).
5. Keep `INSTALL.md` out of the repo if you prefer; it is only instructions.
6. Review locally by opening `preview.html` in a browser, then:

```bash
git add -A
git commit -m "Redesign profile README with animated portfolio visuals"
git push
```

No local clone? On github.com open the repo → **Add file → Upload files**, drag the new `README.md` and the `assets` folder in, and commit.

If the old images still show after pushing, hard refresh (Ctrl+Shift+R). Every image URL carries `?v=3`; bump it to `?v=4` whenever you change an SVG, because GitHub caches images aggressively.

## What is in `assets/`

| File | Used for |
|---|---|
| `hero.svg` | Hero: name, headline, portrait, floating chips |
| `pill-github/linkedin/portfolio.svg` | Clickable link pills under the hero |
| `sec-*.svg` | Section headers (About, Tech Stack, Projects, Builder Pass, Connect) |
| `about-life.svg` | Code-window about visual |
| `stack.svg` | Orbit diagram and tool cards |
| `proj-*.svg` | Project cards (clickable in the README) |
| `id-card.svg` | Animated ID card on a lanyard |
| `connect.svg`, `btn-*.svg` | Connect banner and four link buttons |
| `static/*.png` | Static snapshots (optional) |

Your portrait is embedded inside the SVGs as an optimized JPEG (GitHub blocks SVGs from loading external images), so there is no separate photo file to keep in sync.

## What was verified, and what was not

**Checked here, in headless Chromium:** all 21 SVGs are valid XML with no broken internal references, no scripts and no external requests; every image path in the README resolves; the layout was rendered at desktop and 390 px widths; animation was confirmed by comparing frames taken at different times (e.g. the ID card swings and its glare sweeps).

**Links fetched successfully:** the three GitHub repositories, both Vercel demos and your portfolio. I could not fetch your LinkedIn and LeetCode pages, so check those two by clicking them after you push.

**Not testable here:** GitHub's own renderer. Based on how GitHub serves README images, SVGs used through `<img>` run CSS and SMIL animations but never scripts, which is why every effect here is pure CSS inside the SVG. Please open the pushed profile once in light and dark theme to confirm. Clickable areas are the `<a>` wrappers around the images, as GitHub does not make links inside an SVG work.

**3D:** SVG has no real 3D, so the ID card's tilt is simulated with swing, horizontal squeeze, skew and a moving glare. Reduced-motion users see the static frame automatically.

## Fallbacks

- Every SVG is a complete picture at its first frame, so if animation is ever disabled (or the viewer prefers reduced motion) it simply shows the static design.
- `assets/static/*.png` are manual fallbacks. To use one, change an `src` in the README from `./assets/hero.svg?v=3` to `./assets/static/hero.png`.

## GitHub stats

I deliberately did not add third-party stats widgets (they depend on external servers that rate-limit or disappear, and I cannot verify them). Your native pinned repositories and contribution graph still appear below the README. Pin QuestLearn and Studio-Namma-Clone from your profile page (**Customize your pins**).

## Things to double-check

- **QuestLearn:** its own README says it was built from an existing project foundation with your modifications. The profile calls it "a gamified learning platform", as you asked, but you may want a wording you are comfortable defending in an interview.
- **QuestLearn tech labels:** the card shows React, Vite and Tailwind CSS, taken from the repo. The repo also uses TypeScript; I left it off because you asked not to claim it. Add it if you are comfortable with it.
- **Ride-Hailing AI:** described as a team project with your part being XGBoost trip-duration prediction. The repository belongs to AryanJha05.
- **Builder Pass numbers:** "3 projects, 2 live demos, 8 core tools" are simply counts of what is shown on the page. Update them if you add projects.

## Editing later

Text, colours and layout live inside the SVG files. Photos are base64 data inside `hero.svg`, `id-card.svg` and `connect.svg`. If you want to swap the portrait, ask me to regenerate them rather than hand-editing.
