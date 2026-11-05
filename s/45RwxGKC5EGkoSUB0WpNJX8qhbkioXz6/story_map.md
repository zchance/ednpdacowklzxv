# Evelyn and the TimeBand: The Golden Spike (v2)

Reader: Evelyn, age 5  
Status: v2 draft for parent review (Nov 5, 2026): punchier rewrite, riskier branches, new scenes s12 Jupiter Rolls In and s23 The Wire Wagon, new ending e_too_soon. No recorded narration yet (browser voice / text-only).

## Premise

Dr. Ada Finch is an inventor at the museum who buys honey from your mom, a beekeeper. Your Apollo 11 recording now plays at the museum every day. On May 10, 1869, the first railroad across America was finished at Promontory Summit, Utah Territory. The museum has photos of that day, but no sound: nobody could record sound until Edison's phonograph in 1877. Dr. Finch's briefing (a countdown, not a lecture): "Your mission is to record the moment the railroad was finished: the last spike, and the telegraphed word DONE." Mom says many of your great-great-grandparents walked to Utah as Latter-day Saint pioneers, some pulling handcarts, so a side trip to an 1856 handcart company is offered, at the cost of a charge. TimeBand rules (same band as the Moon trip, worn on the left wrist): (1) Three charges: each trip into the past uses one; the trip home is free (backup power); a trip tapped at 0 charges sends you home (Out of Charges). (2) Safety rule: watch and record, but never change what happened; if you touch, move, or say something that could change history, the band brings you home and locks. It also pulls you home from danger. (3) Record: press the red button and hold still; when it saves a big moment it beeps twice and brings you home. Let go too soon and it stops. (4) Trip clock: the band can hold you in the past for one hour per trip; when the clock runs out, it brings you home. (5) Blend in: Dr. Finch brings 1869-style clothes (calico dress, apron, bonnet, boots) so nobody notices you. v2 design: what you learn on one trip unlocks better viewpoints on another (the code from Ten-Mile Day, the old grade from March, the crew from the Ten-Mile finish, the handcart pioneers in Salt Lake City), and charges are tight enough that you cannot have everything in one play-through.

## Tracked items and flags

| Id | Type | Starts | What it does |
|---|---|---|---|
| `charges` | counter | 3 | **TimeBand charges.** Each trip costs 1. Home is free. A trip tapped at 0 goes to Out of Charges. Shown as 3 dots. Seeing all of Ten-Mile Day costs 2, so the handcart trip + full Ten-Mile Day leaves nothing for May 10. |
| `walked_trail` | flag | False | **Walked with the handcart company.** Set on arrival at s03 (1856 trip, 1 charge). Unlocks 'Find the handcart pioneers' in Salt Lake City (s26 -> s27) and adds lines at good endings. |
| `saw_grades` | flag | False | **Saw the two grades (Latter-day Saint crews).** Set on arrival at s06 (March trip, 1 charge). UNLOCKS 'Climb the old grade' at the back of the crowd (s29 -> s21): one of two ways to reach the telegraph-table ending. Adds lines at band/Salt Lake/telegraph endings. |
| `knows_code` | flag | False | **Learned the dot-dash code.** Set on arrival at s23, the wire wagon on Ten-Mile Day (no longer free on the wire map). UNLOCKS 'Stay and read the clicks' at the telegraph table (s20 -> s21): the other way to the telegraph-table ending. Adds lines in Washington and at DONE endings. |
| `ten_mile` | flag | False | **Saw the Ten-Mile Day finish.** Set on arrival at s10 (sunset, a second Ten-Mile charge). UNLOCKS 'Stand with the Chinese crew' at the last rail (s17 -> s18 -> g_crew). Adds lines at endings. |
| `clock_min` | counter | 60 | **Trip clock (minutes).** Shown in past scenes. Choices that wait for hours (camp nap, waiting all of Ten-Mile Day, landing at 11 a.m. and staying) lead to Time's Up. |
| `via` | note | None | **Route note.** Picks the variant line for scenes/endings reached from more than one place (s21, safety, time_up, steam, too_soon, salt_lake). |
| `recording_saved` | flag | False | **Mission done.** Set at every GOOD ending. The band beeps twice and saves the recording for the museum. |

Any choice marked **(trip, -1 charge)** costs one charge. With 0 charges, it goes to **Out of Charges**.
With three charges, one play-through can visit at most three of: the handcart trail, the grades, Ten-Mile Day (a 2nd charge to see the finish), Promontory Summit (landing at eleven costs a 2nd charge to reach noon), Salt Lake City, Washington. Every path has to give something up.

