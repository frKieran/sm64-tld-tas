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

## Files

- **One folder per course,** like the sheet's sections: `1-playful-palace`, `2-bob-omb-temple`, `3-gelato-beach`,
  `4-the-white-abyss`, `dream-realm`, `cap-levels`, `miscellaneous`, `bowser-levels`.
- **Names:** `<course>.<star>.<time>.m64`, and its savestate is `<course>.<star>.st`, for example
  `pp.dusk_whomp.44_67.m64` and `pp.dusk_whomp.st`.
  - Course codes: `pp` Playful Palace, `bt` Bob-omb Temple, `gb` Gelato Beach, `wa` The White Abyss, `dr` The Dream
    Realm, `wc` / `vc` / `mc` the cap levels, `mos` Mountain of Serenity, `cwt` Cyberwave Trial, `gl` Goombas Lair,
    `rr` Rainbow Road, `ttc` Tick Tock Chaos, `b1` / `b2` / `b3` the Bowser levels.
  - The time is in seconds, `SS_CC` (2:49.73 is `169_73`), as in the sm64-island-tas repo. It is the time in the
    original file name when it had one, otherwise the sheet's. Where the two differ, the table's Notes say so.
- **Contents are unchanged:** every file is byte-for-byte the downloaded attachment. Only the names changed, and the
  savestate extension `.savestate` became `.st`. `manifest.csv` / `manifest.json` give each file's original name,
  original Discord URL, size and SHA-256.
- **Each movie has its own savestate,** even where several are the same file (see Duplicates), so every pair stays
  together.
- **Other files** come from links in the sheet's Comments column:
  - `pp.lonely_shroom.hyperjump_14_73.zip`: the slower hyperjump strat, as uploaded. It holds
    `TotheLonelyShroom1473.m64` and `TotheLonelyShroom1473.savestate`.
  - `rr.rainbow_road.improvement_higher_flyguy.m64`: linked as an "improvement". It has 1420 samples, against the
    main movie's 3600.
  - `b3.nightmare_realm.improvement_109_77.m64`: linked as an "improvement" (originally `smtld_b3.10977 - Copy.m64`).
    Its 1:49.77 is the time the sheet shows for the star.
  - These keep their star's prefix, so Mupen offers them the star's savestate. Whether they were made from that
    savestate is not checked.

## Playing a movie

- Use Mupen64 (mupen64-rr-lua) with the Super Mario The Lost Dreams v1.2h ROM.
- Keep each `.m64` in the same folder as its `.st`. Mupen plays `a.b.c.m64` from `a.b.c.st`, else `a.b.st`, else
  `a.st`.
- The savestates come from two Mupen generations (10.5 MB and 21 MB unpacked, all gzip). An old Mupen may not load
  the larger ones.
- 31 movies have input data after their header's sample count. Mupen keeps the old inputs when you re-record from an
  earlier frame, and playback stops at the count. They are kept as uploaded.

## What was checked

- Every sheet link was accounted for: 89 attachment links downloaded, and 1 Discord message link not retrieved
  (below).
- Every `.m64` has a valid header, names the TLD ROM, starts from a snapshot, and is not shorter than its sample
  count.
- Every savestate decompresses with no CRC error and records the TLD v1.2h ROM.
- The `.zip` passes its CRC test.
- **Not checked:** playing each movie in Mupen to its star. The files are archived as uploaded.

## Missing, questionable and duplicate files

- **Entries with no files on the sheet (5):**
  - Find 8 Red Coins (Playful Palace): "done in 100c".
  - 8 Risky Red Coins (Bob-omb Temple): 41.70 by ChouxZi3, no links.
  - 8 Underwater Redcoins (Gelato Beach).
  - 8 Red Coins in the Mountain (The White Abyss).
  - B3. The Nightmare Realm - Battle (status "open").
- **Not retrieved (1):** the Gelato Beach 100 Coins comment ("paired with reds. improvement") links to a Discord
  message (`discord.com/channels/929005491634442260/929005491634442263/1529915408986149077`), not a file. The
  account used for the download cannot read that server. The sheet's own 100c files (115.80) are archived.
- **Linked file and sheet time differ:**
  - Fly Through the Abyss: the file is 25.10, the sheet says 14.70.
  - B3. The Nightmare Realm: the linked file is 124.00, the sheet says 1:49.77. The comment's improvement file
    matches the sheet.
  - B1 battle: the file is 22.20, the sheet says 27.93.
  - B2 battle: the file is 30.10, the sheet says 32.60.
