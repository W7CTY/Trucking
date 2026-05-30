# Changelog — UVL Inventory

All notable changes are recorded here. Versions follow `MAJOR.MINOR.PATCH`.

## 3.0.0 — 2025

Security and reliability pass plus PWA packaging.

### Fixed
- **Auto-email was broken by a temporal-dead-zone bug.** The email subject used a
  `safeText()` helper one line *before* that `const` was declared, throwing a
  `ReferenceError` and aborting the automatic send. The declaration was moved
  ahead of its first use; auto-send now runs.
- **Service worker was never registered.** The offline files shipped but nothing
  registered the worker, so "works offline" did not actually work. Registration
  was added.
- **PDF document title could be injected.** The save filename embedded the raw
  customer name into the print document's `<title>`, allowing markup injection in
  the generated (same-origin) print window. The customer-name portion is now
  sanitized and the title is HTML-escaped.
- **`mailto:` recipient** is now URL-encoded to prevent mail-parameter injection.
- Replaced the placeholder blank app icon with a proper themed icon.

### Added
- Installable PWA packaging: PNG app icons (192 / 512 / 180) and offline support
  that is actually wired up.
- Version and copyright line on the Jobs screen, generated from the `VERSION`
  constant.

### Security — verified in this pass
- **Subresource Integrity (SRI) added to the ZXing scanner script.** Previously
  only the EmailJS script was integrity-pinned; the barcode library was not. Both
  CDN scripts are now SRI-pinned (a supply-chain protection).
- All user-entered fields are HTML-escaped wherever they are rendered (item list
  and generated PDF), and element IDs are sanitized. Email body fields are
  stripped of newlines to prevent header injection.
- All data stays on the device; nothing is transmitted except via EmailJS, and
  only when the user configures it and chooses to send.

---

### How to release the next version
1. Bump `VERSION` in `index.html`.
2. Bump the cache name (`uvl-vN`) in `sw.js`.
3. Add an entry here.
4. Re-deploy the folder.