**Carried-item stakes (v2):** the telegraph-table ending (g_telegraph) needs `knows_code` (wire wagon, Ten-Mile Day) OR `saw_grades` (March trip); the Chinese-crew ending needs `ten_mile` (Ten-Mile finish, 2 charges); the handcart pioneers in Salt Lake City need `walked_trail` (1856 trip).

## Scenes

### s01 · p.1 · The Second Mission
*Your kitchen, Saturday morning*

Countdown briefing. Dr. Finch snaps the TimeBand on (left wrist, three green dots). May 10, 1869, Promontory Summit: photos exist, no sound. Mission line (approved): "Your mission is to record the moment the railroad was finished: the last spike, and the telegraphed word DONE." Rules in one breath: three charges, home is free, one hour per trip, don't change anything, hold still to record. 1869 clothes. Mom: ancestors pulled handcarts. The handcart trip costs a charge: 'Spend them wisely.'

**Science:** Sound is air shaking. In 1869 no machine could save it.

**Choices:**
- If you want to visit a handcart company on the trail in 1856, tap 'Visit the handcart trail.' → **s02 The Handcart Trail** *(trip, -1 charge)*
- If you are ready to pick a day in 1869, tap 'Open the mission map.' → **s05 The Mission Map**

### s02 · p.2 · The Handcart Trail
*Beside the Platte River, Nebraska Territory - August 1856, late afternoon* · trip clock 60 min

You land by the Platte beside the first handcart company (Captain Edmund Ellsworth), Latter-day Saints walking to Salt Lake City. Four-year-old Annie walks beside the captain for the promise of bread and butter. One wheel squeaks.

**Science:** Wheels roll instead of drag.

**Choices:**
- If you climb up and ride in a handcart, tap 'Ride in a cart.' → **e_safety_return Safety Return** *(sets via=cart)*
- If you walk at the side of the trail near Annie, tap 'Walk with Annie.' → **s03 The Squeaky Wheel**

### s03 · p.3 · The Squeaky Wheel
*Camp by the Platte River - before sunset* · trip clock 40 min

Camp. The squeaky axle is hot and worn; a man wraps it in tin. Fifteen miles a day, all summer; a train will do it in days. The hammer is right by your hand.

**Science:** Friction: rubbing makes heat and wear. Smooth metal rubs less than rough wood.

**On arrival:** set walked_trail=True

**Choices:**
- If you pick up the hammer and fix the wheel yourself, tap 'Hammer it yourself.' → **e_safety_return Safety Return** *(sets via=wheel)*
- If you stay and watch the camp make supper, tap 'Stay for supper.' → **s04 Songs at Camp**

### s04 · p.4 · Songs at Camp
*Camp by the Platte River - sunset* · trip clock 10 min

Buffalo-chip fires. The camp sings the handcart song. Annie claps. The fire is warm, your eyes are heavy, and the clock says 10 minutes.

**Science:** Fire turns stored energy in fuel into heat and light.

**Choices:**
- If you curl up by the warm fire for a little nap, tap 'Sleep by the fire.' → **e_time_up Time's Up** *(sets via=camp)*
- If you go home and open the mission map, tap 'Go home to the map.' (Going home is free.) → **s05 The Mission Map**

### s05 · p.5 · The Mission Map
*The TimeBand screen, in your kitchen*

A glowing line across America: Central Pacific from California, Union Pacific from Nebraska. Four stops: March 1869 (two grades and blasting), April 28 (Ten-Mile Day, a record race), May 8 (the date on the golden spike), May 10 (free place picker). Wire map is free. 'What you learn on one trip can help you on another.'

**Science:** A map is a small picture of a big place.

**Choices:**
- If you want to see the workers building the grade in March 1869, tap 'The two grades.' → **s06 Two Grades** *(trip, -1 charge)*
- If you want to see the record race, April 28, 1869, tap 'Ten-Mile Day.' → **s08 Ten-Mile Day** *(trip, -1 charge)*
- If you want to go on May 8, 1869, the date on the golden spike, tap 'May 8.' → **e_wrong_day The Wrong Day** *(trip, -1 charge)*
- If you want to pick a place for May 10, 1869, tap 'May 10.' (Picking is free.) → **s11 Two Promontories**
- If you want to look at the telegraph wires, tap 'Look at the wires.' (Looking is free.) → **s25 The Wire Map**

