# Changelog — HOS Calculator

All notable changes are recorded here. Versions follow `MAJOR.MINOR.PATCH`.

## 3.0.1 — 2025

### Fixed (safety-critical)
- **The 8-day recap was being added to the daily 11-hour and 14-hour limits.**
  "Hours Gained at Midnight" (the recap from the oldest day dropping off the
  8-day window) was incorrectly added to the 11-hour driving limit and the
  14-hour on-duty window, overstating how much a driver could legally drive that
  day (in some inputs it showed values above the 11-hour cap). Per FMCSA, the
  recap restores hours to the **70-hour/8-day cycle only**; the daily 11/14-hour
  limits are independent and reset by 10 consecutive hours off duty. The recap is
  now applied only to the cycle (where it was already correctly reflected by the
  rolling 8-day total), and the on-screen note was reworded to say the recovered
  hours return to the 70-hour cycle at the next midnight. Verified against five
  worked scenarios.

## 3.0.0 — 2025

Security and reliability pass plus PWA packaging.

### Fixed
- **Corrupted document structure.** A previous build had a second, malformed HTML
  skeleton (duplicate `<head>`/`<body>` and a broken tag) pasted inside the page.
  Browsers rendered it only by leniency. The duplicate was removed; the document
  is now valid with exactly one of each structural tag. App logic was preserved
  byte-for-byte.
- **Version mismatch.** The UI showed "v2.0" while the internal version was 3.0.0.
  The footer now reads the single `VERSION` constant, so it always matches.
- **`localStorage` could throw in restricted contexts.** The install-state check
  read `localStorage` without a guard, which throws in private mode or sandboxed
  webviews. It is now wrapped in try/catch like the other storage calls.
- Removed a redundant no-op conditional in the startup routine.

### Added
- Installable PWA: web manifest, offline service worker, and PNG app icons
  (192 / 512 / 180) themed to match the app.
- Version and copyright line in the footer, generated from the `VERSION` constant.

### Security notes
- Fully self-contained: no external scripts, no network calls
  (`connect-src 'self'`). All data stays on the device.
- User input (driver name, etc.) is sanitized on import and never written to the
  page as raw HTML.

---

### How to release the next version
1. Bump `VERSION` in `index.html`.
2. Bump the cache name (`hos-calc-vN`) in `sw.js`.
3. Add an entry here.
4. Re-deploy the folder.
