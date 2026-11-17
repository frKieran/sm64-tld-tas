# Castle and lobby movement

ChouxZi3's movements between levels: from one star's exit (or an Exit Course) to the next level's warp. The "Castle
Movement" tab of the sheet lists them in the same order. It also has open rows for the movements not TASed yet: power-on
to Playful Palace, and a re-entry for every course the route enters more than once (Playful Palace, Gelato Beach,
Bob-omb Temple, The White Abyss). Its Count column says how often each movement is used. Metal Cap Sewers needs no
re-entry of its own: both cap stars exit to the Dream Realm's 0x90, so 08 (Vanishcap → Metal Cap) is also the way back
into Metal Cap after its first star, and it counts 2.

- **Time:** from the first controllable frame to the first frame of the warp action (the door walk, DISAPPEARED,
  TELEPORT_FADE_OUT, or the frame of an Exit Course / look-up / warp floor), in input frames / 30. **Real** is the
  VIs between the same two frames / 60: it adds the lag of the level loads inside a movement.
- **Boundaries:** `NN.st` is the last frame before the movement's first level loads (for 02, the frame before B1's
  star exit puts Mario at node 0x7B). The movie ends where the next course's standard state starts: the act select's
  first frame for Playful Palace, Bob-omb Temple, Gelato Beach and The White Abyss, the last frame before the level
  loads for the others. Every state is gzip and every pair plays in every Mupen version.
- **Checked:** each movie was played from its `NN.st` in Mupen and matches the original run on every frame (level,
  action, action timer, position, warp).

| # | Movement | Movie | Time | Frames | Real | Starts from | Ends: exit warp node → level |
|---|---|---|---|---|---|---|---|
| 01 | Playful Palace → B1. In the Ghost House | `01.pp_to_b1.7_50.m64` | 7.50 | 225 | 7.50 | a Dream Realm star exit: hub node 0x04, the hub's centre | hub door 0x06 → BITDW (17), node 0x0A |
| 02 | B1. In the Ghost House → Gelato Beach | `02.b1_to_gb.9_67.m64` | 9.67 | 290 | 9.95 | B1's star exit: BITDW node 0x7B | Exit Course → hub 0x8D, then hub pipe 0x07 → JRB (12), the act select |
| 03 | Gelato Beach → Tick Tock Chaos | `03.gb_to_ttc.7_20.m64` | 7.20 | 216 | 7.20 | a Dream Realm star exit: hub 0x04 | hub pipe 0x88 → RR (15), node 0x0A |
| 04 | Tick Tock Chaos → Bob-omb Temple | `04.ttc_to_bt.3_87.m64` | 3.87 | 116 | 3.87 | Tick Tock Chaos's star exit: hub 0x6A | hub pipe 0x05 → WF (24), the act select |
| 05 | Bob-omb Temple → The White Abyss | `05.bt_to_wa.8_00.m64` | 8.00 | 240 | 8.00 | a Dream Realm star exit: hub 0x04 | hub door 0x08 → CCM (5), the act select |
| 06 | The White Abyss → Rainbow Road | `06.wa_to_rr.12_97.m64` | 12.97 | 389 | 12.97 | a Dream Realm star exit: hub 0x04 | hub warp 0x0D → hub node 0x0E, then the look-up warp 0xF2 → PSS (27), node 0x0A |
| 07 | Rainbow Road → Vanishcap Ghostly Puzzle | `07.rr_to_vc.31_37.m64` | 31.37 | 941 | 32.73 | Rainbow Road's star exit: hub 0x1E | Dream Realm door 0x00 → VCUTM (18), node 0x0A |
| 08 | Vanishcap Ghostly Puzzle → Metal Cap Sewers | `08.vc_to_mc.4_67.m64` | 4.67 | 140 | 4.67 | Vanishcap's star exit: Dream Realm 0x90 | Dream Realm door 0x01 → COTMC (28), node 0x0A |
| 09 | Metal Cap Sewers → Wing Cap Windy Towers | `09.mc_to_wc.4_83.m64` | 4.83 | 145 | 4.83 | a Vanishcap star exit: Dream Realm 0x90, where Metal Cap's exit lands too | Dream Realm door 0x02 → TOTWC (29), node 0x0A |
| 10 | The Dream Realm Toad → Mountain of Serenity | `10.toad_to_mos.5_27.m64` | 5.27 | 158 | 5.27 | the Toad star's no-exit dance | Dream Realm pipe 0x03 → TTM (36), node 0x0A |
| 11 | B2. Into the Mountain Temple - Battle → B3. The Nightmare Realm | `11.b2battle_to_b3.19_37.m64` | 19.37 | 581 | 19.80 | B2's star exit: Mountain of Serenity 0x0E | level 6 door 0x0E → BITS (21), node 0x0A |
| 12 | B3. The Nightmare Realm → Goombas Lair | `12.b3_to_gl.33_30.m64` | 33.30 | 999 | 34.52 | the B3 stage with Exit Course under way | courtyard pipe 0x02 → SA (20), node 0x0A |
| 13 | Goombas Lair → Cyberwave Trial | `13.gl_to_cwt.5_50.m64` | 5.50 | 165 | 5.50 | Goombas Lair's star exit: courtyard 0x1C | courtyard fading warp 0x45 → SSL (8), node 0x0A |
| 14 | Cyberwave Trial → B3. The Nightmare Realm - Battle | `14.cwt_to_b3battle.20_10.m64` | 20.10 | 603 | 20.72 | Cyberwave Trial's star exit: courtyard 0x1C | level 6 fading warp 0x45 → BOWSER_3 (34), node 0x0A |