### s06 · p.6 · Two Grades
*Promontory Mountains, Utah Territory - late March 1869* · trip clock 60 min

Latter-day Saint farm crews build grade under the contract Brigham Young signed. Two grades run side by side because both companies are paid by the mile. Up the hill a fuse is lit: 'BLAST! STAND CLEAR!' Men run.

**Science:** A grade is a long ramp of dirt and rock that holds the track.

**On arrival:** set saw_grades=True

**Choices:**
- If you run up the hill to get a close look at the fuse, tap 'Run up to see the fuse.' → **e_blast Stand Clear!**
- If you dive behind the wagon and cover your ears, tap 'Dive behind the wagon.' → **s07 The Big Fill**

### s07 · p.7 · The Big Fill
*Spring Creek ravine, Promontory Mountains - late March 1869* · trip clock 45 min

BOOM: the ground jumps, pebbles rattle (black powder makes a huge push of gas). Then the Big Fill, built by Benson, Farr and West, and the UP's Big Trestle beside it. Iron wheels slip on steep hills, so the track stays almost flat.

**Science:** Gas pressure breaks rock. Iron on iron has little friction, so track must be nearly flat.

**Choices:**
- If you jump on an empty dump cart for a ride, tap 'Ride the dump cart.' → **e_safety_return Safety Return** *(sets via=dumpcart)*
- If you jump ahead to April 28, Ten-Mile Day, tap 'Go to Ten-Mile Day.' → **s08 Ten-Mile Day** *(trip, -1 charge)*
- If you want to pick a place for May 10, tap 'Open May 10.' (Picking is free.) → **s11 Two Promontories**

### s08 · p.8 · Ten-Mile Day
*Near Victory camp, Utah Territory - April 28, 1869, 7:15 a.m.* · trip clock 60 min

Crocker's bet: ten miles in ONE day. Whistle. GO! Rails CLANG down, the ground shakes, Chinese crews spike (three blows). Rails get small gaps for heat. A wagon with a telegraph key rolls right behind the crews.

**Science:** Heat makes iron grow a tiny bit, so rails need small gaps.

**Choices:**
- If you push two rails tight together to close the gap, tap 'Push the rails together.' → **e_safety_return Safety Return** *(sets via=gap)*
- If you run along with the rail crew, tap 'Race with the rail crew.' → **s09 Iron and Tea**
- If you run after the wagon with the telegraph key, tap 'Follow the wire wagon.' → **s23 The Wire Wagon**

### s23 · p.9 · The Wire Wagon
*Ten-Mile Day - about 7:45 a.m.* · trip clock 50 min

NEW in v2. The telegraph man in the wagon sends news of the race and teaches D-O-N-E in American Morse (dash dot dot / dot dot / dash dot / dot). Evelyn 'tucks it away for later.' He jokingly offers her a turn on the key.

**Science:** Telegraph code: short clicks are dots, long clicks are dashes.

**On arrival:** set knows_code=True

**Choices:**
- If you take a turn and tap the key, tap 'Take a turn on the key.' → **e_safety_return Safety Return** *(sets via=wirekey)*
- If you say no thank you and run back to the race, tap 'Run back to the race.' → **s09 Iron and Tea**
- If you jump ahead to tonight, when the race ends, tap 'Jump to the finish.' → **s10 Ten Miles!** *(trip, -1 charge)*

### s09 · p.10 · Iron and Tea
*Ten-Mile Day - about 8:30 a.m.* · trip clock 35 min

The track grows as fast as you walk; the ground thumps like a heartbeat. Rails weigh as much as three grown-ups. Tea from boiled water. 'The finish is twelve hours away. Your clock has thirty-five minutes.'

**Science:** Boiling water kills many germs.

**Choices:**
- If you stay here and wait for the end of the race, tap 'Wait for the finish.' → **e_time_up Time's Up** *(sets via=tenmile)*
- If you jump ahead to tonight, when the race ends, tap 'Jump to the finish.' → **s10 Ten Miles!** *(trip, -1 charge)*
- If you want to pick a place for May 10, tap 'Open May 10.' (Picking is free.) → **s11 Two Promontories**

### s10 · p.11 · Ten Miles!
*Ten-Mile Day - about 6:30 p.m.* · trip clock 60 min

'Nine miles!' The crews push faster; then TEN MILES AND FIFTY-SIX FEET. Hats fly; the record still stands. Jim Campbell races an engine over the new track: not one wobble. 'Remember these faces.'

**Science:** A heavy hammer moving fast hits hard. Three blows drive a spike.

