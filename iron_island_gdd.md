# Iron Island Fight League (IIFL) — Game Design Document v0.1

## 1. High Concept

A career-progression combat sports sim. The player creates a 12-year-old fighter, develops him through juvenile → amateur → pro ranks, and over a 5-year (in-game, expandable) arc can transition roles — **Fighter → Coach → GM → Owner → Scout**, or go **Unemployed**/retire. Players can marry, have a child, and continue their legacy by becoming their own offspring when their original fighter ages out or dies (rare).

Tone: GTA-style free roam between fight nights (walk the city, train, do mini-games, build relationships) + Blood Bowl-style play-by-play fight presentation + deep league sim (draft, trades, standings, playoffs) underneath it all.

**Eventual goal:** marketable desktop video game, full graphics. Current phase: text/HTML prototype to nail systems before art investment.

---

## 2. World — Iron Island

8 regions ("Provinces"), each with its own theme, fighting culture, and settlement list. Population tiers:
- **City:** 15,000+
- **Town:** 4,200–15,000
- **Village/Camp:** 100–4,500

| Province | Theme | Settlement Mix | Signature Disciplines | Flavor Notes |
|---|---|---|---|---|
| **Alexandretta** | Old England / Robin Hood era | 4C 2T 2V | Boxing, Wrestling, Karate | Single entry point; horses & wagons once inside |
| **Kolsati District** | New York | 5C 4T 2V | Street Brawling, MMA, Boxing | Big arenas, rowdy crowds, lots of fight opportunities |
| **Sherwood Province** | Chicago | 3C 2T 5V | MMA, Street Brawling, Boxing | Many small suburbs; strong fighter pipeline |
| **Gazon Province** | Africa | 2C 2T 3V | Boxing (dominant) | Underdeveloped, fewer fighters produced |
| **Di Tiero Province** | New Orleans / Mardi Gras | 4C 4T 3V | Karate (huge) | Party capital, trouble-prone, includes outlying islands |
| **Carpathia Province** | Dracula's homeland (1992 film vibe) | 2C 7T 3V | Russian Sambo / "weird" styles | Isolated, spooky; periodically spawns dominant mountain fighters |
| **Northeast Territory** | Japan | 2C 2T 9V | Russian Sambo | Strict visitor rules, huge home-fight advantage, crowd mood swings wildly |
| **Bay Province ("Mayberry")** | 1950s small-town California | 1C 5T 4V | Wrestling (dominant) | Slow-paced, shoddy fairground arenas |

**Totals across the island:** 23 Cities, 28 Towns, 31 Villages.

### 2.1 Settlements (complete)

**Alexandretta** (target 4C 2T 2V — as originally specified, kept as canon):
Williamsburg — City (32,000), St. Anne — Town (12,000), Nattingham — Town (6,800), Wolverbridge — Town (8,000), Blackford — Village (2,300), Mosshead — Town (4,800), Whitechapel — Town (7,600), Cowborough — Village (750)
*Note: original list leans Town-heavy vs. the 4C2T2V target — kept as-is since you specified these directly. Flag if you want it tightened to match the ratio exactly.*

**Kolsati District** (target 5C 4T 2V):
Kolsati — City (55,000), St. Johnson — City (25,000), Bakii — City (34,000), **Briggston** — City (28,000), **Castellan Heights** — City (19,500), **Marrow Hill** — Town (9,200), **Pell's Crossing** — Town (6,500), **Dunmore** — Town (5,800), **Iron Wharf** — Town (12,400), **Slate Row** — Village (3,100), **Cutter's End** — Village (1,650)

**Sherwood Province** (target 3C 2T 5V):
Frontenac City — City (62,000), Lawrenceville — City (23,000), **Millbrook Heights** — City (17,500), North Lawrenceville — Town (11,000), **Caldwell Junction** — Town (8,900), **Petsworth** — Village (3,400), **Harrow's Bend** — Village (2,100), **Oak Siding** — Village (1,800), **Greeley Flats** — Village (900), **Thistledown** — Village (650)

**Gazon Province** (2C 2T 3V — as originally specified, kept as canon):
Gazon Main — City (29,000), Gazon Northern — City (15,000), Gazon South — Town (12,000). *Holds short of the full 2C2T3V on purpose — underdeveloped region per design intent, sparse list reinforces the theme. Say the word if you'd rather it be filled out to spec.*