- **Duplicates:** no two links point to the same URL, and no two movies are the same file. Several savestates are
  byte-identical, being the same course entry state:
  - Playful Palace: `dusk_whomp` = `switch_way` = Dream Realm `course1`, and `lonely_shroom` = `deep_palace` =
    `fire_chamber`.
  - Bob-omb Temple: `dusk_bobomb` = `deep_temple` = `fly_abyss`.
  - Gelato Beach: `waterfall` = `tower` = `shell_ride` = `double_cap` = Dream Realm `course3`.
  - The White Abyss: `explore_sanctuary` = `ice_guardian` = `ice_cave` = Dream Realm `course4`.
  - Bowser levels: `b1.ghost_house` = `b1.ghost_house_battle`, and `b2.mountain_temple` = `b2.mountain_temple_battle`.
  - Two different savestates were both named `mc.savestate` (Metal Cap left and right door). They are
    `mc.sewers_left.st` and `mc.sewers_right.st` here.

## Stars

### 1. Playful Palace

| Star | Time | Author/s | Status | .m64 | .st | Other files | Notes |
|---|---|---|---|---|---|---|---|
| Defeat the Dusk Whomp | 44.67 | RSw | inapplicable | [pp.dusk_whomp.44_67.m64](1-playful-palace/pp.dusk_whomp.44_67.m64) | [pp.dusk_whomp.st](1-playful-palace/pp.dusk_whomp.st) | — |  |
| To the Lonely Shroom | 10.70 | RSw, FeijoadaMolhada | done | [pp.lonely_shroom.10_70.m64](1-playful-palace/pp.lonely_shroom.10_70.m64) | [pp.lonely_shroom.st](1-playful-palace/pp.lonely_shroom.st) | [pp.lonely_shroom.hyperjump_14_73.zip](1-playful-palace/pp.lonely_shroom.hyperjump_14_73.zip) | sheet: "true rr count, hyperjump strat is slower" |
| Find 8 Red Coins | — | RSw | inapplicable | — | — | — | sheet: "done in 100c"; no files linked on the sheet |
| Deep into the Palace | 11.73 | RSw, ChouxZi3, feijoadamolhada | optimised | [pp.deep_palace.11_73.m64](1-playful-palace/pp.deep_palace.11_73.m64) | [pp.deep_palace.st](1-playful-palace/pp.deep_palace.st) | — |  |
| Switch-Way to the Top | 37.47 | RSw | inapplicable | [pp.switch_way.37_47.m64](1-playful-palace/pp.switch_way.37_47.m64) | [pp.switch_way.st](1-playful-palace/pp.switch_way.st) | — | sheet: "might be better to do reverse order, clone star + cancel"; the original name has no time; the file name uses the sheet's 37.47 |
| Vanishcap and the Fire Chamber | 8.70 | RSw, FeijoadaMolhada | done | [pp.fire_chamber.8_70.m64](1-playful-palace/pp.fire_chamber.8_70.m64) | [pp.fire_chamber.st](1-playful-palace/pp.fire_chamber.st) | — | sheet: "negative jump strat" |
| Defeat the Dusk Whomp + 100 Coins | 2:49.73 | RSw | needs optimisation | [pp.dusk_whomp_100c.169_73.m64](1-playful-palace/pp.dusk_whomp_100c.169_73.m64) | [pp.dusk_whomp_100c.st](1-playful-palace/pp.dusk_whomp_100c.st) | — | sheet: "reds + switches included, lotad" |

### 2. Bob-omb Temple