**On arrival:** set ten_mile=True

**Choices:**
- If you want to pick a place for May 10, tap 'Open May 10.' (Picking is free.) → **s11 Two Promontories**
- If you want to look at the telegraph wires, tap 'Look at the wires.' (Looking is free.) → **s25 The Wire Map**

### s11 · p.12 · Two Promontories
*The TimeBand screen - May 10, 1869*

Free place picker. Promontory Point (tip, by the lake) vs Promontory Summit (top of the climb). Two times for the Summit: eleven o'clock, when Jupiter rolls in, or noon. 'You only get one hour.'

**Science:** A summit is the top of a climb.

**Choices:**
- If you go to Promontory Point, at the tip of the land by the lake, tap 'Promontory Point.' → **e_wrong_place The Wrong Promontory** *(trip, -1 charge)*
- If you go to Promontory Summit at eleven o'clock, to see Jupiter roll in, tap 'The Summit at eleven.' → **s12 Jupiter Rolls In** *(trip, -1 charge)*
- If you go to Promontory Summit at noon, tap 'The Summit at noon.' → **s13 Promontory Summit** *(trip, -1 charge)*

### s12 · p.13 · Jupiter Rolls In
*Promontory Summit - May 10, 1869, a few minutes after 11 a.m.* · trip clock 60 min

NEW in v2 (replaces Sunrise). WHOOOO: Jupiter steams in with Stanford's car; No. 119 waits across the gap. Exciting, but the spike is nearly two hours away and the clock has one.

**Choices:**
- If you stay right here and wait for the spike, tap 'Stay for the spike.' → **e_time_up Time's Up** *(sets via=jupiter)*
- If you run right up to Jupiter as it hisses to a stop, tap 'Run up to Jupiter.' → **e_steam Lost in the Steam** *(sets via=arrive)*
- If you jump ahead to noon, tap 'Jump ahead to noon.' → **s13 Promontory Summit** *(trip, -1 charge)*

### s13 · p.14 · Promontory Summit
*Promontory Summit - May 10, 1869, about noon* · trip clock 60 min

Jupiter (funnel stack) and No. 119 (straight stack) face each other across the gap. Hundreds of people, two bands (army; Tenth Ward Band from Salt Lake City). Brigham Young is in southern Utah; Bishop John Sharp and Mayor Lorin Farr came. A telegraph table, a big camera. 'The spike goes in at 12:47. Where will you be?'

**Choices:**
- If you go see the two engines, tap 'Go see the engines.' → **s14 Two Engines**
- If you go to the gap where the last rails go down, tap 'Go to the last rail.' → **s17 The Last Rail**
- If you go to the man with the big camera, tap 'Go to the photographer.' → **s22 The Photographer**
- If you stay at the back of the crowd, tap 'Stay at the back.' → **s29 The Back of the Crowd**

### s14 · p.15 · Two Engines
*Promontory Summit - about 12:10 p.m.* · trip clock 50 min

HUGE, hissing, ticking engines. A steam engine is a teakettle on wheels. Wood (Jupiter) vs coal (No. 119). Pipes by Jupiter's front wheels spit steam.

**Science:** Steam takes up much more room than water, so it pushes hard.

**Choices:**
- If you stand by Jupiter's big front wheels to record, tap 'Stand by the front wheels.' → **e_steam Lost in the Steam** *(sets via=wheels)*
- If you climb up into Jupiter's cab, tap 'Climb into Jupiter.' → **s15 Jupiter's Cab**
- If you climb up into No. 119's cab, tap 'Climb into No. 119.' → **s16 No. 119's Cab**

### s15 · p.16 · Jupiter's Cab
*Inside Jupiter's cab - about 12:20 p.m.* · trip clock 40 min

Fire roars; the gauge needle points high; the whistle cord swings overhead. You can see the gap and the telegraph pole.

**Science:** A pressure gauge shows how hard the steam is pushing.

**Choices:**
- If you pull the whistle cord, tap 'Pull the whistle cord.' → **e_safety_return Safety Return** *(sets via=whistle)*
- If you rest your arm on the cab window and record from here, tap 'Record from the cab.' → **g_jupiter From Jupiter's Cab**
- If you climb down and go to the last rail, tap 'Go to the last rail.' → **s17 The Last Rail**

### s16 · p.17 · No. 119's Cab
*Inside No. 119's cab - about 12:20 p.m.* · trip clock 40 min