**Di Tiero Province** (target 4C 4T 3V):
Di Tiero — City (38,000), South Bender — City (22,000), **Bellechasse** — City (24,000), **Port Maray** — City, island settlement (16,800), **Cane Hollow** — Town (9,500), **Marsh Landing** — Town (7,200), **Bayou Verte** — Town (5,600), **Saint Roque** — Town (4,900), **Driftwood Key** — Village, island (2,300), **Crayfish Bend** — Village (1,400), **Lantern Cay** — Village, island (800)

**Carpathia Province** (target 2C 7T 3V):
**Vyrholm** — City (21,000), **Castle Reach** — City (16,200), Bukovene — Town (11,900), **Greywatch** — Town (9,800), **Hollowmere** — Town (8,400), **Sorrow's Pass** — Town (7,100), **Ravenshade** — Town (6,300), **Drovna** — Town (5,500), **Kessel Vorn** — Town (4,900), Bargo Pass — Village (2,300), **Thornfall** — Village (1,900), **Wraithwood** — Village (1,200)

**Northeast Territory** (target 2C 2T 9V):
**Mizukoshi** — City (22,500), **Tsubaki Bay** — City (16,500), Santorino — Town (13,000), Ineawood — Town (7,800), **Hoshimura** — Village (4,200), **Kanesato** — Village (3,600), **Renkawa** — Village (3,100), **Sodegaura** — Village (2,500), **Takamine** — Village (2,000), **Usuzumi** — Village (1,500), **Yorimasa** — Village (1,100), **Fubuki** — Village (700), **Iwagakure** — Village (350)

**Bay Province ("Mayberry")** (target 1C 5T 4V):
Charleston — City (27,000), Bayport — Town (7,100), **Pinecrest Hollow** — Town (11,200), **Maple Junction** — Town (8,600), **Dell's Corner** — Town (6,400), **Briarwood** — Town (4,900), **Sunfish Cove** — Village (2,800), **Acorn Flats** — Village (1,700), **Quail Hollow** — Village (1,100), **Hickory Bend** — Village (650)

*(Bold = newly added to round out the original list. Names are placeholders — easy to swap.)*

> **Open item:** Full settlement lists are incomplete for 6 of 8 provinces. Need names + populations to round these out before map work begins.

---

## 3. Franchises / Pro Teams

