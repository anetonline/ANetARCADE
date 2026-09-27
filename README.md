<img width="1331" height="682" alt="image" src="https://github.com/user-attachments/assets/ab3df20d-56ad-4005-b121-9920d0c7df21" />

<img width="1325" height="929" alt="image" src="https://github.com/user-attachments/assets/87618a07-2008-4ca5-88b2-ce73e16c8bdc" />

<img width="1323" height="950" alt="image" src="https://github.com/user-attachments/assets/8eb7429d-37c5-4317-af51-f5f7834f3508" />

<img width="1329" height="927" alt="image" src="https://github.com/user-attachments/assets/3bce2036-b0c8-4a51-bb17-a81c177ff3ac" />

<img width="1323" height="941" alt="image" src="https://github.com/user-attachments/assets/3c237ce3-f6fe-41af-aad6-85cb38f6c9a8" />

<img width="1320" height="920" alt="image" src="https://github.com/user-attachments/assets/86513945-8fa4-41ed-8ca3-441f95126dd6" />

**A-NET ARCADE**
v1.2.6
**Five Classic Games. One Epic Arcade.**

**A-NET ARCADE v1.2.6 - LINUX x86-64 INSTALL
==========================================**

1. Extract this release into a writable BBS door directory.
2. chmod +x anetarcade and Run: ./anetarcade --arcade-version
3. Run: ./anetarcade --arcade-config
4. Configure your BBS to launch the executable with its normal OpenDoors
   dropfile arguments (for example ANetBBS may use -D%f).
5. Ensure data/ and any configured high-score export directory are writable.
6. Enter the door, create an arcade handle, choose difficulty with D, and play.

DISPLAY
-------
79x24 is the classic safe target. OpenDoors-reported 132x37 or larger enables
131x36 Wide Mode automatically.

A cinematic return to BBS gaming: five complete native terminal games, one shared arcade identity, one Hall of Fame,
and builds for Linux, Raspberry Pi, and Windows.


**A-NET ARCADE v1.2.6 - SYSOP GUIDE
=================================**

CONFIGURATION
-------------
Run locally from the door directory:
  Linux/Pi:  ./anetarcade --arcade-config
  Windows:   anetarcade.exe --arcade-config

This sets BBS name, Sysop name, optional high-score export, and export path.
The door directory and data/ must be writable by the BBS service account.

OPENDOORS COMMAND LINE / DROPFILES
----------------------------------
ANetARCADE reserves ONLY these standalone private commands:
  --arcade-config
  --arcade-version

Everything else is passed to OpenDoors. Standard OpenDoors options such as
-D/-DROPFILE, -C/-CONFIG, -L/-LOCAL, -N/-NODE and -? remain available.
For ANetBBS, -D%f is valid: ANetBBS expands %f to the generated dropfile path
before starting the door.

DIFFICULTY / SCORING
--------------------
Players press D in the lobby to choose Easy, Medium, or Hard. Difficulty affects
starting lives, timing, enemy/hazard speed and reaction windows. Score
multipliers are Easy x1, Medium x2, Hard x3. Individual games also level up and
increase challenge during play; milestone bonus lives are implemented where
appropriate.

DATA / HALL OF FAME
-------------------
data/player_<hash>.dat stores handle, per-game plays, personal bests and total
plays. data/scores.dat is the shared append-only score journal. Hall of Fame
shows the top five scores for every game.

HIGH-SCORE EXPORT FORMAT
------------------------
When enabled, highscores.asc and highscores.ans are regenerated after a game.
highscores.ans is ANSI plus RAW IBM CP437 artwork bytes (for example C9/CD/BB,
BA, C8/BC). It does NOT write UTF-8 box-drawing glyphs. Dynamic BBS and handle
text is ASCII-sanitized before export so UTF-8 multibyte sequences cannot leak
into the CP437 ANSI file.