CLANG: the firebox blasts orange heat. No. 119 came to the rescue after a flood hurt a bridge in Weber Canyon. A lump of coal lies by your boot.

**Science:** Coal packs more heat into a small pile than wood.

**Choices:**
- If you throw a lump of coal into the fire, tap 'Throw in some coal.' → **e_safety_return Safety Return** *(sets via=coal)*
- If you hold still in the cab and record from here, tap 'Record from the cab.' → **g_119 From No. 119's Cab**
- If you climb down and go to the photographer, tap 'Go to the photographer.' → **s22 The Photographer**

### s17 · p.18 · The Last Rail
*At the gap - about 12:20 p.m.* · trip clock 35 min

'Make way!' Irish UP crew and Chinese CP crew drop the last rails: CLANG, dust. Laurel tie, silver plate, drilled holes. Gold is soft, so the golden spike gets a tap; the wired iron spike and wired hammer do the real job. The golden spike glints right by your hand.

**Science:** Gold is soft. A hard hit would bend it.

**Choices:**
- If you reach out and touch the golden spike, tap 'Touch the golden spike.' → **e_safety_return Safety Return** *(sets via=spike)*
- If you saw Ten-Mile Day end, you know these workers. Tap 'Stand with the Chinese crew.' → **s18 The Chinese Crew** *(needs ten_mile)*
- If you stand with the Union Pacific's Irish crew, tap 'Stand with the Irish crew.' → **s19 The Irish Crew**
- If you go to the telegraph table, tap 'Go to the telegraph table.' → **s20 The Telegraph Table**

### s18 · p.19 · The Chinese Crew
*Beside the last rail* · trip clock 30 min

You know these faces from Ten-Mile Day. Thousands of Chinese workers built the Central Pacific. The speeches and most photos will leave them out.

**Choices:**
- If you stand still with the crew and record, tap 'Record with the crew.' → **g_crew The Crew Who Laid It**
- If you go to the telegraph table, tap 'Go to the telegraph table.' → **s20 The Telegraph Table**

### s19 · p.20 · The Irish Crew
*Beside the last rail* · trip clock 30 min

The Union Pacific crew under foreman Guilford. 'Long handle, fast head. Fast head, hard hit.' A spare maul almost as tall as you.

**Science:** A long handle makes the hammer head move fast (a lever).

**Choices:**
- If you pick up the spare maul and swing it, tap 'Swing the spare maul.' → **e_safety_return Safety Return** *(sets via=maul)*
- If you stand still with the crew and record, tap 'Record with the crew.' → **g_irish Mauls Up!**

### s20 · p.21 · The Telegraph Table
*By the telegraph pole - about 12:27 p.m.* · trip clock 25 min

Shilling taps 'Almost ready. Hats off. Prayer is being offered.' The whole country is listening. WITHOUT the code the clicks are a blur and a soldier waves kids back: you cannot stay. WITH the code you can read every letter.

**Science:** Telegraph: electricity in a wire carries a signal almost instantly.

**Choices:**
- If you reach over and tap the telegraph key, tap 'Tap the key.' → **e_safety_return Safety Return** *(sets via=key)*
- If you learned the code, stay close and read the clicks. Tap 'Stay and read the clicks.' → **s21 Hats Off** *(needs knows_code; sets via=code)*
- If you want to hear the news arrive somewhere far away, tap 'Look at the wires.' (Looking is free.) → **s25 The Wire Map**

### s21 · p.22 · Hats Off
*By the telegraph table - about 12:45 p.m.* · trip clock 15 min

Reached only with the code (s20) or from the old grade (s29). Prayer, speeches, special spikes. 'The signal will be three dots for the start of the blows.' Stanford lifts the hammer. 'Three dots are coming. Then the blows. Then DONE.'

**Choices:**
- If you press record and hold the band still until the very end, tap 'Record the clicks.' → **g_telegraph D-O-N-E**
- If you stop recording as soon as you hear three dots, tap 'Stop at three dots.' → **e_too_soon Too Soon!** *(sets via=table)*
- If you jump to Washington, D.C., to hear the same clicks arrive there, tap 'Jump to Washington.' → **s28 Washington, D.C.** *(trip, -1 charge)*

### s22 · p.23 · The Photographer
*Near the engines - about 12:15 p.m.* · trip clock 45 min

Andrew J. Russell under his black cloth; wet glass plates; the lens stays open for seconds so anything moving blurs. 'After the spike, the engines come together. That's my picture.' You are standing right in front of his lens.

