# Installation and player guide

[Home](../README.md) · [Русский](guide.ru.md)

## Requirements

- Windows 10 or Windows 11, 64-bit.
- AION 2 running on the same computer.
- Npcap for local packet capture. Setup can download the official installer if it is missing.
- Internet for release downloads and optional public character profiles. Maps, art and saved progress are local.

The Windows x64 release includes .NET. You do not need to install an SDK or build the app.

## Setup

Download the latest **Setup EXE** from [Releases](https://github.com/squortexxx/AION-2-Tools/releases/latest). Run it, choose a language and installation folder, then complete the wizard. If Npcap is missing, complete its separate official installer when prompted. Keep the default Npcap options unless your environment requires otherwise.

If Npcap requests a restart, restart Windows and finish setup before troubleshooting capture. Reinstalling Nauchpop tools does not require reinstalling an already detected Npcap driver.

For the portable ZIP, extract all files into a writable folder. Launch `NauchpopTools.Next.exe` from that folder; copying the EXE alone is not enough.

## First connection

Launch Nauchpop tools and enter the game. In **Settings → Connection**, enter your character name and select the matching region and server. Public-profile lookup matches name, region and server. The Character and Arcana forms also provide region and server selectors; a server name can repeat across regions with different IDs.

To populate data, open the relevant in-game windows:

| In-game action | Information it helps populate |
| --- | --- |
| Deal damage while grouped | Players, party DPS, class inference and skill damage |
| Select an enemy | Target health and retained target summary |
| Open the pet/soul collection | Collection levels and remaining souls |
| Open skills / change hotbar | Learned skills, levels and equipped slots |
| Open world-boss list | Reported status and spawn times |
| Open rankings / party finder | Rank and recruitment information |

If the app started after the client received its initial state, some information may take more game activity or a character reconnect to appear.

## Language

The first launch uses **English**. Open **Settings → Interface language** and choose **Русский** to switch to Russian. Changes apply immediately to the app and overlays, including voice selection. Your ongoing fight, saved collection and window positions are retained.

Character names, user-written instructions and personal tasks keep their original text. Spoken instructions use an installed Windows voice for the selected language; a notification sound is used when a suitable voice is unavailable.

## Overlay controls

| Control | Action |
| --- | --- |
| Workspace toggles | Show or hide individual panels |
| Arrange windows / Ctrl + Alt + M | Enter or leave layout mode |
| Done / Escape | Finish arranging |
| Hold Alt | Interact with overlays during play |
| Drag a panel header | Move that panel when interaction is enabled and position is unlocked |
| Drag the bottom-right corner | Resize width and height independently |
| Panel options / Ctrl + mouse wheel | Change text size separately |
| Panel close button | Hide that panel; restore it from Workspace |

Overlays normally pass clicks through to the game. They appear with the game active or during layout editing. Borderless/windowed mode is recommended; exclusive fullscreen may hide desktop overlays.

## Combat

Use **Me / Party** and **All targets / Bosses only** in the combat window. Player rows remain stable while values update. Select a player for a skill breakdown. Start a new fight manually or allow the configured damage-idle timeout to end the previous encounter. Healing is tracked separately and does not extend the damage interval.

The target panel is independent of DPS. It retains the last target after death so you can review it. CP and GS appear only when reported by the game or obtained from a matching public profile; missing values are shown as unavailable.

## Hunting, atlas and cubes

In **Hunting**, search for a pet, filter collection progress and pin the targets you want. From the hunting overlay, use **Add**, **From target**, or the remove action without opening the main application. Map actions show known locations and remaining souls. The estimated number of kills appears only after enough drops have been observed.

In **Atlas**, choose a map and layer, then narrow resource types or search by name. Resource markers have game icons; hover for names and select for details. Build a route through up to 12 reference locations and advance to the next point yourself. The app does not move your character.

Cube alerts are enabled by default with a 120 m radius when a fresh position is available. Change the radius, alert and sound options in **Settings**. When the position is stale or unknown, an alert can identify a cube in the loaded area without inventing an exact distance. Repeated reports of the same cube are suppressed.

## Boss instructions and events

In **Boss guides**, enter a skill ID and your instruction, or use the current observed skill. During a matching cast, the boss overlay displays the instruction and can speak it. The overlay also lets you edit an instruction directly. Saved instructions are your own encounter notes; this is not a complete built-in strategy library.

In **Events**, choose which reminders you want. Times are shown in your local time zone. Reminders play one minute before the listed start. Static schedules and observed boss spawn times have different sources; reference schedules do not guarantee a live spawn.

## Updates

Open **Updates** in the sidebar to check manually. Automatic checks run after launch and every 12 hours, and can be disabled. When an update is available:

1. Read the release notes and choose **Download update**.
2. Wait for signature, size and checksum verification. Downloads can be cancelled.
3. Finish combat, then choose **Install and restart**.
4. The app saves state and closes. Accept the normal Windows administrator prompt and complete Setup.

Already downloaded valid packages can be reused after restarting the app. Failed, modified or incomplete packages are blocked. Users on 0.6.1 need to install 0.7.0 manually once to receive the in-app updater.

## Data and removal

Settings, layouts, collections and fight history are stored under `%LOCALAPPDATA%\NauchpopTools.Next`. Close the app before making a manual backup. Updates and uninstall retain these per-user files. Npcap is a shared driver and is not removed by the Nauchpop uninstaller.

## Troubleshooting

| Symptom | What to check |
| --- | --- |
| Waiting for AION 2 | Enter the game, confirm Npcap is installed, and generate game activity. If needed, reconnect the character. |
| No CP or GS | Check character name, server, region and the public-profile option. Private or unavailable profiles cannot provide stats. |
| Missing collection / skills | Open that window in the game to receive its state. |
| No ping | Wait for a supported game response. Stale samples are intentionally hidden. |
| Cannot click or move an overlay | Hold Alt or enter Arrange windows. Check whether its position is locked. |
| Hotkey already in use | Use the Arrange windows button. Another running copy or application may own the hotkey. |
| Overlay not visible | Enable it in Workspace, focus the game, and use borderless/windowed mode. Layout mode can bring panels into view. |
| Map marker has no live object | Atlas points are reference locations. A live report is a separate signal. |
| Update cannot be verified | Cancel, then download again from this repository's Releases. Do not run a modified cached package. |
| New game patch broke capture | Report the game version and the affected feature. Protocol support may need an application update. |

The Setup EXE is not yet Authenticode-signed. The signed update manifest verifies publisher-controlled release contents; it is a separate mechanism from Windows publisher signing.

When [reporting an issue](https://github.com/squortexxx/AION-2-Tools/issues/new?template=bug_report.md), include app version, Windows version, game region, steps and the visible status. Omit passwords, tokens and raw packet captures.
