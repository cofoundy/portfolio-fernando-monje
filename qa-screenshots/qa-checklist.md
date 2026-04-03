# QA Report: Fernando Monje Bolivar

**Date:** 2026-04-03
**URL:** https://fernando-monje.cofoundy.dev
**Tier:** Pro (S/.120 upgrade + Blog CMS S/.120)
**Status:** FAIL

## Technical Health
- [x] HTML 200
- [x] CSS 200 (`/_astro/index.Df_DGx_c.css`)
- [x] Profile 200 (`/profile.png`)
- [x] Favicon 200 (`/favicon.svg`)
- [x] OG image — `/og.jpg` returns 200, BUT HTML meta tag references `/og.png` (404) **MISMATCH**
- [x] Guia 200 (`/guia.pdf`)
- [ ] CV 404 (`/cv.pdf`) — **Pro tier should have CV PDF**

## Visual — Desktop (1280px)
- [x] CSS loaded — fully styled, green/white/black scheme applied
- [x] Profile photo visible — renders correctly with green border, transparent bg works on light bg
- [x] Name correct — "Fernando Monje Bolivar" matches config.ts
- [x] Title visible — "Psicologo Clinico | Investigador en Neurociencia"
- [x] Colors match — dark green #166534 + emerald #22c55e as specified in config.ts and client preferences (white, black, green)
- [x] Fonts loaded — Libre Baskerville + Source Sans 3 (Google Fonts preconnected)
- [x] All 6 sections render — hero (with stats), about (with skills), projects (3), experience (7 entries with timeline), education, footer
- [x] No horizontal overflow
- [x] Spacing consistent — clean section separation
- [x] Footer — copyright 2026, name correct, social icons present (email, LinkedIn, Instagram)

## Visual — Mobile (375px)
- [x] Name fits — "Fernando Monje Bolivar" renders on two lines, no overflow
- [x] Photo sized correctly — square with green border, not overflowing
- [x] Nav mobile-friendly — floating pill nav only appears on scroll (desktop), hidden on mobile = clean
- [x] Text legible — appropriate sizing throughout
- [x] Cards stack vertically — projects and experience cards properly stacked
- [x] No horizontal scroll — fits 375px width
- [x] Stats readable — 5+, UCSP, SERUMS row displays correctly
- [x] Contact info accessible — social icons (email, LinkedIn, Instagram) visible in hero and footer

## Client Preferences (form match)
- [x] Style — Pro default (no specific style requested), pro-starter template used correctly
- [x] Colors — white/black/green requested, delivered dark green + emerald green on white bg
- [ ] N/A — Form never arrived at Sheet (2 failed attempts), preferences from WhatsApp/client-meta only
- [x] Social links — LinkedIn (nanoamonje) and Instagram (@nanoamonje) both included
- [x] Blog — Client paid for Blog CMS addon (not checked in this QA — separate /admin route)

## Data Validation
- [x] Name — "Fernando Monje Bolivar" matches research-notes.md (full: Fernando Alexander Monje Bolivar, display name shortened appropriately)
- [x] Email — Fernando.monje.bolivar@gmail.com matches research-notes.md (Cloudflare email protection active)
- [x] LinkedIn — linkedin.com/in/nanoamonje matches research-notes.md
- [x] Instagram — @nanoamonje matches research-notes.md
- [x] Companies — All 7 match research-notes.md: Hospital Santa Clotilde, Centro Psicotherapy, UCSP (2 roles), EIC, UCSP Social, G & D Foster Home
- [x] Job titles — All match research-notes.md exactly
- [x] Date ranges — All match research-notes.md
- [x] Education — UCSP, Licenciado en Psicologia, C.Ps.P. 61795 — all verified
- [x] Skills — All from research-notes.md (EEG, Python, MATLAB, PsychoPy, R, JASP, Jamovi)
- [x] No hallucinated data detected

## Clean Deploy
- [x] No template default names
- [x] No placeholder text (Lorem ipsum, <<, undefined)
- [x] No template default social links — all point to real profiles
- [x] Social links point to real URLs (not # or javascript:void)

## Issues Found

### CRITICAL
1. **OG image meta tag mismatch** — HTML references `/og.png` but deployed file is `/og.jpg`. Social media previews (WhatsApp, LinkedIn, Facebook) will show a broken/missing image when the URL is shared. Fix: either rename og.jpg to og.png, or update the meta tag to reference og.jpg.

### WARNING
2. **CV PDF missing (404)** — Pro tier includes Harvard CV as a deliverable. `/cv.pdf` returns 404. Either the CV hasn't been generated yet, or it wasn't included in the deploy. If CV generation is pending (F5.5), note in TRACKER. If it was generated but not deployed, re-deploy.

## Evidence
- desktop-full.png
- mobile-full.png
- desktop-hero.png, desktop-about.png, desktop-projects.png, desktop-experience.png, desktop-education.png, desktop-footer-5.png
- mobile-hero.png, mobile-about.png, mobile-projects.png, mobile-experience.png, mobile-education.png, mobile-footer-5.png