**Science:** A camera collects light. Dim light needs more time, so moving things blur.

**Choices:**
- If you run in front of the camera and wave, tap 'Run in front and wave.' → **e_in_photo In the Picture**
- If you stand behind the camera and record, tap 'Stand behind the camera.' → **g_camera Hold Still!**
- If you follow the music to the band, tap 'Go to the band.' → **s24 The Tenth Ward Band**

### s24 · p.24 · The Tenth Ward Band
*Near the crowd* · trip clock 35 min

The Tenth Ward Band from Salt Lake City (a ward is a Latter-day Saint congregation) in new uniforms. How a horn makes sound. Charles R. Savage, the Latter-day Saint photographer from Salt Lake City, sets up nearby (folded in from the old s23). The drum sticks lie right on top.

**Science:** Sound is shaking air. A longer tube makes a lower note.

**Choices:**
- If you pick up the sticks and play the drum, tap 'Play the drum.' → **e_safety_return Safety Return** *(sets via=drum)*
- If you stand by the band and record, tap 'Record with the band.' → **g_band Music at Promontory**
- If you jump to Salt Lake City, where the band came from, tap 'Go to Salt Lake City.' → **s26 Salt Lake City** *(trip, -1 charge)*

### s25 · p.25 · The Wire Map
*The TimeBand screen*

The telegraph race: clicks hit every city at once. Sun time: 12:47 in Utah is 2:47 in Washington (time zones come in 1883). The code is NOT given here any more; without it Dr. Finch hints 'Somebody on Ten-Mile Day could teach you.'

**Science:** Sun time: the sun reaches the East first.

**Choices:**
- If you go to Salt Lake City, about 90 miles from Promontory, tap 'Salt Lake City.' → **s26 Salt Lake City** *(trip, -1 charge)*
- If you go to Washington when its clocks say 12:47, tap 'Washington at 12:47.' → **e_too_early Too Early in Washington** *(trip, -1 charge)*
- If you go to Washington when its clocks say 2:47, tap 'Washington at 2:47.' → **s28 Washington, D.C.** *(trip, -1 charge)*

### s26 · p.26 · Salt Lake City
*Salt Lake City, Utah Territory - May 10, 1869, just after noon* · trip clock 60 min

Flags, bands, cannons ready on Arsenal Hill. No railroad yet; they'll build their own to Ogden by January. The new Tabernacle. Everyone watches the telegraph office.

**Choices:**
- If you wait on the street for the signal, tap 'Wait for the signal.' → **g_salt_lake Salt Lake City Hears**
- If you walked with the handcart company, look for people who walked here too. Tap 'Find the handcart pioneers.' → **s27 People Who Walked** *(needs walked_trail)*
- If you go to the telegraph office, tap 'Go to the telegraph office.' → **s30 The Telegraph Office**

### s27 · p.27 · People Who Walked
*A street corner in Salt Lake City* · trip clock 50 min

An old woman who pulled a handcart in 1856 tells her grandson it took all summer. Annie would be seventeen. You want to tell her you walked too.

**Choices:**
- If you tell her you walked with a handcart company too, tap 'Tell her you walked too.' → **e_safety_return Safety Return** *(sets via=tell)*
- If you stand by her and record, tap 'Record with the crowd.' → **g_salt_lake Salt Lake City Hears** *(sets via=handcart)*

### s28 · p.28 · Washington, D.C.
*Western Union office, Washington, D.C. - 2:40 p.m. (Washington clocks)* · trip clock 60 min

Mr. Tinker's bell rings with every click. 'We have got done praying...' Chicago: 'All are ready in the East.' 'The signal will be three dots for the start of the blows.' The bell is right by your hand.

**Science:** A bell-sounder: electricity pulls a little hammer to ring a bell.

**Choices:**
- If you ring the bell yourself to hurry things up, tap 'Ring the bell yourself.' → **e_safety_return Safety Return** *(sets via=bell)*
- If you stop recording as soon as the bell rings three times, tap 'Stop at three dings.' → **e_too_soon Too Soon!** *(sets via=bell)*
- If you hold still by the bell and record until the very end, tap 'Record the bell.' → **g_washington Washington Hears**

### s29 · p.29 · The Back of the Crowd
*Promontory Summit - about 12:20 p.m.* · trip clock 40 min

Coats, hats, elbows. Sound gets quieter with distance. A far hill would show everything. IF you saw the grades in March, you spot the extra grade running right past the track: close and high.

**Science:** Sound spreads out as it travels, so it gets quieter far away.