| Star | Time | Author/s | Status | .m64 | .st | Other files | Notes |
|---|---|---|---|---|---|---|---|
| Defeat the Dusk Bob-omb | 63.77 | tjk, FeijoadaMolhada, ChouxZi3 | needs optimisation | [bt.dusk_bobomb.63_77.m64](2-bob-omb-temple/bt.dusk_bobomb.63_77.m64) | [bt.dusk_bobomb.st](2-bob-omb-temple/bt.dusk_bobomb.st) | — | sheet: "no quick releases" |
| Deep into the Temple | 10.20 | FeijoadaMolhada, ChouxZi3 | needs optimisation | [bt.deep_temple.10_20.m64](2-bob-omb-temple/bt.deep_temple.10_20.m64) | [bt.deep_temple.st](2-bob-omb-temple/bt.deep_temple.st) | — |  |
| 8 Risky Red Coins | 41.70 | ChouxZi3 | inapplicable | — | — | — | no files linked on the sheet |
| The High Room | 17.93 | FeijoadaMolhada | inapplicable | [bt.high_room.17_93.m64](2-bob-omb-temple/bt.high_room.17_93.m64) | [bt.high_room.st](2-bob-omb-temple/bt.high_room.st) | — |  |
| Cannon and Vanishcap | 9.70 | FeijoadaMolhada | needs optimisation | [bt.cannon_vanishcap.9_70.m64](2-bob-omb-temple/bt.cannon_vanishcap.9_70.m64) | [bt.cannon_vanishcap.st](2-bob-omb-temple/bt.cannon_vanishcap.st) | — |  |
| Fly Through the Abyss | 14.70 | FeijoadaMolhada, ChouxZi3 | needs optimisation | [bt.fly_abyss.25_10.m64](2-bob-omb-temple/bt.fly_abyss.25_10.m64) | [bt.fly_abyss.st](2-bob-omb-temple/bt.fly_abyss.st) | — | sheet: "grindel rng"; the linked .m64's name says 25.10 and its header 71 rerecords; the sheet says 14.70 and 732, so the link may be an older or different movie |
| The High Room + 100 Coins | 2:09.47 | ChouxZi3 | needs optimisation | [bt.high_room_100c.129_47.m64](2-bob-omb-temple/bt.high_room_100c.129_47.m64) | [bt.high_room_100c.st](2-bob-omb-temple/bt.high_room_100c.st) | — | sheet: "reds included, rng heavy" |

### 3. Gelato Beach

| Star | Time | Author/s | Status | .m64 | .st | Other files | Notes |
|---|---|---|---|---|---|---|---|
| Waterfall in the Distance | 14.73 | ChouxZi3, FeijoadaMolhada | needs optimisation | [gb.waterfall.14_73.m64](3-gelato-beach/gb.waterfall.14_73.m64) | [gb.waterfall.st](3-gelato-beach/gb.waterfall.st) | — |  |
| Climb up the Tower | 10.80 | ChouxZi3 | needs optimisation | [gb.tower.10_80.m64](3-gelato-beach/gb.tower.10_80.m64) | [gb.tower.st](3-gelato-beach/gb.tower.st) | — |  |
| Angry Wiggler Awoke | 31.60 | ChouxZi3 | needs optimisation | [gb.wiggler.31_60.m64](3-gelato-beach/gb.wiggler.31_60.m64) | [gb.wiggler.st](3-gelato-beach/gb.wiggler.st) | — | sheet: "will most likely be retased in the full game run due to rng" |
| 8 Underwater Redcoins | — | — | inapplicable | — | — | — | no files linked on the sheet |
| Shell-Ride Through Panels | 23.17 | ChouxZi3, FeijoadaMolhada | needs optimisation | [gb.shell_ride.23_17.m64](3-gelato-beach/gb.shell_ride.23_17.m64) | [gb.shell_ride.st](3-gelato-beach/gb.shell_ride.st) | — |  |
| Double Cap Trouble | 22.07 | ChouxZi3 | needs optimisation | [gb.double_cap.22_07.m64](3-gelato-beach/gb.double_cap.22_07.m64) | [gb.double_cap.st](3-gelato-beach/gb.double_cap.st) | — |  |
| 100 Coins | 1:55.80 | ChouxZi3, Kieran | needs optimisation | [gb.100c.115_80.m64](3-gelato-beach/gb.100c.115_80.m64) | [gb.100c.st](3-gelato-beach/gb.100c.st) | — | sheet: "paired with reds. improvement"; the comment's improvement is a Discord message link (not a file) in a server this archive's account cannot read: not retrieved |

### 4. The White Abyss