TERMINAL GEOMETRY / RENDERING
-----------------------------
Classic safe canvas: 79x24; column 80 is intentionally avoided.
Wide safe canvas: 131x36 when OpenDoors reports at least 132x37.
Wide mode is never guessed. If dimensions are unavailable, classic mode is used.
Realtime games clear once on entry and update moving objects/dirty regions with
OpenDoors cursor positioning instead of full-screen redraw loops.

RELEASE PACKAGES
----------------
build-all.sh creates separate Linux x64, Raspberry Pi ARM64, Windows x86 and
Windows x64 release folders/ZIPs. Each receives its own FILE_ID.DIZ, PLAYING.txt,
SYSOP-GUIDE.txt, platform INSTALL.txt, config example, binary and data folder.
No machine-specific binary-info/path text file is included in public packages.
Linux packages include source/ plus build-local.sh as a compatibility fallback
because prebuilt glibc binaries are not universal across all Linux distributions.


WIN32 / ANIMATION SPEED
-----------------------
SPEED_PERCENT=100 is normal. Valid range: 50 through 200.
Lower values reduce animation/input delay; higher values increase it.
Examples: 75 = faster, 100 = normal, 125 = slower.

This changes timing only. It does not change difficulty, scoring, lives, or
leaderboard multipliers. v1.2.6 also caches unchanged HUD output and batches
Frogger river updates to reduce terminal I/O on older Win32 systems. Test at
100 first; use SPEED_PERCENT only for host-specific timing preference.




A-NET ARCADE v1.2.6 - PLAYER GUIDE
=================================

A-Net Arcade contains five complete native OpenDoors terminal games sharing one
arcade profile and Hall of Fame.

LOBBY / DIFFICULTY
------------------
1-5 selects a game. S opens Hall of Fame. H opens Help. Q returns to the BBS.
D cycles EASY -> MEDIUM -> HARD. MEDIUM is the default.

Difficulty changes the actual game mechanics, not just the score:
  EASY   - 5 starting lives where lives apply, slower/longer reaction windows,
           x1 score multiplier.
  MEDIUM - 3 starting lives, standard timing, x2 score multiplier.
  HARD   - 2 starting lives, faster hazards/enemies, x3 score multiplier.

FROGGER 2026
------------
Arrows/WASD move. Cross three traffic lanes, then ride five alternating river
lanes to HOME. The frog rides a supporting log. Reaching HOME advances the
level; traffic/river pressure increases. A bonus life is awarded every 3 levels.
P pauses. Q quits.

GALAGA 2026
-----------
Left/Right or A/D moves. Space/F fires. Destroy the three-row formation while
aliens fire back. Only the lowest surviving alien in a column may fire. New
waves increase the level and hostile pressure. A bonus life is awarded every
3 waves. Q quits.

PONG
----
W/S or Up/Down moves your paddle two rows per tap. First to 7 wins. CPU reaction
speed depends on difficulty and improves as the match level advances. Q quits.

TURTLE BRIDGE
-------------
Left/Right or A/D hops between HOME BANK, five turtles, and TOURIST. Deliver the
package, then return for another. !3 !2 !1 warns that a turtle is about to dive.
Higher levels increase dive pressure; difficulty changes warning/reaction time.
A milestone bonus life is awarded every 4 levels. Q quits.

MANHOLE 2026
------------
Move the cover with arrows/WASD or 1-4. Watch the pedestrian warning and cover
the threatened hole before the countdown expires. Higher levels shorten the
reaction window; difficulty also changes hazard frequency/timing. A milestone
bonus life is awarded every 4 levels. Q quits.

ARCADE HANDLES / HALL OF FAME
-----------------------------
First play creates a handle up to 24 visible characters. Pipe colors |00-|15 are
supported and do not count toward visible length. Hall of Fame shows the top 5
scores per game; N=Next, B=Back, Q=Quit.

DISPLAY
-------
Classic terminals use 79x24 safely. When OpenDoors reports at least 132x37,
Wide Mode uses a 131x36 safe canvas. Realtime animation uses dirty-region
updates to minimize terminal flashing.
