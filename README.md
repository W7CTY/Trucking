# Trucking Apps by W7CTY

A collection of offline-capable Progressive Web Apps (PWAs) for professional truck drivers. All apps run entirely in the browser, store data locally on your device, and work without an internet connection once installed.

🔗 https://github.com/W7CTY/Trucking

---

## Apps

### 🚛 HOS Calculator — v3.0.1
A Hours of Service calculator built around the FMCSA 70-hour/8-day rule. Helps drivers plan their available driving time, track daily and cycle hours, and understand exactly where they stand before they roll.

📦 Download: `hos-calculator-app.zip`
📖 User Guide: [HOS-USER-GUIDE.md](HOS-USER-GUIDE.md)
📋 Changelog: [HOS-CHANGELOG.md](HOS-CHANGELOG.md)

**Features:**
- 70-hour / 8-day rolling cycle calculator
- Daily 11-hour driving and 14-hour on-duty limit tracking
- Midnight auto-rollover — hours update automatically as the oldest day drops off
- Driver name, timezone, and mileage tracking (miles or kilometers)
- Export and import data for backup or device transfer
- Text size slider up to 300% for easy reading in the cab
- Fully offline after first load; no data ever leaves your device
- Installable as a home-screen app on iOS, Android, and desktop

> **Important:** This app is a planning aid, not a legal logbook. Always confirm hours against your ELD and carrier records.

---

### 📦 UVL Inventory — v3.0.0
A mobile-friendly inventory and job tracking app with barcode scanning, PDF generation, and optional email delivery. Designed for managing loads, inspections, or equipment inventory on the go.

📦 Download: `uvl-inventory-app.zip`
📋 Changelog: [INVENTORY-CHANGELOG.md](INVENTORY-CHANGELOG.md)

**Features:**
- Barcode scanning via device camera (ZXing)
- Job and item tracking with customer name support
- PDF generation for job summaries
- Optional auto-email via EmailJS (user-configured)
- Fully offline after first load
- Installable as a home-screen app on iOS, Android, and desktop

---

## Installation

Both apps are self-contained folders — no build step required.

1. Download and extract the `.zip` file for the app you want.
2. Deploy the extracted folder to any static web host, or open `index.html` directly in a browser.
3. On mobile: tap **Add to Home Screen** (iOS Safari) or **Install App** (Android Chrome) for offline use.

---

## Requirements

- Any modern browser (Chrome, Edge, Firefox, Safari)
- No internet required after first load
- No server, database, or account needed

---

## Security

Both apps are fully self-contained with no external dependencies beyond optional CDN scripts (SRI-pinned). All user data stays on the device. No tracking, no analytics, no automatic uploads.

- Content-Security-Policy on all pages
- All user input HTML-escaped before rendering
- `localStorage` access guarded for private/sandboxed contexts
- Email fields stripped of newlines to prevent header injection (UVL Inventory)
- CDN scripts integrity-pinned with Subresource Integrity (SRI)

---

## License

Apache License 2.0 — see [LICENSE](LICENSE)

---

© 2026 W7CTY · w7cty@outlook.com · github.com/W7CTY/Trucking