| Star | Time | Author/s | Status | .m64 | .st | Other files | Notes |
|---|---|---|---|---|---|---|---|
| Get to the Checkpoint | 31.60 | ChouxZi3 | needs optimisation | [wa.checkpoint.31_60.m64](4-the-white-abyss/wa.checkpoint.31_60.m64) | [wa.checkpoint.st](4-the-white-abyss/wa.checkpoint.st) | — | the sheet's rerecords are 11965 + 1130; the .m64 header has 1130 |
| 8 Red Coins in the Mountain | — | — | inapplicable | — | — | — | no files linked on the sheet |
| Find the Ice Sanctuary | 17.03 | ChouxZi3 | needs optimisation | [wa.ice_sanctuary.17_03.m64](4-the-white-abyss/wa.ice_sanctuary.17_03.m64) | [wa.ice_sanctuary.st](4-the-white-abyss/wa.ice_sanctuary.st) | — | sheet: "from star 1 checkpoint" |
| Explore the Sanctuary | 10.87 | ChouxZi3 | needs optimisation | [wa.explore_sanctuary.10_87.m64](4-the-white-abyss/wa.explore_sanctuary.10_87.m64) | [wa.explore_sanctuary.st](4-the-white-abyss/wa.explore_sanctuary.st) | — | sheet: "from star 3 checkpoint" |
| Chill Out the Ice Guardian | 15.87 | ChouxZi3 | needs optimisation | [wa.ice_guardian.15_87.m64](4-the-white-abyss/wa.ice_guardian.15_87.m64) | [wa.ice_guardian.st](4-the-white-abyss/wa.ice_guardian.st) | — | sheet: "from star 1 checkpoint" |
| Spring Up the Ice Cave | 8.87 | ChouxZi3 | needs optimisation | [wa.ice_cave.8_87.m64](4-the-white-abyss/wa.ice_cave.8_87.m64) | [wa.ice_cave.st](4-the-white-abyss/wa.ice_cave.st) | — | sheet: "from star 3 checkpoint" |
| 100 Coins + 8 Red Coins in the Mountain | 1:14.43 | ChouxZi3 | needs optimisation | [wa.100c_reds.74_43.m64](4-the-white-abyss/wa.100c_reds.74_43.m64) | [wa.100c_reds.st](4-the-white-abyss/wa.100c_reds.st) | — | sheet: "from star 1 checkpoint" |

### The Dream Realm

| Star | Time | Author/s | Status | .m64 | .st | Other files | Notes |
|---|---|---|---|---|---|---|---|
| Course 1 | 14.47 | ChouxZi3 | needs optimisation | [dr.course1.14_47.m64](dream-realm/dr.course1.14_47.m64) | [dr.course1.st](dream-realm/dr.course1.st) | — |  |
| Course 2 | 25.63 | RSw, FeijoadaMolhada, ChouxZi3 | needs optimisation | [dr.course2.25_63.m64](dream-realm/dr.course2.25_63.m64) | [dr.course2.st](dream-realm/dr.course2.st) | — | sheet: "precise grindel rng. rng might be more lenient with a better blj setup" |
| Course 3 | 23.50 | ChouxZi3, FeijoadaMolhada | needs optimisation | [dr.course3.23_50.m64](dream-realm/dr.course3.23_50.m64) | [dr.course3.st](dream-realm/dr.course3.st) | — |  |
| Course 4 | 12.53 | ChouxZi3 | needs optimisation | [dr.course4.12_53.m64](dream-realm/dr.course4.12_53.m64) | [dr.course4.st](dream-realm/dr.course4.st) | — | sheet: "from star 3 checkpoint" |
| Toad | 19.60 | ChouxZi3 | needs optimisation | [dr.toad.19_60.m64](dream-realm/dr.toad.19_60.m64) | [dr.toad.st](dream-realm/dr.toad.st) | — |  |

### Cap Levels

| Star | Time | Author/s | Status | .m64 | .st | Other files | Notes |
|---|---|---|---|---|---|---|---|
| WC. Wing Cap Windy Towers | 1:09.97 | ChouxZi3, RSw | needs optimisation | [wc.windy_towers.69_97.m64](cap-levels/wc.windy_towers.69_97.m64) | [wc.windy_towers.st](cap-levels/wc.windy_towers.st) | — | sheet: "flying still sucks" |
| VC. Vanishcap Ghostly Puzzle | 50.80 | ChouxZi3 | needs optimisation | [vc.ghostly_puzzle.50_80.m64](cap-levels/vc.ghostly_puzzle.50_80.m64) | [vc.ghostly_puzzle.st](cap-levels/vc.ghostly_puzzle.st) | — |  |
| MC. Metal Cap Sewers - Left Door | 18.13 | RSw, ChouxZi3 | needs optimisation | [mc.sewers_left.18_13.m64](cap-levels/mc.sewers_left.18_13.m64) | [mc.sewers_left.st](cap-levels/mc.sewers_left.st) | — | sheet: "pretty sure we dont need mc at all" |
| MC. Metal Cap Sewers - Right Door | 18.13 | RSw, ChouxZi3 | needs optimisation | [mc.sewers_right.18_13.m64](cap-levels/mc.sewers_right.18_13.m64) | [mc.sewers_right.st](cap-levels/mc.sewers_right.st) | — | sheet: "assumes 280 swimming strength" |

