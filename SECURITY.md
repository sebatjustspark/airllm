# Security Policy

## Supported versions
| Version | Supported |
| ------- | --------- |
| main    | Yes       |

## Reporting a vulnerability
Open a private issue or contact the repo owner. Include reproduction steps for code you own.
Do not test against systems you do not own or are not authorised to test.

## Hardening baseline for this repo
- Rename `DOCTYPE html.html` to `index.html`; serve directly, no meta-refresh stub.
- Pin third-party assets (Leaflet 1.9.4) with SRI or vendor them.
- Add Content-Security-Policy, X-Frame-Options, Referrer-Policy at the host.
- Enable Dependabot alerts and Code scanning; sign commits.
- Run `security/audit.html` before publishing changes.