**Choices:**
- If you climb the far hill to see everything, tap 'Climb the far hill.' → **e_too_far Too Far Away**
- If you saw the grades in March, climb the old grade by the track. Tap 'Climb the old grade.' → **s21 Hats Off** *(needs saw_grades; sets via=grade)*
- If you say 'excuse me' and squeeze to the front by the telegraph table, tap 'Squeeze to the front.' → **s20 The Telegraph Table**
- If you follow the sound of the band, tap 'Follow the music.' → **s24 The Tenth Ward Band**

### s30 · p.30 · The Telegraph Office
*Telegraph office, Salt Lake City* · trip clock 55 min

A young woman operator on the Deseret Telegraph (built by Latter-day Saints) listens to the sounder, pencil ready.

**Science:** A telegraph sounder clicks when electricity pulls its little arm.

**Choices:**
- If you tap the telegraph key while she listens, tap 'Tap the key.' → **e_safety_return Safety Return** *(sets via=key2)*
- If you stand quietly by her desk and record, tap 'Record with her.' → **g_deseret The Operator**

## Endings

Every ending has **Start over** and **Back to my last choice**. Every GOOD ending sets `recording_saved` and is followed by a **You were really there** page of real 1869 photos.

### g_telegraph · p.31 · GOOD: D-O-N-E · viewpoint: At the telegraph table with W. N. Shilling (needs the code OR the old grade)

Stanford misses and hits the tie; Durant misses. Three dots. CLANG, CLANG, CLANG. At 12:47 Shilling sends D-O-N-E. You held on through the dots and recorded the clicks and the roar.

### g_jupiter · p.32 · GOOD: From Jupiter's Cab · viewpoint: Central Pacific engine Jupiter

Whistle duel (WHOOOO / WHOO-WHOO), then the engines creep nose to nose and the engineers christen each other's engine.

### g_119 · p.33 · GOOD: From No. 119's Cab · viewpoint: Union Pacific engine No. 119

Whistles and cheers from No. 119, then it rolls across the joined rails, the first engine to cross, before Jupiter.

### g_crew · p.34 · GOOD: The Crew Who Laid It · viewpoint: The Central Pacific's Chinese track crew (needs the Ten-Mile finish)

You record with the crew who laid the last rail. Afterward Strobridge invites them to dinner, and the guests stand and cheer them.

### g_irish · p.35 · GOOD: Mauls Up! · viewpoint: The Union Pacific's Irish track crew

The crew that laid track from Nebraska throws up mauls and hats at DONE. 1,086 miles from Omaha, 690 from Sacramento.

### g_camera · p.36 · GOOD: Hold Still! · viewpoint: Behind A. J. Russell's camera

DONE, then the engines nose to nose, Montague and Dodge shake hands, and 'HOLD STILL!': one, two, three. The champagne photo is made.

### g_band · p.37 · GOOD: Music at Promontory · viewpoint: With the Tenth Ward Band from Salt Lake City

DONE, and the band blasts out a song; the big drum booms in your chest.

### g_salt_lake · p.38 · GOOD: Salt Lake City Hears · viewpoint: A street in Salt Lake City

'It's DONE!' Flags, bands, a cannon (smoke first, then BOOM: light is faster than sound). Thousands will fill the Tabernacle.

Variant line (by route):
- handcart: The old woman who pulled a handcart: 'In a few days. Not a whole summer.'
- _default: A man whose family came by wagon: 'Now it will take days.'

### g_deseret · p.39 · GOOD: The Operator · viewpoint: A young woman telegraph operator in Salt Lake City

Three dots, the blows, then D-O-N-E under her pencil. The office cheers; she sends it on down the Deseret Telegraph.

### g_washington · p.40 · GOOD: Washington Hears · viewpoint: The Western Union office in Washington, D.C.

You hold on past the three dots and the blows; at 2:47 Washington time the bell spells DONE. In New York, cannons fire 100 times.

### e_safety_return · p.41 · BAD: Safety Return · cause: Tried to change what happened

Bzz, bzz, bzz: the band takes you home and locks. Each variant line explains why that thing had to stay as it was.

*What could you try differently? Watch, and keep your hands still. The band can only record a moment you leave just as it was.*

### e_out_of_charges · p.42 · BAD: Out of Charges · cause: Tried a trip with no charges left

Press. Nothing. The band uses backup power to take you home. (Handcart + full Ten-Mile Day + May 10 = one trip too many.)

*What could you try differently? Every trip used a charge. Which trips mattered most?*

