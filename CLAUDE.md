# CLAUDE.md

Guidance for Claude Code (and humans) working in this repository.

## What this is

The brand website for **Outcast Acres Farm**, a licensed New York adult-use
cannabis cultivator, processor, and distributor in Granville, New York.
Tagline: **Be Different.** (always italic on the site).

It replaces the old site at outcastacres.com. It is a static, single-page site
with no build step, served by GitHub Pages from the main branch root. Open
`index.html` in a browser and it runs. Do not add a CNAME file yet; the domain
cutover happens later.

This site is the farm umbrella. Two product brands hang off it, presented as
equals in the Our Brands section (decided 2026-09-22: neither brand leads, and
product detail lives on the brand sites, not here):

- **CORE**: 2g all-in-one distillate vapes (value line, has its own site at
  findyourcoreny.com). Tagline: Consistency comes standard.
- **Adirondack Cold Water**: solventless live rosin (sister repo
  `OutcastChris/Adirondack-Cold-Water`, site at adirondackcoldwater.com).
  This repo copies ACW's architecture (no-build static, inline CSS, single
  vanilla JS IIFE, self-hosted fonts, session age gate) but has its own look.

The farm no longer sells dry flower, so the old "Sustainably Grown. Slow
Cured." flower-curing section was removed (2026-09-22). Do not bring back
flower or curing copy.

There is intentionally no "About the Farm" story section (Chris cut it,
2026-09-22). The page is hero, What We Do, Our Brands, Contact, footer.
Do not re-add farm story copy without direction.

## Project layout

```
.
├── index.html        # The whole site (inline CSS + inline JS IIFE)
├── assets/
│   ├── fonts/        # Self-hosted Playfair Display + Inter (woff2, same files as ACW)
│   └── media/        # Farm video + photos (pending; slots are commented in index.html)
├── CLAUDE.md         # This file
└── README.md         # Human-facing overview
```

## Look and voice

Dark editorial. Understated, North Country, premium but not luxury language.

| Token          | Value                     | Use                                        |
| -------------- | ------------------------- | ------------------------------------------ |
| `--char`       | `#2b2a28`                 | Page ground (charcoal).                    |
| `--char-deep`  | `#232220`                 | Alternate bands, age gate, footer.         |
| `--panel`      | `#333230`                 | Card surfaces.                             |
| `--cream`      | `#f0e9dc`                 | Primary type. Warm off-white.              |
| `--marigold`   | `#d97425`                 | Hairline rules and small accents ONLY. Never large fills, never body text. |

- Display and body: Playfair Display. Labels, nav, buttons: Inter, uppercase,
  tracked. Fonts are self-hosted woff2 under `assets/fonts/`; no third-party
  font requests.
- No gradients, no neon, no stock cannabis clichés (no smoke, leaves as decor,
  green-and-gold weed aesthetics).
- **No em dashes anywhere**: site copy, code comments, commit messages. Use
  commas, colons, periods, or a middot (`&middot;`) in labels.

## Compliance (hard rules, read before editing content)

- Keep the **21+ age gate** (`#age-gate`) functional. sessionStorage key
  `oaf-age-verified`, session-scoped, reappears next visit. Same mechanics as
  ACW's gate.
- **No prices, no e-commerce, no online ordering.**
- **No potency numbers. No health, medical, or effect claims.** Sensory
  descriptors only.
- **Never invent product copy.** Individual products are currently not listed
  on this site at all (brand cards only; product detail lives on the brand
  sites). If products are ever listed again, only approved descriptions render,
  word for word; the approved CORE strain copy (Super Lemon Haze, GMO,
  Blackberry Kush) is in git history. Products without an approved description
  are not listed.
- **Never call the vapes cartridges.** They are 2g all-in-one vapes.
- Keep the footer legal line exactly: "For adults 21 and over. Keep out of
  reach of children. Licensed by the New York State Office of Cannabis
  Management. Cultivator OCM-AUCC-22-000042 · Processor OCM-PROC-25-000317 ·
  Distributor OCM-DIST-24-000060."

## Pending content (commented slots in index.html)

- Hero farm video: `assets/media/farm-hero.mp4`. Slot is commented in the
  hero section, paste-ready. Content direction is being rethought: Chris
  finds the old site's footage (bees on the hive box, crop rows) too
  literal for this brand. Expect moodier, less narrative footage.
- Three-photo farm grid: `assets/media/farm-1.jpg` through `farm-3.jpg`.
  Slot is commented in the What We Do section. Same direction note applies.

## Conventions

- No framework, no build, no npm. Plain HTML/CSS/JS. CSS lives in the
  `<style>` block of `index.html` (variables, age gate, header, hero,
  sections, footer, responsive). JS is one vanilla IIFE at the bottom.
- Responsive breakpoint: 860px (mobile nav, single-column grids). Verify at
  desktop and 400px widths; no horizontal overflow.
- Commit author is the GitHub identity OutcastChris
  (288340278+OutcastChris@users.noreply.github.com). Repo-local git config is
  already set.
- Develop on a branch and open a PR for review. Do not push to main directly.

## Running / deploying

No build. Preview locally:

```bash
python3 -m http.server 8000
```

Deploy: GitHub Pages serves the main branch root. Enable under Settings,
Pages, deploy from main, root.
