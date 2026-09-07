# cert-validator-demo

**Demonstration only. Every activity number, title, date and certificate number in this repository is invented placeholder data. Nothing here describes a real UNODC event, a real trainee, or a real certificate.**

This is a design proof-of-concept for a public, anonymous certificate validator that a training-management application would publish to. It exists so the design can be reviewed by clicking through it. It is not a production deployment and must not be used to validate anything.

## What the site does

- `index.html` — a static page. Scanning a certificate's QR code opens `?c=<certificate number>`; the page fetches `data/<activity>.json` (the activity segment of the number) and reports **valid**, **revoked**, or **no record**.
- `data/<activity>.json` — one file per published activity. It contains **only**: the activity number, a generalized title, the dates, a coarse location, the organizer, and the list of certificate numbers with their status.
- Optional name confirmation: a record may carry `h`, a one-way SHA-256 fingerprint of `certificate number | verification code | normalized name`. The verification code is printed only on the paper certificate, so the name cannot be recovered or guessed from the public data; a holder can prove the name on their certificate matches without the name ever being published.

## What is deliberately absent

No names, no e-mail addresses, no photographs, no organizations, no per-person attendance detail, no certificate PDFs. The PDF itself stays private with the issuing office; the page only offers a "request a copy" e-mail link (a placeholder address here).

## Fake-data boundary

All eight-character activity numbers here (`deadbeef`, `0badf00d`, `c0ffee42`) and all certificate serials (`DEM001` …) are obviously synthetic. The verification codes used in the sample name checks are `DEMO-1234`, `DEMO-7777` and `DEMO-0101`.

Plan document (private, not in this repository): `tools/ManagerAppSP/feature-signin-certificates-2026-09-07.md`.
