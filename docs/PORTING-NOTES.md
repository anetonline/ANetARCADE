# Porting notes from the Synchronet JavaScript originals

The uploaded source set was reviewed as the design baseline. The OpenDoors edition keeps the recognizable core loops but replaces Synchronet-specific services (`load()`, `console.inkey`, `console.gotoxy`, `user`, `File`, `js.exec_dir`) with OpenDoors and portable C.

## Architectural changes

- Five independent persistence implementations -> one `Player` record.
- Five leaderboard implementations -> one shared score journal and Hall of Fame.
- Synchronet user number -> `od_get_user_id()` stable identity.
- Hand-decoded ANSI arrow sequences -> `od_get_input(..., GETIN_NORMAL)` extended keys.
- Synchronet console screen control -> OpenDoors screen/cursor API.
- Per-game aliases -> one confirmed arcade handle supporting pipe colors.
- Separate launchers -> one native executable and lobby.

## Gameplay refresh

The first C edition is intentionally a clean playable baseline rather than a byte-for-byte translation. Each game has been tightened for an 80x24 BBS terminal and shares consistent Q/P/control behavior. Scores, levels and game loops are structured so additional enemy patterns, achievements, daily challenges, tournaments and inter-BBS score exchange can be layered on without changing the OpenDoors/session core.
