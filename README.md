<div align="center">

# 🕹️ ANetARCADE
### FIVE CLASSIC GAMES. ONE EPIC ARCADE.

**Dodge traffic. Fight the fleet. Beat the paddle. Chase the next high score.**

![Version](https://img.shields.io/badge/version-1.3.0-00d9ff?style=for-the-badge)
![Games](https://img.shields.io/badge/games-5-ff2bd6?style=for-the-badge)
![ANSI](https://img.shields.io/badge/graphics-CP437%20%2F%20ANSI-55ff77?style=for-the-badge)
![Platforms](https://img.shields.io/badge/platforms-Linux%20%7C%20Pi%20%7C%20Windows-ffb52e?style=for-the-badge)

*Insert coin. Pick your game. Keep the BBS alive.*

[The games](#-pick-your-game) · [Your player card](#-one-player-card-five-games) · [InterBBS scores](#-your-board-your-score-worldwide) · [Shared lobby](#-different-games-same-lobby) · [Installation](#-put-the-arcade-on-your-bbs)

[Visit the ANetARCADE website](https://a-net-online.lol/anetarcade/)

</div>

<img width="1331" height="682" alt="image" src="https://github.com/user-attachments/assets/ab3df20d-56ad-4005-b121-9920d0c7df21" />

<img width="1325" height="929" alt="image" src="https://github.com/user-attachments/assets/87618a07-2008-4ca5-88b2-ce73e16c8bdc" />

<img width="1323" height="950" alt="image" src="https://github.com/user-attachments/assets/8eb7429d-37c5-4317-af51-f5f7834f3508" />

<img width="1329" height="927" alt="image" src="https://github.com/user-attachments/assets/3bce2036-b0c8-4a51-bb17-a81c177ff3ac" />

<img width="1323" height="941" alt="image" src="https://github.com/user-attachments/assets/3c237ce3-f6fe-41af-aad6-85cb38f6c9a8" />

<img width="1320" height="920" alt="image" src="https://github.com/user-attachments/assets/86513945-8fa4-41ed-8ca3-441f95126dd6" />


---

**ANetARCADE brings five classic-inspired arcade games to your BBS through OpenDoors.** One persistent player profile ties them together, with local Hall of Fame rankings, adjustable difficulty, optional InterBBS score sharing, and a shared live lobby.

It is native terminal gaming with **CP437 ANSI artwork**, builds for Linux, Raspberry Pi, and Windows, and a sysop updater for signed releases.

**Created by StingRay · Jerry Reed · A-Net Online**

> **About this release:** the current **1.3.0 IBBS-UPDATER rebuild** adds InterBBS score sharing and the signed updater while retaining the existing 1.3.0 package filenames. Earlier 1.3.0 packages need a manual upgrade to receive these features.

## 🎮 Pick your game.

| Game | The challenge | Controls |
| :--- | :--- | :--- |
| 🐸 **Frogger 2026** | Cross three traffic lanes, ride the river’s moving logs, and reach HOME. Each level increases the pressure. | Arrows / WASD · **P** pause · **Q** quit |
| 🚀 **Galaga 2026** | Destroy a three-row alien fleet while dodging return fire. New waves bring a tougher fight. | Left / Right or A / D · Space / F fire · **Q** quit |
| 🏓 **Pong** | Face the CPU in a race to seven points. Its reaction speed changes with difficulty and match progression. | W / S or Up / Down · **Q** quit |
| 🐢 **Turtle Bridge** | Deliver a package across five turtles, then return to the bank. Watch their dive countdowns. | Left / Right or A / D · **Q** quit |
| 🕳️ **Manhole 2026** | Cover the threatened hole before a pedestrian reaches it. Higher levels shorten the reaction window. | Arrows / WASD or 1–4 · **Q** quit |

### Easy to enter. Hard to leave.

Press **D** in the lobby to cycle difficulty:

| Difficulty | Starting lives, where applicable | Score multiplier |
| :--- | :---: | :---: |
| **Easy** | 5 | ×1 |
| **Medium** — default | 3 | ×2 |
| **Hard** | 2 | ×3 |

Difficulty changes the actual game: lives, speeds, hazards, and reaction windows. Each game also increases its challenge as play progresses. Milestone bonus lives are available where implemented.

## 🪪 One player card. Five games.

Create an arcade handle on your first visit and carry it across every game.

- Up to **24 visible characters**, with `|00`–`|15` pipe colors.
- Persistent per-game play counts and personal bests.
- A shared total-play count.
- A local **Hall of Fame** showing the top five score entries per game.
- Optional `highscores.asc` and CP437 `highscores.ans` exports for your BBS.

Your BBS caller identity anchors the profile. Keep the same dropfile/caller configuration when upgrading so players retain their records.

### The lobby

| Key | Action |
| :---: | :--- |
| **1–5** | Choose a game |
| **D** | Cycle difficulty |
| **S** | Local Hall of Fame |
| **I** | InterBBS scores, when enabled |
| **C** | Shared chat, when enabled |
| **H / ?** | Help and controls |
| **Q** | Return to the BBS |

## 🏆 Your board. Your score. Worldwide.

Enable **InterBBS score sharing** to compete with callers on other BBSes. Each of the five games has its own leaderboard, keeping paddle victories separate from alien-fleet scores.

Press **I** from the lobby to view the rankings:

- **N** — next game.
- **B** — previous game.
- **R** — redraw current results.
- **Q** — return to the arcade.

New scores are queued on disk and uploaded by a background worker. Failed uploads remain queued for retry, and the hub deduplicates event IDs. Leaderboards refresh in the background; cached results remain available when the hub cannot be reached.

**Score hub:** https://scores.a-net.online

Setup can reuse existing shared-chat credentials, so an already registered BBS does not need another enrollment. Score sharing and chat are independent options. Disabling score sharing hides the InterBBS menu.

<details>
<summary><strong>Hub operator notes</strong></summary>

The five leaderboard IDs are:

| Game | Hub ID |
| :--- | :--- |
| Frogger | `anetarcade-frogger` |
| Galaga | `anetarcade-galaga` |
| Pong | `anetarcade-pong` |
| Turtle Bridge | `anetarcade-turtle` |
| Manhole | `anetarcade-manhole` |

The current hub stores arcade scores under `mode=story` as a compatibility convention; this does not add a Story mode to ANetARCADE. Difficulty multipliers are included in the submitted score, and rankings combine difficulties, like the local Hall of Fame.

The hub operator must enable these IDs. The source includes `ENABLE-ARCADE-HUB.py` for the migrated A-Net hub layout; client sysops do not need to run it. The separate Hub Setup kit also installs the initial signed update files and public update route.

Only new scored runs are queued. Existing local score history is not automatically backfilled.

</details>

## 💬 Different games. Same lobby.

An ANetARCADE caller on one BBS. A **PUMPKO** caller on another. One shared room.

Enable optional live chat during setup, then press **C** from the lobby. The status display shows connected players, connected BBSes, and callers in chat.

**Shared lobby:** https://chat.a-net.online

Say **no** to chat during setup and its menu stays hidden. You can enable chat without score sharing, or score sharing without chat.

If your BBS already has hub credentials, reuse them. A fresh directory does not reclaim an existing registered BBS name; lost credentials require recovery or a verified reset by the hub operator.

## 🖥 Native terminal gaming.

ANetARCADE uses **OpenDoors** for BBS integration and terminal input. Gameplay updates moving regions instead of repeatedly clearing the entire screen.

- **Classic mode:** a 79×24 safe canvas.
- **Wide mode:** a 131×36 safe canvas when OpenDoors reports at least 132×37.
- **CP437 ANSI exports:** raw IBM character bytes, with dynamic text sanitized for compatibility.
- **Host timing adjustment:** `SPEED_PERCENT=50–200`; 100 is normal, lower values are faster, higher values are slower. This changes timing, not difficulty or score multipliers.

Wide mode is detected from reported terminal geometry, not guessed.

## 📦 Choose your build.

| Platform | Release package |
| :--- | :--- |
| Linux x86-64 | `ANetArcade-1.3.0-linux-x64.zip` |
| Raspberry Pi / Linux ARM64 | `ANetArcade-1.3.0-pi-arm64.zip` |
| Windows 32-bit | `ANetArcade-1.3.0-windows-x86.zip` |
| Windows 64-bit | `ANetArcade-1.3.0-windows-x64.zip` |
| Source | `ANetArcade-OpenDoors-v1.3.0-source.zip` |

Download builds from the [ANetARCADE website](https://a-net-online.lol/anetarcade/).

Use a **64-bit operating system** for the ARM64 package. Linux online features need HTTPS-capable `curl` and CA certificates. Windows online features use native WinHTTP with TLS 1.2 and require a working certificate trust store.

No Python or PowerShell is required on the installed game client. Python is used for developer packaging tools and the separate hub software.

## 🚀 Put the arcade on your BBS.

1. Download and extract the package for your operating system and architecture.
2. Run the installer:
   - **Linux / Pi:** `bash INSTALL-LINUX.sh`
   - **Windows:** launch `ANetARCADE-SETUP.exe`.
3. Choose the installation directory and review the BBS identity, score exports, InterBBS score sharing, and live-chat settings.
4. Add the door to your BBS menu, using the installed folder as its working directory and passing an OpenDoors-compatible caller dropfile.

### Local play

```bash
# Linux / Raspberry Pi
./anetarcade -L
```

```bat
REM Windows
anetarcade.exe -L
```

### Configuration

```bash
# Full configuration, including optional online features
./anetarcade --arcade-config

# Configure just one online feature
./anetarcade --scores-config
./anetarcade --chat-config
```

On Windows, use `anetarcade.exe` with the same options.

### Door command examples

```bash
./anetarcade -D /path/to/BBSDEV.DRP
```

```bat
anetarcade.exe -D C:\path\to\DOOR32.SYS
```

Use your BBS software’s actual dropfile path or substitution. On **ANetBBS**, `-D %f` passes the generated dropfile to the game.

**Linux permissions:** the BBS service account needs write access to `data/` and read access to its configuration, including private credential files. Install as the BBS account where practical, or assign suitable ownership and group access afterward. Do not make secret files world-readable.

## 🔄 Keep your players. Update your arcade.

Back up the door, close active ANetARCADE sessions, and run the new installer into the **existing directory**. Profiles, local scores, and existing configuration are retained. Setup lets you review settings and opt into the new features.

**Do not delete the game directory to upgrade.**

The current rebuild adds a signed sysop updater:

```bash
# Linux / Raspberry Pi
./ANetARCADE-UPDATE --check
./ANetARCADE-UPDATE
```

```bat
REM Windows
ANetARCADE-UPDATE.exe --check
ANetARCADE-UPDATE.exe
```

The updater validates the release signature, download size, and SHA-256 hash before running the installer. It gates new sessions and refuses installation while an ANetARCADE process is active. Update mode backs up payload files and restores them on failure while preserving settings and player data.

No BBS or VM reboot is required. Public update hosting must be configured by the hub operator first.

> **Same-version rebuild:** manually install this updated 1.3.0 package to introduce the updater. It does not automatically replace another 1.3.0 installation. Future automatic releases must use a higher version, such as 1.3.1.

See [InterBBS setup](docs/INTERBBS-SCORES.txt) and [online updates](docs/ONLINE-UPDATES.txt).

## 🛠 Build from source.

The source includes the bundled OpenDoors tree, game code, shared chat, score-sharing worker, updater, and installer tooling.

```bash
# Build all four platform packages
bash build-all.sh

# Or select one platform
bash build-all.sh linux-x64
bash build-all.sh pi-arm64
bash build-all.sh windows-x86
bash build-all.sh windows-x64
```

Build tools include CMake, make, Python 3, and the appropriate compilers: `musl-gcc` for Linux x64, GNU ARM64 cross tools for Pi, and MinGW for Windows. These are developer dependencies rather than installed-client requirements.

## 📖 Player and sysop reference.

| Topic | Guide |
| :--- | :--- |
| Controls, difficulty, and profiles | [PLAYING.txt](docs/PLAYING.txt) |
| BBS integration and configuration | [SYSOP-GUIDE.txt](docs/SYSOP-GUIDE.txt) |
| InterBBS scores | [INTERBBS-SCORES.txt](docs/INTERBBS-SCORES.txt) |
| Shared lobby | [SHARED-CHAT.txt](docs/SHARED-CHAT.txt) |
| Signed updates | [ONLINE-UPDATES.txt](docs/ONLINE-UPDATES.txt) |
| Release notes | [RELEASE-NOTES.txt](docs/RELEASE-NOTES.txt) |
| Build and test status | [RELEASE-VALIDATION.txt](docs/RELEASE-VALIDATION.txt) |

Linux startup, leaderboard navigation, upload retry/deduplication, and updater rollback were tested. ARM64 startup was checked under emulation. Windows x86/x64 builds compiled successfully; consult the release validation notes for runtime testing limits.

For bug reports, include your build marker, OS/architecture, BBS software, dropfile, terminal client, and steps to reproduce. The rebuild’s marker is `ANETARCADE-1.3.0-IBBS-UPDATER`.

**Never commit credential JSON files, player data, shared secrets, or private signing keys.**

## ❤️ Built for the BBS.

Created by **StingRay (Jerry Reed)** at **[A-Net Online](https://a-net.online)**. **[OpenDoors](https://github.com/RealDeuce/OpenDoors)** provides the door interface; its bundled license and notices are included in [OPENDOORS-LICENSE.txt](docs/OPENDOORS-LICENSE.txt).

The games celebrate classic arcade ideas with native BBS implementations. ANetARCADE is an independent A-Net project.

<div align="center">

**Five games. One player card. A whole network of challengers.**

*Some legends never die. They just find another BBS.*

🐸 🚀 🏓 🐢 🕳️

</div>