### e_in_photo · p.43 · BAD: In the Picture · cause: Ran in front of the camera

You'd be a blur in a famous photo, a girl who was never there. The band pulls you home.

*What could you try differently? Where could you stand to watch the picture being made, without being in it?*

### e_wrong_day · p.44 · BAD: The Wrong Day · cause: Went on May 8, the planned day

Nothing happens on May 8: the Union Pacific train is stuck (unpaid workers chained Durant's car; rain hurt a bridge). The clock runs out.

*What could you try differently? The date on the golden spike was the plan. Which day did it really happen?*

### e_wrong_place · p.45 · BAD: The Wrong Promontory · cause: Went to Promontory Point instead of Promontory Summit

Salt water, gulls, and rocks. No railroad.

*What could you try differently? The railroad climbed up to the top. What's another word for the top of a climb?*

### e_steam · p.46 · BAD: Lost in the Steam · cause: Got too close to an engine's steam valves

WHOOSH: the engineer opens the drain valves and the band's lens fogs. Reached from Jupiter's front wheels (s14) or by running up to Jupiter as it arrives (s12).

Variant line (by route):
- wheels: By the front wheels, just as the hammer goes up.
- arrive: Running up to Jupiter as it hisses to a stop.

*What could you try differently? Steam is very wet. Where could you watch from, away from the puffs?*

### e_time_up · p.47 · BAD: Time's Up · cause: Waited longer than the one-hour trip clock

Beep, beep, beep: zero. The band brings you home before the big moment.

Variant line (by route):
- camp: Fell asleep by the fire.
- tenmile: The day had twelve hours; the clock had one.
- jupiter: Landed at 11 for Jupiter and stayed: the laurel tie is out and Shilling is at his table when the clock runs out, forty minutes before the spike.

*What could you try differently? The band can only stay one hour. How could you get there closer to the moment?*

### e_too_early · p.48 · BAD: Too Early in Washington · cause: Went to Washington at 12:47 Washington time

Washington's clocks say 12:47, but in Utah it's not even 11. Nothing comes. The clock runs out.

*What could you try differently? The sun reaches the East first. Were Washington's clocks ahead or behind?*

### e_too_far · p.49 · BAD: Too Far Away · cause: Watched from the far hill, too far away to hear

You see the hammer swing, but the sound is faint and the wind is loud. The recording is mostly wind.

*What could you try differently? Sound gets quieter far away. How could you get closer?*

### e_blast · p.50 · BAD: Stand Clear! · cause: Ran toward the lit fuse

The fuse is getting shorter; 'STAND CLEAR!' The band's safety rule pulls you home before the boom.

*What could you try differently? Where else could you watch the workers, safely?*

### e_too_soon · p.51 · BAD: Too Soon! · cause: Stopped recording at the three-dot start signal

NEW in v2. You let go at three dots (the signal that the blows are STARTING). The recording is click, click, click, then nothing: no DONE. Reached from the telegraph table (s21) or the Washington bell (s28).

Variant line (by route):
- table: At Shilling's table.
- bell: At the Washington bell.

*What could you try differently? Three dots were the signal to start. Which word were you waiting for?*

## Choices that test a science or history idea

- s07/s08: rails need gaps (heat) → pushing them together is a Safety Return.
- s05: May 8 (date engraved on the spike) vs May 10 → The Wrong Day.
- s11: Promontory Point vs Promontory Summit (a summit is the top of a climb) → The Wrong Promontory.
- s14: standing by the cylinder cocks (steam) → Lost in the Steam.
- s22: running in front of a slow camera → In the Picture.
- s25: sun time, Washington 12:47 vs 2:47 → Too Early in Washington.
- s29: sound gets quieter with distance → Too Far Away.
- s04/s09/s12: the one-hour trip clock → Time's Up (s12: landing at 11 for Jupiter and staying runs out with the ceremony setting up).
- s21/s28: three dots meant START, not done → Too Soon!
- s12/s14: steam from the engine's drain valves fogs the lens → Lost in the Steam.
- s06: a lit fuse, 'Stand clear!' → Stand Clear!

## Counts

- Story scenes: 30
- Endings: 21 (10 GOOD, 11 BAD)
- Choice branches: 85
- Total pages: 51 (plus a 'You were really there' photo page after each GOOD ending)

Flowcharts: `story_map.mmd` (full) and `story_map_compact.mmd` (short labels; thick arrows cost a charge). Facts and sources: `FACTS.md`.
