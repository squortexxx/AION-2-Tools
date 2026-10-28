# Changelog

[Русский](CHANGELOG.ru.md)

## 0.7.1 — 2026-10-28

- Fixed profile/Arcana lookup using LATAM server IDs for other regions.
- Added official regional server catalogs and a region selector directly in profile and Arcana forms.
- Server choices update with the region; saved choices from 0.7.0 are migrated by server name.
- Reject mismatched region/server requests before contacting the profile service.

210 checks passed, including regional IDs, migration and selector changes. Public profile and all five Arcana details verified against EU Kaisinel.

## 0.7.0 — 2026-10-28

- Added the Updates page, automatic version checks, release notes, download progress and cancellation.
- Added RSA-PSS manifest verification, bounded HTTPS downloads, SHA-256/size verification and checks before Setup starts.
- Added an installer helper that waits for saved state and shutdown before opening Setup. Installation is available after combat ends.
- Added English as the default interface language and an immediate Russian switch in Settings, including overlays, local game names and voice selection.
- Added English/Russian Setup languages and product documentation with screenshots.
- Kept independent overlay sizes, per-window controls, hunting, atlas, cube alerts and the existing combat/profile features.

Users on 0.6.1 need one manual installation of 0.7.0. Future releases can be checked and downloaded inside the app.

## 0.6.1

- Nearby cube alerts with duplicate suppression, configurable radius and optional sound.
- Separate target panel, party DPS filters, in-overlay actions and independent width/height resizing.
- Setup with an official Npcap download when the driver is missing.
