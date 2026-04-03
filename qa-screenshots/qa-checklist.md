# QA Report: Fernando Monje Bolivar

**Date:** 2026-04-03
**URL:** https://fernando-monje.cofoundy.dev
**Tier:** Pro (S/.120)
**Status:** FAIL

## Technical Health
- [ ] HTML 200 — FAIL (404)
- [ ] CSS 200 — FAIL (no CSS found, site not loading)
- [ ] Profile 200 — FAIL (404)
- [ ] Favicon 200 — FAIL (404)
- [ ] OG 200 — FAIL (404)
- [ ] Guia 200 — FAIL (404)

**Root Cause:** gh-pages branch is polluted with source files (node_modules, .astro, public, dist nested). GitHub Pages cannot serve the site. The `dist/` folder locally is clean — this is a deploy issue, not a build issue.

## Visual — Desktop (1280px)
- [ ] NOT TESTABLE — site returns GitHub 404 page

## Visual — Mobile (375px)
- [ ] NOT TESTABLE — site returns GitHub 404 page

## Client Preferences (form match)
- [ ] NOT TESTABLE — site not deployed

## Data Validation
- [x] Name matches source (Fernando Monje Bolivar)
- [x] Email matches research (Fernando.monje.bolivar@gmail.com)
- [x] LinkedIn matches research (nanoamonje)
- [x] Instagram matches research (@nanoamonje)
- [x] Experience entries match research-notes.md (7 roles verified)
- [x] Education matches (UCSP, Licenciado en Psicologia, C.Ps.P. 61795)
- [x] No hallucinated data detected in config.ts

## Clean Deploy
- [x] No template default names
- [x] No placeholder text
- [x] No "undefined" or "null" values
- [x] Social links point to real profiles
- [ ] gh-pages branch polluted with source files — CRITICAL

## Premium Gates
- N/A (Pro tier)

## Issues Found
- **CRITICAL** — Site returns 404. gh-pages branch contains source files (node_modules, .astro, public/, dist/ nested inside gh-pages root). GitHub Pages build status: "errored". The local dist/ folder is clean — this is a deploy pipeline issue, not a build issue.

## Fix Required
Re-deploy using `./scripts/deploy.sh fernando-monje` which will clean the gh-pages cache and push only dist/ contents. Alternatively, manually delete the gh-pages branch via API and do a clean push of just the dist/ folder.

## Evidence
- desktop-full.png (shows GitHub 404 page)
- mobile-full.png (shows GitHub 404 page)