### Miscellaneous

| Star | Time | Author/s | Status | .m64 | .st | Other files | Notes |
|---|---|---|---|---|---|---|---|
| Mountain of Serenity - Red Coins | 26.07 | ChouxZi3 | needs optimisation | [mos.reds.26_07.m64](miscellaneous/mos.reds.26_07.m64) | [mos.reds.st](miscellaneous/mos.reds.st) | — |  |
| Cyberwave Trial - Red Coins | 1:20.20 | ChouxZi3 | needs optimisation | [cwt.reds.80_20.m64](miscellaneous/cwt.reds.80_20.m64) | [cwt.reds.st](miscellaneous/cwt.reds.st) | — | sheet: "requires 49 stars to access."; the sheet's rerecords are 7532 + 3300; the .m64 header has 3300 |
| Goombas Lair | 1:28.00 | ChouxZi3 | needs optimisation | [gl.goombas_lair.88_00.m64](miscellaneous/gl.goombas_lair.88_00.m64) | [gl.goombas_lair.st](miscellaneous/gl.goombas_lair.st) | — |  |
| Rainbow Road | 1:44.20 | FeijoadaMolhada | needs optimisation | [rr.rainbow_road.104_20.m64](miscellaneous/rr.rainbow_road.104_20.m64) | [rr.rainbow_road.st](miscellaneous/rr.rainbow_road.st) | [rr.rainbow_road.improvement_higher_flyguy.m64](miscellaneous/rr.rainbow_road.improvement_higher_flyguy.m64) | sheet: "requires 30 stars to access. cannon is skipable. improvement" |
| Tick Tock Chaos | 40.10 | ChouxZi3 | needs optimisation | [ttc.tick_tock_chaos.40_10.m64](miscellaneous/ttc.tick_tock_chaos.40_10.m64) | [ttc.tick_tock_chaos.st](miscellaneous/ttc.tick_tock_chaos.st) | — |  |

### Bowser Levels

| Star | Time | Author/s | Status | .m64 | .st | Other files | Notes |
|---|---|---|---|---|---|---|---|
| B1. In the Ghost House | 13.37 | ChouxZi3 | needs optimisation | [b1.ghost_house.13_37.m64](bowser-levels/b1.ghost_house.13_37.m64) | [b1.ghost_house.st](bowser-levels/b1.ghost_house.st) | — | sheet: "star time only" |
| B2. Into the Mountain Temple | 29.07 | ChouxZi3 | needs optimisation | [b2.mountain_temple.29_07.m64](bowser-levels/b2.mountain_temple.29_07.m64) | [b2.mountain_temple.st](bowser-levels/b2.mountain_temple.st) | — | sheet: "star time only" |
| B3. The Nightmare Realm | 1:49.77 | ChouxZi3, RSw | needs optimisation | [b3.nightmare_realm.124_00.m64](bowser-levels/b3.nightmare_realm.124_00.m64) | [b3.nightmare_realm.st](bowser-levels/b3.nightmare_realm.st) | [b3.nightmare_realm.improvement_109_77.m64](bowser-levels/b3.nightmare_realm.improvement_109_77.m64) | sheet: "red coins only - improvement"; the linked .m64 is 124.00 (name); the sheet's 1:49.77 matches the comment's improvement file (`improvement_109_77`) |
| B1. In the Ghost House - Battle | 27.93 | ChouxZi3 | inapplicable | [b1.ghost_house_battle.22_20.m64](bowser-levels/b1.ghost_house_battle.22_20.m64) | [b1.ghost_house_battle.st](bowser-levels/b1.ghost_house_battle.st) | — | the linked .m64's name says 22.20; the sheet says 27.93 |
| B2. Into the Mountain Temple - Battle | 32.60 | ChouxZi3 | needs optimisation | [b2.mountain_temple_battle.30_10.m64](bowser-levels/b2.mountain_temple_battle.30_10.m64) | [b2.mountain_temple_battle.st](bowser-levels/b2.mountain_temple_battle.st) | — | the linked .m64's name says 30.10; the sheet says 32.60 |
| B3. The Nightmare Realm - Battle | — | — | open | — | — | — | no files linked on the sheet |