An unfinished variant of 04 is in `wip/`: `wip/castle04.ttc_to_bt.1.m64` with `wip/castle04.st`, which ends short
of the Bob-omb Temple pipe.

## Notes

- **01 and 02 come from one movie** with the B1 stage in between. That stage is not the published one; the published
  stage is in `bowser-levels/`.
- **01, 03, 05 and 06 start from a Dream Realm star exit** (hub node 0x04, the hub's centre), with the save set to that
  point of the route. Each main course's Dream Realm course (Course 1 to 4) is entered through that course's act
  select, and its star exits to hub 0x04. So a course whose last star is its Dream Realm course hands over at the
  hub's centre; the course's own stars exit beside its entrance (hub 0x1A, 0x2A, 0x3A, 0x4A), which is what the
  re-entry rows start from.
- **The routes through other levels:**
  - 07: the look-up warp into Rainbow Road, Exit Course back to the hub, through The White Abyss's warp 0x06 into
    the Dream Realm.
  - 11 and 14: Exit Course to the hub, then the hub's key door 0x00 into level 6. 11 unlocks that door, which costs
    148 frames.
  - 12: The White Abyss's warp into the Dream Realm, then a fall through its floor: the death node 0xF1 leads to
    the courtyard's pipe 0x03.
- **There is no Wing Cap → Toad movement:** the Toad star's file (`dream-realm/dr.toad.19_60.m64`) starts from a
  Vanishcap star exit, which lands on the same Dream Realm node 0x90 as Wing Cap's. Its time runs to the star dance,
  so a Wing Cap exit goes straight into the Toad star.
- **Movement 10 is that file's tail:** from the first frame of the no-exit dance, where the star's time stops, to the
  pipe, with Kieran's exit (frames 124 to 282 of this movie). Its rerecords are counted on the Toad row.
- **The first movement 10 was replaced:** ChouxZi3's Wing Cap → Mountain of Serenity is now in
  `archive/castle-movement/`. Up to the star it was the same run as the Toad file, and its exit was 9 frames slower.
- **06's state has an edited save.** The look-up warp into Rainbow Road needs 30 stars, and it counts the save file
  in use (`gCurrSaveFileNum`): file B, which had 2 (file A in the same state has 50).
  - `06.st` gives file B 30: all seven stars of Playful Palace, Bob-omb Temple, Gelato Beach and The White Abyss,
    one of Tick Tock Chaos, and the Dream Realm star it already had.
  - Mario's star count, the HUD and `prevNumStarsForDialog` are set to 30. Without the last, the save menu plays
    the star-count dialog (96 frames) and the movie desyncs.
  - Nothing else in the state changed, and the run matches the 2-star one on every frame until the warp fires.
  - Kieran finished the draft: ChouxZi3's first 430 inputs, then his.
  - The 12.97 is Kieran's improvement of the 13.10 from frame 471: the look-up warp on frame 539 instead of 543.
    The 13.10 is in `archive/castle-movement/`, with a copy of `06.st` beside it.
- **12 is a join of two drafts:** the full movement to the courtyard, then a pipe BLJ there from the courtyard's pipe
  arrival, which is 193 frames faster than the full movement's own courtyard leg. A neutral input pads it during the
  final warp's fade to its boundary. Rerecords are the two drafts' together.
- **14 enters the B3 battle through level 6's fading warp**, not the B3 stage's pipe, which `bowser-levels/`'s battle
  state comes from.
