# QA Report: Fernando Monje Bolivar

**Date:** 2026-04-04
**URL:** https://fernando-monje.cofoundy.dev
**Tier:** Pro (S/.120 upgrade + Blog CMS S/.120 = S/.160 total)
**Status:** PASS WITH WARNINGS

## Technical Health
- [x] HTML 200
- [x] CSS 200 (`_astro/_slug_.eSAy0elh.css`)
- [x] Profile image 200
- [x] Favicon 200
- [x] OG image 200
- [x] Guia PDF 200
- [x] CV PDF 200 (Pro tier)
- [x] Blog listing `/blog` 200
- [x] Blog post `/blog/bienvenida.md` 200
- [ ] Blog post `/blog/bienvenida` (without .md) 404 — **WARNING**

## Visual — Desktop (1280px)
- [x] CSS loaded — site is fully styled with green accent theme
- [x] Profile photo visible — clear photo with green gradient border frame
- [x] Name correct — "Fernando Monje Bolivar" matches config.ts
- [x] Title visible — "Psicólogo Clínico | Investigador en Neurociencia"
- [x] Colors match — dark green #166534 accent + #22c55e highlight (matches config.ts)
- [x] Fonts loaded — Libre Baskerville + Source Sans 3 from Google Fonts
- [x] All sections render — Hero, About/Sobre Mi, Investigaciones, Experiencia, Educación, Footer (6 sections)
- [x] No horizontal overflow
- [x] Spacing consistent
- [x] Footer — copyright 2026, name correct, social icons present
- [x] Tagline visible — "Psicología con vocación..."
- [x] Stats row — "5+" / "UCSP" / "SERUMS" all visible
- [x] Blog link in floating header nav

## Visual — Mobile (375px)
- [x] Name fits — "Fernando Monje Bolivar" renders cleanly, no overflow
- [x] Photo sized correctly — proportional within green frame
- [x] Text legible — appropriate font sizes
- [x] Cards stack vertically — experience cards, project cards all stack
- [x] No horizontal scroll — page fits 375px width
- [x] Stats/metrics readable — stats row stacks properly
- [x] Contact info accessible — social icons in hero and footer
- [x] Investigaciones cards stack vertically with status badges visible

## Specific Checks (requested)
- [x] WhatsApp icon in Hero social links — present (wa.me/51999448325)
- [x] WhatsApp icon in Footer social links — present
- [x] "Investigaciones" section heading renders
- [x] Status badges: 1x "Activa" + 2x "Finalizada" — correct per config.ts
- [x] "Blog" link in floating header nav — navigates to /blog
- [x] Blog listing page renders correctly with post card
- [x] Blog post page renders with full content, nav, and back link
- [x] 7 experience entries rendered — all match config.ts
- [x] 1 education entry rendered — UCSP, matches config.ts
- [x] 3 projects/investigations rendered — all match config.ts

## Data Validation
- [x] Name: "Fernando Monje Bolivar" — matches research-notes.md
- [x] Email: Fernando.monje.bolivar@gmail.com — matches research-notes.md
- [x] LinkedIn: linkedin.com/in/nanoamonje — matches research-notes.md
- [x] Instagram: @nanoamonje — matches research-notes.md
- [x] WhatsApp: 51999448325 — matches TRACKER phone number
- [x] Companies match research: Hospital Santa Clotilde, Centro Psicotherapy, UCSP (x2), EIC, G&D Foster Home
- [x] Job titles match research-notes.md
- [x] Date ranges match research-notes.md
- [x] Education: Licenciado en Psicología, UCSP — matches research
- [x] Colegiado C.Ps.P. 61795 — in education achievements, matches research
- [x] No hallucinated data detected

## Clean Deploy
- [x] No template default names
- [x] No placeholder text or Lorem ipsum
- [x] No "undefined" or "null" values
- [x] No template default social links — all point to real profiles
- [x] Social links functional (LinkedIn, Instagram, WhatsApp all real URLs)

## Issues Found

### WARNING: Blog post URL contains .md extension
- **Severity:** WARNING
- **Description:** The blog listing links to `/blog/bienvenida.md` (with .md extension). This URL works (200), but the clean URL `/blog/bienvenida` (without .md) returns 404. The Astro content collection uses `post.id` which includes the file extension. Should use `post.slug` instead of `post.id` for cleaner URLs.
- **Impact:** Functional but non-standard URL pattern. When the client manages the blog via Decap CMS, all post URLs will have `.md` in them. Not user-friendly for sharing.
- **Fix:** In `blog/index.astro` line 52: change `post.id` to `post.id.replace(/\.md$/, '')` or use `post.slug`. In `blog/[...slug].astro` line 9: same change for `getStaticPaths`.

## Evidence
- desktop-full.png
- mobile-full.png
- desktop-hero.png (WhatsApp icon confirmed)
- desktop-projects.png (Investigaciones + status badges confirmed)
- desktop-footer-5.png (WhatsApp icon confirmed)
- mobile-hero.png (name fits, photo OK)
- mobile-projects.png (cards stack, badges visible)
