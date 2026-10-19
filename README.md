# Super Mario: The Lost Dreams TAS files

Input files (`.m64`) and savestates (`.st`) for the individual-star TASes of **Super Mario: The Lost Dreams**
(SM THE LOST DREAMS, TLD), archived from the community sheet so they no longer depend on Discord attachment links.

- **Source:** the Google Sheet "Super Mario: The Lost Dreams - TAS Times", tab "Star Times"
  (<https://docs.google.com/spreadsheets/d/1bXzwzvykQH8wmp1JIh1yZGuM0TnsMK4vSZsAwvThNEo/edit?gid=2052950279>),
  read on 2026-10-19. Every file was linked from that sheet as a Discord attachment and was downloaded on 2026-10-19.
- **Credit:** the TASes belong to the authors in the table (the sheet's Author/s column). This repo only stores the
  files; the times, statuses, comments and authors are copied from the sheet as it was on 2026-10-19.
- **ROM:** Super Mario The Lost Dreams v1.2h (header name `SM THE LOST DREAMS`, CRC1 `FA5EE6EB`, savestate ROM MD5
  `8dc54ac604994d056d4a7cdaff393ba2`). Every `.m64` header names this ROM, and every savestate was made with it.

## Files: standard savestates (2026-10-19)

- **One folder per course,** like the sheet's sections: `1-playful-palace`, `2-bob-omb-temple`, `3-gelato-beach`,
  `4-the-white-abyss`, `dream-realm`, `cap-levels`, `miscellaneous`, `bowser-levels`.
- **Names:** `<course>.<star>.<time>.m64`, and its savestate is `<course>.<star>.st`, for example
  `pp.dusk_whomp.44_67.m64` and `pp.dusk_whomp.st`.
  - Course codes: `pp` Playful Palace, `bt` Bob-omb Temple, `gb` Gelato Beach, `wa` The White Abyss, `dr` The Dream
    Realm, `wc` / `vc` / `mc` the cap levels, `mos` Mountain of Serenity, `cwt` Cyberwave Trial, `gl` Goombas Lair,
    `rr` Rainbow Road, `ttc` Tick Tock Chaos, `b1` / `b2` / `b3` the Bowser levels.
  - The time is in seconds, `SS_CC` (2:49.73 is `169_73`), as in the sm64-island-tas repo. It is the time in the
    original file name when it had one, otherwise the sheet's.
- **Standard savestates** (the sm64-island-tas rule), so every movie starts at the same point and they append:
  - **Courses with an act select** (Playful Palace, Bob-omb Temple, Gelato Beach, The White Abyss; the Dream Realm's
    courses 1-4 start in them): the state sits on the act select's first frame, the poll where the level changes,
    before its input. The movie presses Start on input 26, the first one the selector takes, and the level loads on
    row 44. Where the selector opens on another act, the movie first taps the stick to the movie's act.
  - **Levels without an act select** (the Bowser levels and arenas, the cap levels, the miscellaneous levels, Toad):
    the state sits on the level's first frame.
  - **Every movie ends on the input before the next level's first frame** (the hub, or whatever level comes next).
    Movies that stopped earlier were padded with neutral inputs up to it, and longer ones were cut. The exception is
    B1's secret star, which has no exit: that movie keeps its original end.
  - **The battle rows are the arena fight alone,** from the arena's first frame. Their originals also played the
    course and an older secret star first.
- **Each movie was checked in Mupen:** it matches its original row by row (level, action, position, speed, facing,
  coins) from the level load to its end.
- **Entry conditions:** each state keeps its movie's own save (stars, file) and the values the original was recorded
  with. The game carries these from the hub into the course:
  - Mario's pre-warp facing, position, speed and the action he warped in;
  - the camera's state: camera.c's statics and the D-pad camera hook's remembered mode at 0x80286D20;
  - the swim strength (Gelato Beach's movies need 280);
  - the last completed course and star.
  - Where a movie needed it, also the RNG seed, the global timer and `gAreaUpdateCounter`; the manifest's
    `rebase_fix` says which (`plain`: none).
  - A full run that arrives differently would need its own movie into the course.
- **`archive/<folder>/`** holds every original file unchanged, with its original savestate, so Mupen still pairs them.
  The comment-linked files are there too, since they play from the original savestates:
  - `pp.lonely_shroom.hyperjump_14_73.zip`: the slower hyperjump strat, as uploaded. It holds
    `TotheLonelyShroom1473.m64` and `TotheLonelyShroom1473.savestate` (14.73 in Mupen).
  - `rr.rainbow_road.improvement_higher_flyguy.m64` and `b3.nightmare_realm.improvement_109_77.m64`: unfinished
    drafts (no star), as uploaded.
- **The manifest** (`manifest.csv` / `manifest.json`) lists every sheet link:
  - where its file is now, and where the original is (`original_path`);
  - the original's name, Discord URL, size and SHA-256 (`sha256`);
  - for a rebased file, its SHA-256 (`rebased_sha256`), the fix it needed and its measured time.

## Playing a movie

- Use Mupen64 (mupen64-rr-lua) with the Super Mario The Lost Dreams v1.2h ROM.
- Keep each `.m64` in the same folder as its `.st`. Mupen plays `a.b.c.m64` from `a.b.c.st`, else `a.b.st`, else
  `a.st`.
- The original savestates in `archive/` come from two Mupen generations (10.5 MB and 21 MB unpacked, all gzip). An old
  Mupen may not load the larger ones.

## Timing

- **The sheet's rule, as measured in Mupen:** VIs (lag included) / 60, from the first frame of the level's fade-in to
  the first frame of the star dance (exit or no-exit dance; for 100-coin rows, the last star).
  - The fade-in's first frame is the first poll where the camera transition has started with Mario present.
  - A level change inside the run (the Dream Realm's warp into the dream) doesn't restart it.
  - The battle rows are timed from the arena's fade-in to the key or star dance.
- Timed this way, 39 of the 43 linked movies replay to exactly the sheet's time. The four others are in the notes:
  Fly Through the Abyss, B3, the B2 star, and Dream Realm 1 and 3.
- Note for timers: SM64LuaRedux's own timer starts one frame after the fade-in's first frame in most of these
  savestates, so it reads 0.03 below the sheet there.

## What was checked

- Every sheet link was accounted for: 89 attachment links downloaded, and 1 Discord message link not retrieved
  (below).
- Every original `.m64` has a valid header, names the TLD ROM, starts from a snapshot, and is not shorter than its
  sample count. Every original savestate decompresses with no CRC error and records the TLD v1.2h ROM. The `.zip`
  passes its CRC test.
- Every movie was played in Mupen and timed (above). Every rebased movie matches its original row by row, and its time
  is unchanged.

## Missing, questionable and duplicate files

- **Entries with no files on the sheet (5):**
  - Find 8 Red Coins (Playful Palace): "done in 100c".
  - 8 Risky Red Coins (Bob-omb Temple): 41.70 by ChouxZi3, no links.
  - 8 Underwater Redcoins (Gelato Beach).
  - 8 Red Coins in the Mountain (The White Abyss).
  - B3. The Nightmare Realm - Battle (status "open").
- **Not retrieved (1):** the Gelato Beach 100 Coins comment ("paired with reds. improvement") links to a Discord
  message (`discord.com/channels/929005491634442260/929005491634442263/1529915408986149077`), not a file. The
  account used for the download cannot read that server.
- **The sheet's times are kept.** Where a linked file doesn't match its time, the table says so:
  - Fly Through the Abyss: the linked movie is a 25.10; the 14.70 movie isn't linked.
  - B3: the linked movie is a 2:04.00. The 1:49.77 has only an unfinished draft.
  - The B2 star: it desyncs from its savestate, so it isn't rebased and is kept as uploaded.
  - Dream Realm 1 and 3: the sheet leaves out the dream warp's lag here.
- **Duplicates:** no two links point to the same URL, and no two movies are the same file. Several original savestates
  are byte-identical (the same course-entry state). Two different original savestates were both named `mc.savestate`
  (Metal Cap left and right door).

## Stars

### 1. Playful Palace

| Star | Time | Author/s | Status | .m64 | .st | Originals | Other files | Notes |
|---|---|---|---|---|---|---|---|---|
| Defeat the Dusk Whomp | 44.67 | RSw | inapplicable | [pp.dusk_whomp.44_67.m64](1-playful-palace/pp.dusk_whomp.44_67.m64) | [pp.dusk_whomp.st](1-playful-palace/pp.dusk_whomp.st) | [pp.dusk_whomp.44_67.m64](archive/1-playful-palace/pp.dusk_whomp.44_67.m64) [pp.dusk_whomp.st](archive/1-playful-palace/pp.dusk_whomp.st) | — |  |
| To the Lonely Shroom | 10.70 | RSw, FeijoadaMolhada | done | [pp.lonely_shroom.10_70.m64](1-playful-palace/pp.lonely_shroom.10_70.m64) | [pp.lonely_shroom.st](1-playful-palace/pp.lonely_shroom.st) | [pp.lonely_shroom.10_70.m64](archive/1-playful-palace/pp.lonely_shroom.10_70.m64) [pp.lonely_shroom.st](archive/1-playful-palace/pp.lonely_shroom.st) | [pp.lonely_shroom.hyperjump_14_73.zip](archive/1-playful-palace/pp.lonely_shroom.hyperjump_14_73.zip) | sheet: "true rr count, hyperjump strat is slower" |
| Find 8 Red Coins | — | RSw | inapplicable | — | — | — | — | sheet: "done in 100c"; no files linked on the sheet |
| Deep into the Palace | 11.73 | RSw, ChouxZi3, feijoadamolhada | optimised | [pp.deep_palace.11_73.m64](1-playful-palace/pp.deep_palace.11_73.m64) | [pp.deep_palace.st](1-playful-palace/pp.deep_palace.st) | [pp.deep_palace.11_73.m64](archive/1-playful-palace/pp.deep_palace.11_73.m64) [pp.deep_palace.st](archive/1-playful-palace/pp.deep_palace.st) | — |  |
| Switch-Way to the Top | 37.47 | RSw | inapplicable | [pp.switch_way.37_47.m64](1-playful-palace/pp.switch_way.37_47.m64) | [pp.switch_way.st](1-playful-palace/pp.switch_way.st) | [pp.switch_way.37_47.m64](archive/1-playful-palace/pp.switch_way.37_47.m64) [pp.switch_way.st](archive/1-playful-palace/pp.switch_way.st) | — | sheet: "might be better to do reverse order, clone star + cancel"; the original name has no time; the file name uses the sheet's 37.47 |
| Vanishcap and the Fire Chamber | 8.70 | RSw, FeijoadaMolhada | done | [pp.fire_chamber.8_70.m64](1-playful-palace/pp.fire_chamber.8_70.m64) | [pp.fire_chamber.st](1-playful-palace/pp.fire_chamber.st) | [pp.fire_chamber.8_70.m64](archive/1-playful-palace/pp.fire_chamber.8_70.m64) [pp.fire_chamber.st](archive/1-playful-palace/pp.fire_chamber.st) | — | sheet: "negative jump strat" |
| Defeat the Dusk Whomp + 100 Coins | 2:49.73 | RSw | needs optimisation | [pp.dusk_whomp_100c.169_73.m64](1-playful-palace/pp.dusk_whomp_100c.169_73.m64) | [pp.dusk_whomp_100c.st](1-playful-palace/pp.dusk_whomp_100c.st) | [pp.dusk_whomp_100c.169_73.m64](archive/1-playful-palace/pp.dusk_whomp_100c.169_73.m64) [pp.dusk_whomp_100c.st](archive/1-playful-palace/pp.dusk_whomp_100c.st) | — | sheet: "reds + switches included, lotad" |

### 2. Bob-omb Temple

| Star | Time | Author/s | Status | .m64 | .st | Originals | Other files | Notes |
|---|---|---|---|---|---|---|---|---|
| Defeat the Dusk Bob-omb | 63.77 | tjk, FeijoadaMolhada, ChouxZi3 | needs optimisation | [bt.dusk_bobomb.63_77.m64](2-bob-omb-temple/bt.dusk_bobomb.63_77.m64) | [bt.dusk_bobomb.st](2-bob-omb-temple/bt.dusk_bobomb.st) | [bt.dusk_bobomb.63_77.m64](archive/2-bob-omb-temple/bt.dusk_bobomb.63_77.m64) [bt.dusk_bobomb.st](archive/2-bob-omb-temple/bt.dusk_bobomb.st) | — | sheet: "no quick releases" |
| Deep into the Temple | 10.20 | FeijoadaMolhada, ChouxZi3 | needs optimisation | [bt.deep_temple.10_20.m64](2-bob-omb-temple/bt.deep_temple.10_20.m64) | [bt.deep_temple.st](2-bob-omb-temple/bt.deep_temple.st) | [bt.deep_temple.10_20.m64](archive/2-bob-omb-temple/bt.deep_temple.10_20.m64) [bt.deep_temple.st](archive/2-bob-omb-temple/bt.deep_temple.st) | — |  |
| 8 Risky Red Coins | 41.70 | ChouxZi3 | inapplicable | — | — | — | — | no files linked on the sheet |
| The High Room | 17.93 | FeijoadaMolhada | inapplicable | [bt.high_room.17_93.m64](2-bob-omb-temple/bt.high_room.17_93.m64) | [bt.high_room.st](2-bob-omb-temple/bt.high_room.st) | [bt.high_room.17_93.m64](archive/2-bob-omb-temple/bt.high_room.17_93.m64) [bt.high_room.st](archive/2-bob-omb-temple/bt.high_room.st) | — |  |
| Cannon and Vanishcap | 9.70 | FeijoadaMolhada | needs optimisation | [bt.cannon_vanishcap.9_70.m64](2-bob-omb-temple/bt.cannon_vanishcap.9_70.m64) | [bt.cannon_vanishcap.st](2-bob-omb-temple/bt.cannon_vanishcap.st) | [bt.cannon_vanishcap.9_70.m64](archive/2-bob-omb-temple/bt.cannon_vanishcap.9_70.m64) [bt.cannon_vanishcap.st](archive/2-bob-omb-temple/bt.cannon_vanishcap.st) | — |  |
| Fly Through the Abyss | 14.70 | FeijoadaMolhada, ChouxZi3 | needs optimisation | [bt.fly_abyss.25_10.m64](2-bob-omb-temple/bt.fly_abyss.25_10.m64) | [bt.fly_abyss.st](2-bob-omb-temple/bt.fly_abyss.st) | [bt.fly_abyss.25_10.m64](archive/2-bob-omb-temple/bt.fly_abyss.25_10.m64) [bt.fly_abyss.st](archive/2-bob-omb-temple/bt.fly_abyss.st) | — | sheet: "grindel rng"; the linked movie replays to 25.10 (header 71 rerecords); the sheet's 14.70 (732 rerecords) is a movie that isn't linked |
| The High Room + 100 Coins | 2:09.47 | ChouxZi3 | needs optimisation | [bt.high_room_100c.129_47.m64](2-bob-omb-temple/bt.high_room_100c.129_47.m64) | [bt.high_room_100c.st](2-bob-omb-temple/bt.high_room_100c.st) | [bt.high_room_100c.129_47.m64](archive/2-bob-omb-temple/bt.high_room_100c.129_47.m64) [bt.high_room_100c.st](archive/2-bob-omb-temple/bt.high_room_100c.st) | — | sheet: "reds included, rng heavy" |

### 3. Gelato Beach

| Star | Time | Author/s | Status | .m64 | .st | Originals | Other files | Notes |
|---|---|---|---|---|---|---|---|---|
| Waterfall in the Distance | 14.73 | ChouxZi3, FeijoadaMolhada | needs optimisation | [gb.waterfall.14_73.m64](3-gelato-beach/gb.waterfall.14_73.m64) | [gb.waterfall.st](3-gelato-beach/gb.waterfall.st) | [gb.waterfall.14_73.m64](archive/3-gelato-beach/gb.waterfall.14_73.m64) [gb.waterfall.st](archive/3-gelato-beach/gb.waterfall.st) | — |  |
| Climb up the Tower | 10.80 | ChouxZi3 | needs optimisation | [gb.tower.10_80.m64](3-gelato-beach/gb.tower.10_80.m64) | [gb.tower.st](3-gelato-beach/gb.tower.st) | [gb.tower.10_80.m64](archive/3-gelato-beach/gb.tower.10_80.m64) [gb.tower.st](archive/3-gelato-beach/gb.tower.st) | — |  |
| Angry Wiggler Awoke | 31.60 | ChouxZi3 | needs optimisation | [gb.wiggler.31_60.m64](3-gelato-beach/gb.wiggler.31_60.m64) | [gb.wiggler.st](3-gelato-beach/gb.wiggler.st) | [gb.wiggler.31_60.m64](archive/3-gelato-beach/gb.wiggler.31_60.m64) [gb.wiggler.st](archive/3-gelato-beach/gb.wiggler.st) | — | sheet: "will most likely be retased in the full game run due to rng" |
| 8 Underwater Redcoins | — | — | inapplicable | — | — | — | — | no files linked on the sheet |
| Shell-Ride Through Panels | 23.17 | ChouxZi3, FeijoadaMolhada | needs optimisation | [gb.shell_ride.23_17.m64](3-gelato-beach/gb.shell_ride.23_17.m64) | [gb.shell_ride.st](3-gelato-beach/gb.shell_ride.st) | [gb.shell_ride.23_17.m64](archive/3-gelato-beach/gb.shell_ride.23_17.m64) [gb.shell_ride.st](archive/3-gelato-beach/gb.shell_ride.st) | — |  |
| Double Cap Trouble | 22.07 | ChouxZi3 | needs optimisation | [gb.double_cap.22_07.m64](3-gelato-beach/gb.double_cap.22_07.m64) | [gb.double_cap.st](3-gelato-beach/gb.double_cap.st) | [gb.double_cap.22_07.m64](archive/3-gelato-beach/gb.double_cap.22_07.m64) [gb.double_cap.st](archive/3-gelato-beach/gb.double_cap.st) | — |  |
| 100 Coins | 1:55.80 | ChouxZi3, Kieran | needs optimisation | [gb.100c.115_80.m64](3-gelato-beach/gb.100c.115_80.m64) | [gb.100c.st](3-gelato-beach/gb.100c.st) | [gb.100c.115_80.m64](archive/3-gelato-beach/gb.100c.115_80.m64) [gb.100c.st](archive/3-gelato-beach/gb.100c.st) | — | sheet: "paired with reds. improvement"; the comment's improvement is a Discord message link (not a file) in a server this archive's account cannot read: not retrieved |

### 4. The White Abyss

| Star | Time | Author/s | Status | .m64 | .st | Originals | Other files | Notes |
|---|---|---|---|---|---|---|---|---|
| Get to the Checkpoint | 31.60 | ChouxZi3 | needs optimisation | [wa.checkpoint.31_60.m64](4-the-white-abyss/wa.checkpoint.31_60.m64) | [wa.checkpoint.st](4-the-white-abyss/wa.checkpoint.st) | [wa.checkpoint.31_60.m64](archive/4-the-white-abyss/wa.checkpoint.31_60.m64) [wa.checkpoint.st](archive/4-the-white-abyss/wa.checkpoint.st) | — | the sheet's rerecords are 11965 + 1130; the .m64 header has 1130 |
| 8 Red Coins in the Mountain | — | — | inapplicable | — | — | — | — | no files linked on the sheet |
| Find the Ice Sanctuary | 17.03 | ChouxZi3 | needs optimisation | [wa.ice_sanctuary.17_03.m64](4-the-white-abyss/wa.ice_sanctuary.17_03.m64) | [wa.ice_sanctuary.st](4-the-white-abyss/wa.ice_sanctuary.st) | [wa.ice_sanctuary.17_03.m64](archive/4-the-white-abyss/wa.ice_sanctuary.17_03.m64) [wa.ice_sanctuary.st](archive/4-the-white-abyss/wa.ice_sanctuary.st) | — | sheet: "from star 1 checkpoint" |
| Explore the Sanctuary | 10.87 | ChouxZi3 | needs optimisation | [wa.explore_sanctuary.10_87.m64](4-the-white-abyss/wa.explore_sanctuary.10_87.m64) | [wa.explore_sanctuary.st](4-the-white-abyss/wa.explore_sanctuary.st) | [wa.explore_sanctuary.10_87.m64](archive/4-the-white-abyss/wa.explore_sanctuary.10_87.m64) [wa.explore_sanctuary.st](archive/4-the-white-abyss/wa.explore_sanctuary.st) | — | sheet: "from star 3 checkpoint" |
| Chill Out the Ice Guardian | 15.87 | ChouxZi3 | needs optimisation | [wa.ice_guardian.15_87.m64](4-the-white-abyss/wa.ice_guardian.15_87.m64) | [wa.ice_guardian.st](4-the-white-abyss/wa.ice_guardian.st) | [wa.ice_guardian.15_87.m64](archive/4-the-white-abyss/wa.ice_guardian.15_87.m64) [wa.ice_guardian.st](archive/4-the-white-abyss/wa.ice_guardian.st) | — | sheet: "from star 1 checkpoint" |
| Spring Up the Ice Cave | 8.87 | ChouxZi3 | needs optimisation | [wa.ice_cave.8_87.m64](4-the-white-abyss/wa.ice_cave.8_87.m64) | [wa.ice_cave.st](4-the-white-abyss/wa.ice_cave.st) | [wa.ice_cave.8_87.m64](archive/4-the-white-abyss/wa.ice_cave.8_87.m64) [wa.ice_cave.st](archive/4-the-white-abyss/wa.ice_cave.st) | — | sheet: "from star 3 checkpoint" |
| 100 Coins + 8 Red Coins in the Mountain | 1:14.43 | ChouxZi3 | needs optimisation | [wa.100c_reds.74_43.m64](4-the-white-abyss/wa.100c_reds.74_43.m64) | [wa.100c_reds.st](4-the-white-abyss/wa.100c_reds.st) | [wa.100c_reds.74_43.m64](archive/4-the-white-abyss/wa.100c_reds.74_43.m64) [wa.100c_reds.st](archive/4-the-white-abyss/wa.100c_reds.st) | — | sheet: "from star 1 checkpoint" |

### The Dream Realm

| Star | Time | Author/s | Status | .m64 | .st | Originals | Other files | Notes |
|---|---|---|---|---|---|---|---|---|
| Course 1 | 14.47 | ChouxZi3 | needs optimisation | [dr.course1.14_47.m64](dream-realm/dr.course1.14_47.m64) | [dr.course1.st](dream-realm/dr.course1.st) | [dr.course1.14_47.m64](archive/dream-realm/dr.course1.14_47.m64) [dr.course1.st](archive/dream-realm/dr.course1.st) | — | by the sheet's rule (VIs) 14.63: the sheet's 14.47 leaves out the dream warp's 12-VI load |
| Course 2 | 25.63 | RSw, FeijoadaMolhada, ChouxZi3 | needs optimisation | [dr.course2.25_63.m64](dream-realm/dr.course2.25_63.m64) | [dr.course2.st](dream-realm/dr.course2.st) | [dr.course2.25_63.m64](archive/dream-realm/dr.course2.25_63.m64) [dr.course2.st](archive/dream-realm/dr.course2.st) | — | sheet: "precise grindel rng. rng might be more lenient with a better blj setup" |
| Course 3 | 23.50 | ChouxZi3, FeijoadaMolhada | needs optimisation | [dr.course3.23_50.m64](dream-realm/dr.course3.23_50.m64) | [dr.course3.st](dream-realm/dr.course3.st) | [dr.course3.23_50.m64](archive/dream-realm/dr.course3.23_50.m64) [dr.course3.st](archive/dream-realm/dr.course3.st) | — | by the sheet's rule (VIs) 23.67: the sheet's 23.50 leaves out the dream warp's 12-VI load |
| Course 4 | 12.53 | ChouxZi3 | needs optimisation | [dr.course4.12_53.m64](dream-realm/dr.course4.12_53.m64) | [dr.course4.st](dream-realm/dr.course4.st) | [dr.course4.12_53.m64](archive/dream-realm/dr.course4.12_53.m64) [dr.course4.st](archive/dream-realm/dr.course4.st) | — | sheet: "from star 3 checkpoint" |
| Toad | 19.60 | ChouxZi3 | needs optimisation | [dr.toad.19_60.m64](dream-realm/dr.toad.19_60.m64) | [dr.toad.st](dream-realm/dr.toad.st) | [dr.toad.19_60.m64](archive/dream-realm/dr.toad.19_60.m64) [dr.toad.st](archive/dream-realm/dr.toad.st) | — |  |

### Cap Levels

| Star | Time | Author/s | Status | .m64 | .st | Originals | Other files | Notes |
|---|---|---|---|---|---|---|---|---|
| WC. Wing Cap Windy Towers | 1:09.97 | ChouxZi3, RSw | needs optimisation | [wc.windy_towers.69_97.m64](cap-levels/wc.windy_towers.69_97.m64) | [wc.windy_towers.st](cap-levels/wc.windy_towers.st) | [wc.windy_towers.69_97.m64](archive/cap-levels/wc.windy_towers.69_97.m64) [wc.windy_towers.st](archive/cap-levels/wc.windy_towers.st) | — | sheet: "flying still sucks" |
| VC. Vanishcap Ghostly Puzzle | 50.80 | ChouxZi3 | needs optimisation | [vc.ghostly_puzzle.50_80.m64](cap-levels/vc.ghostly_puzzle.50_80.m64) | [vc.ghostly_puzzle.st](cap-levels/vc.ghostly_puzzle.st) | [vc.ghostly_puzzle.50_80.m64](archive/cap-levels/vc.ghostly_puzzle.50_80.m64) [vc.ghostly_puzzle.st](archive/cap-levels/vc.ghostly_puzzle.st) | — |  |
| MC. Metal Cap Sewers - Left Door | 18.13 | RSw, ChouxZi3 | needs optimisation | [mc.sewers_left.18_13.m64](cap-levels/mc.sewers_left.18_13.m64) | [mc.sewers_left.st](cap-levels/mc.sewers_left.st) | [mc.sewers_left.18_13.m64](archive/cap-levels/mc.sewers_left.18_13.m64) [mc.sewers_left.st](archive/cap-levels/mc.sewers_left.st) | — | sheet: "pretty sure we dont need mc at all" |
| MC. Metal Cap Sewers - Right Door | 18.13 | RSw, ChouxZi3 | needs optimisation | [mc.sewers_right.18_13.m64](cap-levels/mc.sewers_right.18_13.m64) | [mc.sewers_right.st](cap-levels/mc.sewers_right.st) | [mc.sewers_right.18_13.m64](archive/cap-levels/mc.sewers_right.18_13.m64) [mc.sewers_right.st](archive/cap-levels/mc.sewers_right.st) | — | sheet: "assumes 280 swimming strength" |

### Miscellaneous

| Star | Time | Author/s | Status | .m64 | .st | Originals | Other files | Notes |
|---|---|---|---|---|---|---|---|---|
| Mountain of Serenity - Red Coins | 26.07 | ChouxZi3 | needs optimisation | [mos.reds.26_07.m64](miscellaneous/mos.reds.26_07.m64) | [mos.reds.st](miscellaneous/mos.reds.st) | [mos.reds.26_07.m64](archive/miscellaneous/mos.reds.26_07.m64) [mos.reds.st](archive/miscellaneous/mos.reds.st) | — |  |
| Cyberwave Trial - Red Coins | 1:20.20 | ChouxZi3 | needs optimisation | [cwt.reds.80_20.m64](miscellaneous/cwt.reds.80_20.m64) | [cwt.reds.st](miscellaneous/cwt.reds.st) | [cwt.reds.80_20.m64](archive/miscellaneous/cwt.reds.80_20.m64) [cwt.reds.st](archive/miscellaneous/cwt.reds.st) | — | sheet: "requires 49 stars to access."; the sheet's rerecords are 7532 + 3300; the .m64 header has 3300 |
| Goombas Lair | 1:28.00 | ChouxZi3 | needs optimisation | [gl.goombas_lair.88_00.m64](miscellaneous/gl.goombas_lair.88_00.m64) | [gl.goombas_lair.st](miscellaneous/gl.goombas_lair.st) | [gl.goombas_lair.88_00.m64](archive/miscellaneous/gl.goombas_lair.88_00.m64) [gl.goombas_lair.st](archive/miscellaneous/gl.goombas_lair.st) | — |  |
| Rainbow Road | 1:44.20 | FeijoadaMolhada | needs optimisation | [rr.rainbow_road.104_20.m64](miscellaneous/rr.rainbow_road.104_20.m64) | [rr.rainbow_road.st](miscellaneous/rr.rainbow_road.st) | [rr.rainbow_road.104_20.m64](archive/miscellaneous/rr.rainbow_road.104_20.m64) [rr.rainbow_road.st](archive/miscellaneous/rr.rainbow_road.st) | [rr.rainbow_road.improvement_higher_flyguy.m64](archive/miscellaneous/rr.rainbow_road.improvement_higher_flyguy.m64) | sheet: "requires 30 stars to access. cannon is skipable. improvement"; the comment's improvement (`improvement_higher_flyguy`) is a draft: the 1:44.20's inputs to input 848, new from 849, 1420 inputs, no star |
| Tick Tock Chaos | 40.10 | ChouxZi3 | needs optimisation | [ttc.tick_tock_chaos.40_10.m64](miscellaneous/ttc.tick_tock_chaos.40_10.m64) | [ttc.tick_tock_chaos.st](miscellaneous/ttc.tick_tock_chaos.st) | [ttc.tick_tock_chaos.40_10.m64](archive/miscellaneous/ttc.tick_tock_chaos.40_10.m64) [ttc.tick_tock_chaos.st](archive/miscellaneous/ttc.tick_tock_chaos.st) | — |  |

### Bowser Levels

| Star | Time | Author/s | Status | .m64 | .st | Originals | Other files | Notes |
|---|---|---|---|---|---|---|---|---|
| B1. In the Ghost House | 13.37 | ChouxZi3 | needs optimisation | [b1.ghost_house.13_37.m64](bowser-levels/b1.ghost_house.13_37.m64) | [b1.ghost_house.st](bowser-levels/b1.ghost_house.st) | [b1.ghost_house.13_37.m64](archive/bowser-levels/b1.ghost_house.13_37.m64) [b1.ghost_house.st](archive/bowser-levels/b1.ghost_house.st) | — | sheet: "star time only" |
| B2. Into the Mountain Temple | 29.07 | ChouxZi3 | needs optimisation | [b2.mountain_temple.29_07.m64](bowser-levels/b2.mountain_temple.29_07.m64) | [b2.mountain_temple.st](bowser-levels/b2.mountain_temple.st) | — | — | sheet: "star time only"; the linked movie desyncs from its savestate (Mario lands in lava at input ~560 and falls to a death exit; its .st is the 2023 B2 battle state): not rebased, kept as uploaded; not rebased: the original files, as uploaded |
| B3. The Nightmare Realm | 1:49.77 | ChouxZi3, RSw | needs optimisation | [b3.nightmare_realm.124_00.m64](bowser-levels/b3.nightmare_realm.124_00.m64) | [b3.nightmare_realm.st](bowser-levels/b3.nightmare_realm.st) | [b3.nightmare_realm.124_00.m64](archive/bowser-levels/b3.nightmare_realm.124_00.m64) [b3.nightmare_realm.st](archive/bowser-levels/b3.nightmare_realm.st) | [b3.nightmare_realm.improvement_109_77.m64](archive/bowser-levels/b3.nightmare_realm.improvement_109_77.m64) | sheet: "red coins only - improvement"; the linked movie replays to 2:04.00; the sheet's 1:49.77 isn't backed by a complete movie: the comment's improvement (`improvement_109_77`) is a draft (the 2:04.00's inputs to input 406, new from 407, 644 inputs, no star) |
| B1. In the Ghost House - Battle | 27.93 | ChouxZi3 | inapplicable | [b1.ghost_house_battle.22_20.m64](bowser-levels/b1.ghost_house_battle.22_20.m64) | [b1.ghost_house_battle.st](bowser-levels/b1.ghost_house_battle.st) | [b1.ghost_house_battle.22_20.m64](archive/bowser-levels/b1.ghost_house_battle.22_20.m64) [b1.ghost_house_battle.st](archive/bowser-levels/b1.ghost_house_battle.st) | — | the movie is the arena fight only (the course part, with its older 22.20 secret star, is in the original) |
| B2. Into the Mountain Temple - Battle | 32.60 | ChouxZi3 | needs optimisation | [b2.mountain_temple_battle.30_10.m64](bowser-levels/b2.mountain_temple_battle.30_10.m64) | [b2.mountain_temple_battle.st](bowser-levels/b2.mountain_temple_battle.st) | [b2.mountain_temple_battle.30_10.m64](archive/bowser-levels/b2.mountain_temple_battle.30_10.m64) [b2.mountain_temple_battle.st](archive/bowser-levels/b2.mountain_temple_battle.st) | — | the movie is the arena fight only (the course part, with its older 30.10 secret star, is in the original) |
| B3. The Nightmare Realm - Battle | — | — | open | — | — | — | — | no files linked on the sheet |
