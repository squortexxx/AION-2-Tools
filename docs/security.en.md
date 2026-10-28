# Data and update security

[Home](../README.md) · [Русский](security.ru.md)

## Data sources

| Source | Purpose |
| --- | --- |
| Local AION 2 connection, via Npcap | Combat, target, collection, skills and nearby objects |
| Local game catalogs and images | Map markers, names, class/skill/resource icons and reference locations |
| assets.playnccdn.com | Missing equipment icons, cached locally; fixed HTTPS resources path, PNGs only, no redirects or credentials |
| Public NCSOFT profile endpoints | Optional equipment, CP, GS and Arcana lookup using character name, server and region |
| This repository's GitHub Releases | Update manifest and installation packages |
| npcap.com during setup | Official Npcap download if the driver is missing |

Public-profile requests go to `api-search.plaync.com` and `aion2.plaync.com`. Disable the public-profile option in Settings if you do not want automatic lookups. Manual profile requests still run when you ask for them.

The app does not ask for your game password, login cookies or GitHub token. It does not automatically upload fight history or raw packet captures. Profile and update services naturally receive the network requests needed to serve those features.

## Local storage

User data is stored in `%LOCALAPPDATA%\NauchpopTools.Next`. It includes settings, layout, collection progress, recent fights and downloaded updates. Exporting a report or making a backup is a user action. Uninstall keeps user data and does not remove the shared Npcap driver.

## Update verification

1. The app requests `update.json` from the fixed GitHub repository.
2. It verifies the original manifest bytes with a pinned RSA public key using RSA-PSS and SHA-256.
3. It validates repository, platform, version, asset name, size and issue date. Same-version and older installers cannot be applied.
4. It downloads over HTTPS with checked GitHub/CDN redirects and bounded response sizes.
5. It checks installer size and SHA-256. Interrupted or incorrect downloads are not marked ready.
6. Before installation, the app and helper check the cached manifest and file again. The helper waits for the app to save state and exit, then opens Setup with the normal Windows permission prompt.

The signing private key is not included in the application or public repository. GitHub authentication is not required on a player's computer.

Manifest verification and Windows Authenticode are separate. The current Setup EXE does not have an Authenticode publisher certificate. A signed manifest does not make unknown files from another website trustworthy.

## Reporting a security issue

Describe the affected version and behavior without publishing credentials, private profile information or executable attack payloads in an ordinary bug report. This public repository contains release documentation and binaries; the application source remains private.