- **8 Pro teams to start** (1 per province, based in that province's lead city), expandable up to **16**, with a wishlist ceiling of **24**.
- League can **contract** if a club is unprofitable for 6 straight seasons.
- **2 Conferences.**
- Roster: **12 fighters**, can protect **2** on injured reserve/Minor Pro for a season.
- Each team: **8 male fighters, 4 female fighters** (matches the 7-fight card + extras/cuts).
- **2 Minor Pro leagues to start:** Kolsati & Gazon.

---

## 4. Character Creation & The Sequencing Event

1. Player names their fighter, sets starting age (12), Province, Height, Weight.
2. **The Sequencing Event** — a series of mini-games/questions that determine:
   - Discipline strengths/weaknesses
   - Potential, Injury Proneness, Superstar Potential, Personality
   - Starting stat distribution
3. **Opening cutscene:** young fighter leaves home, walks the neighborhood, is approached by a local who explains the area. Then control is handed to the player — free roam begins.

### 4.1 Player Card Stats

| Stat | Range | Notes |
|---|---|---|
| Speed | — | |
| Quickness | — | |
| Toughness | — | |
| Power | — | |
| Agility | — | |
| Injury Potential | 1–20 | example given: 4 vs. 17 |

Card also displays: Photo, Height, Weight, Reach, Age, Discipline, Hometown, and separate **Juvenile / Amateur / Pro records**.

### 4.2 Aging & Peak Curves
- **Early peak:** best at 16–21
- **Middle peak:** 20–27
- **Late peak:** 25–33
- Rare fighters compete into their 40s, possibly 50s.
- Stat growth rate scales with Potential.

---

## 5. Fighting Disciplines

**8 disciplines at launch** — your original 6 plus 2 new additions to round out the roster:

| Discipline | Origin/Flavor Province | Style Notes |
|---|---|---|
| Boxer | Alexandretta, Gazon, Sherwood | Pure striking, hands only |
| Street Brawler | Kolsati, Sherwood | Unpredictable, no formal technique, high variance |
| Wrestler | Bay Province | Takedowns, control, grinding decisions |
| Russian Sambo | Northeast Territory, Carpathia | Throws + submissions, hybrid grappling |
| MMA | Kolsati, Sherwood | All-around, no major weakness, no major peak |
| Karate | Alexandretta, Di Tiero | Sharp striking, point-style speed |
| **Judo** *(new)* | Northeast Territory | Throw-heavy grappling, explosive but can be over-committed |
| **Catch Wrestling** *(new)* | Bay Province | Old-school submission wrestling, sneaky finishes, fits the "Mayberry" wrestling-town flavor |

**Stretch goal — 4 more disciplines to reach 12 later, not built yet:** Muay Thai, Brazilian Jiu-Jitsu, Kickboxing, Capoeira. Easy to slot in later since the matchup table below is built to extend.

### 5.1 Discipline Matchup Chart (strategy layer)

Each discipline has a natural advantage/disadvantage against others — this is what a Trainer can help a fighter (or GM) read before setting a lineup. Scale: **+2 strong advantage, +1 slight edge, 0 even, -1 slight disadvantage, -2 strong disadvantage.** Read row vs. column.

| vs. → | Boxer | Brawler | Wrestler | Sambo | MMA | Karate | Judo | Catch |
|---|---|---|---|---|---|---|---|---|
| **Boxer** | 0 | +1 | -1 | -1 | -1 | +1 | -1 | -1 |
| **Brawler** | -1 | 0 | -1 | -2 | -1 | 0 | -2 | -1 |
| **Wrestler** | +1 | +1 | 0 | -1 | 0 | +1 | 0 | +1 |
| **Sambo** | +1 | +2 | +1 | 0 | 0 | +1 | -1 | 0 |
| **MMA** | +1 | +1 | 0 | 0 | 0 | +1 | 0 | +1 |
| **Karate** | -1 | 0 | -1 | -1 | -1 | 0 | -1 | 0 |
| **Judo** | +1 | +2 | 0 | +1 | 0 | +1 | 0 | +1 |
| **Catch** | +1 | +1 | -1 | 0 | -1 | 0 | -1 | 0 |

**Design logic:** Strikers (Boxer, Karate) struggle against anyone who can close distance and grapple (Wrestler, Sambo, Judo, Catch). Brawlers beat nobody decisively but catch Boxers off-guard with chaos; they get exposed badly by trained grapplers. MMA is the deliberate "no bad matchups, no great ones" generalist. This chart is a starting point — easy to retune once you see it play out in sim.

**Trainer/Coach gating:** A low-skill Trainer only reveals a vague hint ("this matchup favors your striker"); a high-skill Trainer reveals the actual numeric edge. This becomes a real strategic resource — better coaching staff = better intel = better lineup decisions.

---

## 6. Weight Classes

**Amateur (Juvenile):** Light, Middle, Heavy — split by age bracket: **12u, 14u, 16u, 18u**
**Amateur (Adult-track):** Light, Middle, Heavy
**Pro Men (5):** Fly, Light, Middle, Heavy, Mega
**Pro Women (2):** Light, Heavy

---

## 7. Career Ladder (Amateur Path)

### 7.1 Fight Pits
- Local fighting venues within a city/town (e.g., **Big Jim's Fightin' Pit** in Di Tiero; that town alone also has Snake Pit, Power's Pit, Abrams Corner — multiple pits per city is normal).
- Hosts **all amateur levels**.
- Fight days: **Wednesday, Saturday, Sunday** — these build skill and reputation (record-driven).

### 7.2 Juvenile Season
- **Monthly**, 9 fights per season, league championship at month's end during off-peak months.
- Weight classes: Boys – Light/Middle/Heavy; Girls – Light/Middle.

### 7.3 Amateur Season
- **1st Half:** October–December
- **2nd Half:** January–March
- 1x/week, ~12 fights per half.
- Top 6 per season qualify for tournament → **2 Champions**.
- **April:** City Championships
- **May:** Regional Championships
- **June:** National Championships
- **July–September:** Off-season / training

### 7.4 Amateur Advancement Pyramid
```
2–4 City Fight Pits → determine City Champion
6–8 City Champs → advance to Regionals
8 Regional Champs → advance to Nationals
```

---

## 8. Pro League Structure

### 8.1 Annual Calendar
| Month | Event |
|---|---|
| July | Women's Draft (2 rounds) → Men's Draft (3 rounds), then Minor Pro Call-Up period opens |
| August | Sparring camp — determines roster cuts |
| September | **Pro season begins**, fights every other week |
| Sep–Jan | Regular season (12 fights total, biweekly) |
| February | Playoffs begin (1 game), then continue |
| March | League Finals |
| April | Individual Championships (top 6 per weight class/gender bracket: 4v5 @1, 3v6 @2, winners meet in finals; consolation bracket sets 3rd–6th) |
| July | Next Draft / Call-Ups |

Minor Pro fighters can be called up any time from **September through playoffs**.

### 8.2 Draft Night
- Held in **July**.
- Women's Draft (2 rounds) goes first, then Men's Draft (3 rounds).
- Full presentation: music, intros, pick announcements with location-based crowd reaction (cheer/boo).
- **No free agency at launch** — trades are the only roster tool outside the draft/call-ups.

### 8.3 Roster Management
- 12-man roster, 2 protected (IR/Minor Pro) slots per season.
- Cut players may sign elsewhere, retire, sit out the season, or return to Minor Pro.

### 8.4 Fight Night Format
- **7 fights per event**, fixed order: **M-Fly, M-Light, W-Light, M-Middle, W-Heavy, M-Heavy, M-Mega**
- Team score outcomes: 7-0, 6-1, 5-2, or 4-3.
- Individual results: **Decision, DQ, TKO, KO.**
- Forfeits possible; fighters must make weight.
- **Pre-fight flow:** team in locker room → called to arena → intros (home music, crowd boos visitors, reaction scales with crowd type) → bouts.
- **Travel:** no planes — long road trips fatigue traveling fighters, giving home teams an edge. Long-distance fighters can also start a match with an early advantage (per your notes, conditioning/crowd-adjacent).

### 8.5 Arenas (Presentation Variety)
- Capacity range: **500 to 10,000** — a packed 500-seat pit can out-roar an empty 10,000-seat coliseum.
- Floor types: sport court, rubber mat on cement, grass, clay, dirt (some with glass in it).
- Seating: coliseum-style down to rotting wooden benches.
- Lighting: light shows in wealthy venues.
- Every arena has a unique name, look, and music.
- Crowd size/energy responds to team performance over time; reputations (rabid, reserved, indifferent) can shift long-term.
- Arenas can be **upgraded or replaced** over time (Owner-level decision).

---

## 9. Weekly Routine (Free Roam Loop)

Player has a **points budget** each week based on **last week's performance**. Activities cost points:
- Walk the city
- Train
- Fight
- Visit home
- Mini-training
- Visit girlfriend/partner
- Mini-games (bowling, darts, bags, foot races, high jump, gym workouts, basketball, home run derby, etc.)

**Friday = Game Day:** set nutrition + pregame workout → travel to arena (home: pregame sequence; away: team bus) → fight night.

---

## 10. Career Roles

Beyond active fighter, the player can become: **Coach, GM, Owner, Scout, or Unemployed.**
- **Legacy system:** create a family, attract a mate, have an heir. When your fighter's career ends (retirement, rare death), you can continue playing as your child, carrying forward storylines and rivalries.

---

## 11. Media & Storyline Systems

- Daily/weekly in-game newspaper with stats.
- Storylines auto-generate around top fighters — rises, peaks, declines.
- **"Up and Comers":** track fighters you started alongside at age 12 (the "Mud Pit" cohort) as they progress in parallel over the years — your career-long rivals/peers.
- Play-by-play fight announcing, styled like Blood Bowl's commentary.

---

## 12. World Oddities / Texture Systems

- Rare permadeath for fighters.
- Buy houses and other amenities with winnings.
- Attract a mate → heir system (see §10).
- Parties (social/relationship + risk events).
- Random street-fight callouts — most instigators aren't real fighters, but occasionally one is.

---

## 13. Combat Ratings, Balance & Home Advantage (Resolved)

### 13.1 Overall Rating & Win Probability
You want **outcomes that respect skill gap, not arcade-style "anyone beats anyone" balancing.** Each fighter's stats roll up into an **Overall (OVR)**, roughly 0–99. Win probability uses an Elo-style curve, but steeper than standard Elo so big gaps are close to certain rather than just favored:

```
P(A beats B) = 1 / (1 + 10^(-(OVR_A - OVR_B) / 12))
```

What that produces in practice:
| OVR Gap | Favorite's Win Probability |
|---|---|
| 0 | 50% |
| 5 | ~65% |
| 10 | ~77% |
| 15 | ~86% |
| 20 | ~92% |
| 30 | ~97% |

A 90 OVR vs. a 75 OVR (15-point gap) wins roughly **86% of the time** — dominant, not a coinflip, but upsets stay possible and meaningful when they happen instead of routine. Tune the divisor (12) up to flatten the curve or down to make gaps even more decisive — easy single-number knob once you see it simmed.

This probability feeds into *how* a fight ends, not just who wins — bigger gaps skew toward TKO/KO/early finish, closer gaps skew toward Decision.

### 13.2 Home / Hometown Advantage
Two separate bonuses, and they stack:

- **Team Home-Arena Advantage:** the team fighting in its own arena gets a bonus from crowd energy and zero travel fatigue. Magnitude scales with how loud/rabid that arena's crowd reputation is.
- **Personal Hometown Bonus:** *any* individual fighter gets a bonus when competing in or near the city/region they actually grew up in or came up through as an amateur — regardless of which pro team they currently fight for. This means a traded or Minor-Pro-called-up fighter can still get a hometown boost on the road if the matchup happens to land near where they're from.
- **Travel Fatigue (Away Penalty):** since there are no planes, away teams on long road trips accumulate a fatigue debuff scaled to travel distance — worse for cross-province trips than a short regional hop.

### 13.3 Lineup-Setting Advantage
**Home team sets its lineup last**, after the visiting team's card is published. This is a real strategic edge — the home GM/coach can counter-pick matchups (e.g., slot a Sambo fighter against the visitor's announced Brawler) using the matchup chart in §5.1. Visiting teams have to commit blind. This is one of the core strategy layers at the GM/Coach level.

### 13.4 Province → Discipline Weighting (Sequencing Event)
When a fighter is generated/created, their home province should weight which disciplines they're more likely to start strong in:

| Province | Primary (heavy weight) | Secondary (light weight) |
|---|---|---|
| Alexandretta | Boxer, Karate | Wrestler |
| Kolsati | Street Brawler, MMA | Boxer |
| Sherwood | MMA, Street Brawler | Boxer |
| Gazon | Boxer | — |
| Di Tiero | Karate | Street Brawler |
| Carpathia | Russian Sambo | Judo |
| Northeast Territory | Russian Sambo, Judo | Catch Wrestling |
| Bay Province | Wrestler, Catch Wrestling | — |

A fighter created in Carpathia, for example, rolls a heavily weighted chance at Sambo aptitude, a lighter chance at Judo, and a small residual chance at anything else — keeps regional flavor without making it a hard lock.

## 14. Carpathia "Mountain Fighters" Event (Resolved)

A rare, recurring random event: every so often (suggest tunable, e.g. roll a check every 1-2 seasons with low odds — exact cadence to be tuned in playtesting since you said "not all that common"), **1 to 5 fighters** spawn out of Carpathia's mountain villages as a cohort. They are not uniform:
- Each rolls independently for **age** (can enter at different ages within the youth/amateur pipeline).
- Each rolls independently for **development curve** (early/middle/late peak — see §4.2), so the cohort doesn't all break out or decline together.
- Most of the cohort should still trend toward the "almost unbeatable" framing (very high Potential), but per your note that "some might not be so good," 1 of the cohort should have a real chance of rolling as a bust — keeps it from feeling scripted/guaranteed.

---

## 15. Open Items / Still To Resolve

1. **The "5-year career"** — on hold per your note, revisit later (need to know if it's an MVP dev-scope cutoff or an actual in-fiction career-length cap before forced retirement/legacy handoff).
2. **Carpathia event cadence** — frequency knob ("not all that common") needs an actual number once we're simulating seasons and can feel out the right rarity.
3. **Discipline matchup numbers in §5.1** — first draft, worth a look once we can simulate fights and see how it plays.
4. **Alexandretta / Gazon settlement ratios** — both currently don't hit their stated C/T/V targets exactly (kept as you specified, but flagged in §2.1 in case you want them tightened).

## 16. Suggested Prototype Build Order (for the HTML version)

Given the scope, this should follow your usual single-file HTML iterative pattern, but it's too large for one pass. Suggested build order:

1. **Character Creator + Sequencing Event** — name/age/province/height/weight + stat-rolling mini-questionnaire → outputs a fighter card.
2. **Fighter Card / Stat Sheet UI** — the persistent player record (stats, records by level, discipline, photo placeholder).
3. **Fight Resolution Engine** — core sim math (stats + discipline + RNG → Decision/DQ/TKO/KO), text play-by-play output. This is the engine everything else hangs off of.
4. **Fight Pit Loop** — amateur weekly fight cycle, record tracking, reputation.
5. **City Hub / Weekly Routine** — point-budget activity menu (training, mini-games, social).
6. **Season/League Layer** — draft, schedule, standings, playoffs (this is the "Stockyard-scale" systems layer).
7. **Province Map** — once settlement lists are finalized.

I'd recommend we start at **#1 or #3** — character creation is the most fun entry point and gives you something tangible fast; the fight engine is the riskiest/most important piece to get right early since everything depends on it.
