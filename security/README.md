# Security Audit Tool — airllm

Standalone, client-side scanner for code/systems you own. No data leaves the browser.

## Use
Open `security/audit.html` in a browser, paste code or the URL of a page you own, click **Run audit**.

Checks: leaked keys/tokens, open-redirect meta refreshes, external CDN without SRI, unsafe inline handlers, `localStorage` sensitive use, missing CSP/frame protections, mixed-content `http://`, and insecure filenames (e.g. `DOCTYPE html.html`).

## Findings for this repo (from GitHub, 2026-11-04)
- `index.html` (76 bytes) is only `<meta http-equiv="refresh" content="0;url=DOCTYPE html.html">` — open-redirect / fragile redirect, URL contains a space/HTML doctype.
- `DOCTYPE html.html` (47,670 bytes) loads `https://unpkg.com/leaflet@1.9.4/dist/leaflet.css` without SRI, and is a single-file Next Maps app.
- GitHub secret scanning: no open alerts. Dependabot alerts: disabled (403). Code scanning: no analysis found (404).

## Recommended hardening
1. Rename `DOCTYPE html.html` → `index.html`, delete the redirect stub.
2. Pin leaflet CSS/JS with `integrity` + `crossorigin`, or vendor locally.
3. Add CSP, `X-Frame-Options`, and referrer policy via your host headers.
4. Enable Dependabot alerts + Code scanning in repo Settings → Security.
