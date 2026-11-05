# Evelyn and the TimeBand: The Golden Spike (v1)

Reader: Evelyn, age 5  
Status: full draft for parent review: decision tree, narration, and illustrations done. No recorded narration yet (browser voice / text-only).

## Premise

Dr. Ada Finch is an inventor at the museum who buys honey from your mom, a beekeeper. Your Apollo 11 recording now plays at the museum every day. Her new mission: on May 10, 1869, the first railroad across America was finished at Promontory Summit, Utah Territory, when the last spike went in and the telegraph sent the word DONE. The museum has photos of that day, but no sound: no one could record sound until Edison's phonograph in 1877. Your mission: bring home a recording of the moment the railroad was finished (the last spike and the telegraph word DONE). Mom says many of your great-great-grandparents walked to Utah as Latter-day Saint pioneers, some pulling handcarts, so a side trip to an 1856 handcart company is offered. TimeBand rules (same band as the Moon trip): (1) Three charges: each trip into the past uses one; the trip home is free (backup power); a trip tapped at 0 charges sends you home (Out of Charges). (2) Safety rule: watch and record, but never change what happened; if you touch, move, or say something that could change history, the band brings you home and locks. It also pulls you home from danger. (3) Record: press the red button and hold still; when it saves a big moment it beeps twice and brings you home. (4) Trip clock: the band can hold you in the past for one hour per trip (like the Moon suit's one hour of air); when the clock runs out, it brings you home. (5) Blend in: Dr. Finch brings 1869-style clothes (calico dress, apron, bonnet, boots) so nobody notices you.

## Tracked items and flags

| Id | Type | Starts | What it does |
|---|---|---|---|
| `charges` | counter | 3 | **TimeBand charges.** Each trip costs 1. Home is free. A trip tapped at 0 goes to Out of Charges. Shown as 3 dots. |
| `walked_trail` | flag | False | **Walked with the handcart company.** Set on arrival at s03. Unlocks 'Find the handcart pioneers' in Salt Lake City (s26 -> s27) and adds lines at good endings. |
| `ten_mile` | flag | False | **Saw Ten-Mile Day.** Set on arrival at s09. Unlocks 'Stand with the Chinese crew' at the last rail (s17 -> s18): you know who they are. Adds lines at endings. |
| `knows_code` | flag | False | **Knows the dot-dash code.** Set by following the telegraph crew on Ten-Mile Day (s08) or by asking Dr. Finch on the wire map (s25 shows it free). Unlocks 'Listen for the code' at the telegraph table (s20 -> s21) and adds a line at DONE endings. |
| `saw_grades` | flag | False | **Saw the Latter-day Saint grade crews.** Set on arrival at s06. Adds lines at Salt Lake City / band endings (these were the people who built the grade). |
| `clock_min` | counter | 60 | **Trip clock (minutes).** Shown in past scenes. Choices that wait for hours lead to Time's Up. |
| `via` | note | None | **Route note.** Picks the variant line for endings reached from more than one scene (safety, time_up, salt_lake, telegraph). |
| `recording_saved` | flag | False | **Mission done.** Set at every GOOD ending. The band beeps twice and saves the recording for the museum. |

Any choice marked **(trip, -1 charge)** costs one charge. With 0 charges, it goes to **Out of Charges**.
With three charges, one play-through can visit at most three of: the handcart trail, the grades, Ten-Mile Day (a 2nd charge to see sunset), Promontory Summit (sunrise costs a 2nd charge to reach noon), Salt Lake City, Washington. Every path has to give something up.

## Scenes

### s01 · p.1 · The Second Mission
*Your kitchen, Saturday morning*

Dr. Finch comes for honey and brings the TimeBand. Your Moon recording plays at the museum. New mission: bring home the sound of the moment the first railroad across America was finished, May 10, 1869. Nobody could record sound then. Mom says many of your great-great-grandparents walked to Utah, some pulling handcarts. Dr. Finch gives you 1869 clothes and repeats the rules, plus the one-hour trip clock.

**Science:** Sound is air shaking. In 1869 no machine could save it; the first one came in 1877.

**Choices:**
- If you want to visit a handcart company on the trail in 1856, tap 'Visit the handcart trail.' → **s02 The Handcart Trail** *(trip, -1 charge)*
- If you are ready to pick a day in 1869, tap 'Open the mission map.' → **s05 The Mission Map**

### s02 · p.2 · The Handcart Trail
*Beside the Platte River, Nebraska Territory - August 1856, late afternoon* · trip clock 60 min

You land by the Platte River beside the first handcart company (Captain Edmund Ellsworth). People pull and push two-wheeled carts. Four-year-old Annie walks beside the captain; she was promised bread and butter in the valley. One wheel squeaks.

**Science:** Wheels make heavy loads easier to move: they roll instead of drag.

**Choices:**
- If you climb up and ride in a handcart, tap 'Ride in a cart.' → **e_safety_return Safety Return** *(sets via=cart)*
- If you walk at the side of the trail near Annie, tap 'Walk with Annie.' → **s03 The Squeaky Wheel**

### s03 · p.3 · The Squeaky Wheel
*Camp by the Platte River - before sunset* · trip clock 40 min

The company stops to camp. A man turns the squeaky cart over: the wooden hub has rubbed the wooden axle thin and hot. He wraps it with a strip of tin. Dr. Finch: walking 15 miles a day, they need all summer; a train will do it in days.

**Science:** Friction: things that rub slow down, get hot, and wear away. Smooth metal rubs less than rough wood.

**On arrival:** set walked_trail=True

**Choices:**
- If you pick up the hammer and fix the wheel yourself, tap 'Hammer it yourself.' → **e_safety_return Safety Return** *(sets via=wheel)*
- If you stay and watch the camp make supper, tap 'Stay for supper.' → **s04 Songs at Camp**

### s04 · p.4 · Songs at Camp
*Camp by the Platte River - sunset* · trip clock 10 min

Supper cooks on fires of dried buffalo chips. The camp sings the handcart song: 'Some must push and some must pull.' The trip clock is low.

**Science:** Fire turns stored energy in fuel into heat and light. Out here there are few trees, so they burn dried buffalo dung.

**Choices:**
- If you curl up by the warm fire for a little nap, tap 'Sleep by the fire.' → **e_time_up Time's Up** *(sets via=camp)*
- If you go home and open the mission map, tap 'Go home to the map.' (Going home is free.) → **s05 The Mission Map**

### s05 · p.5 · The Mission Map
*The TimeBand screen, in your kitchen*

A line crosses America. The Central Pacific built east from California; the Union Pacific built west from Nebraska. Stops: March 1869 (two grades side by side), April 28 (Ten-Mile Day), May 8 (the date engraved on the golden spike), May 10 (the real day; opens a free place picker). The wire map is free.

**Science:** A map is a small picture of a big place.

**Choices:**
- If you want to see the workers building the grade in March 1869, tap 'The two grades.' → **s06 Two Grades** *(trip, -1 charge)*
- If you want to see the record day, April 28, 1869, tap 'Ten-Mile Day.' → **s08 Ten-Mile Day** *(trip, -1 charge)*
- If you want to go on May 8, 1869, the date on the golden spike, tap 'May 8.' → **e_wrong_day The Wrong Day** *(trip, -1 charge)*
- If you want to pick a place for May 10, 1869, tap 'May 10.' (Picking is free.) → **s11 Two Promontories**
- If you want to look at the telegraph wires, tap 'Look at the wires.' (Looking is free.) → **s25 The Wire Map**

### s06 · p.6 · Two Grades
*Promontory Mountains, Utah Territory - late March 1869* · trip clock 60 min

Crews, many of them Latter-day Saints from nearby towns, build grade under contracts Brigham Young signed in 1868. Two grades run side by side, one for each company, because nobody has picked the meeting place. Up the hill a crew is blasting: 'Blast! Stand clear!'

**Science:** A grade is a long ramp of dirt and rock that holds the track.

**On arrival:** set saw_grades=True

**Choices:**
- If you run up the hill to watch the blasting, tap 'Run up to the rock cut.' → **e_blast Stand Clear!**
- If you walk down to the ravine where the crews are filling it in, tap 'Go to the Big Fill.' → **s07 The Big Fill**

### s07 · p.7 · The Big Fill
*Spring Creek ravine, Promontory Mountains - late March 1869* · trip clock 45 min

Mule teams dump cart after cart into the ravine: the Big Fill, built for the Central Pacific by Benson, Farr and West, Latter-day Saint contractors. Beside it, the Union Pacific builds the wooden Big Trestle. Iron wheels on iron rails roll easily but slip on steep hills, so track must stay almost flat.

**Science:** Slopes and gravity: iron on iron has little friction, great for pulling heavy loads, but wheels spin on steep hills. So builders cut hills and fill low places.

**Choices:**
- If you jump on an empty dump cart for a ride, tap 'Ride the dump cart.' → **e_safety_return Safety Return** *(sets via=dumpcart)*
- If you jump ahead to April 28, Ten-Mile Day, tap 'Go to Ten-Mile Day.' → **s08 Ten-Mile Day** *(trip, -1 charge)*
- If you want to pick a place for May 10, tap 'Open May 10.' (Picking is free.) → **s11 Two Promontories**

### s08 · p.8 · Ten-Mile Day
*Near Victory camp, Utah Territory - April 28, 1869, 7:15 a.m.* · trip clock 60 min

Charles Crocker bet his crews could lay ten miles in a day. Horses pull iron cars of rails; eight Irish rail handlers set each rail; Chinese crews lay ties, spike, and bolt. A good spiker drives a spike in three blows. A telegraph crew hangs wire right behind. Rails get small gaps at the ends.

**Science:** Heat makes iron grow a tiny bit, so rails need small gaps or they would push and bend on hot days.

**Choices:**
- If you push two rails tight together to close the gap, tap 'Push the rails together.' → **e_safety_return Safety Return** *(sets via=gap)*
- If you watch the rail team up close, tap 'Watch the rail team.' → **s09 Iron and Tea**
- If you follow the crew that hangs the telegraph wire, tap 'Follow the telegraph crew.' → **s09 Iron and Tea** *(sets knows_code=True)*

### s09 · p.9 · Iron and Tea
*Ten-Mile Day - about 8:15 a.m.* · trip clock 35 min

Track moves as fast as you walk. Each rail weighs about 560 pounds. Chinese tea carriers bring tea made with boiled water. By 7 p.m. they will have laid 10 miles and 56 feet, a record that still stands. The day is long, and your clock is short.

**Science:** Boiling water kills many germs.

**On arrival:** set ten_mile=True

**Choices:**
- If you wait here to see the end of the day, tap 'Wait for the end.' → **e_time_up Time's Up** *(sets via=tenmile)*
- If you jump ahead to 7 o'clock tonight, tap 'Jump to sunset.' → **s10 Ten Miles!** *(trip, -1 charge)*
- If you want to pick a place for May 10, tap 'Open May 10.' (Picking is free.) → **s11 Two Promontories**

### s10 · p.10 · Ten Miles!
*Ten-Mile Day - 7:00 p.m.* · trip clock 60 min

The last spike of the day goes in and the crews cheer: ten miles and 56 feet. Jim Campbell runs an engine fast over the new track to show it is solid. The railhead is only a few miles from Promontory Summit.

**Science:** A heavy hammer moving fast hits hard. Three blows drive a spike.

**Choices:**
- If you want to pick a place for May 10, tap 'Open May 10.' (Picking is free.) → **s11 Two Promontories**
- If you want to look at the telegraph wires, tap 'Look at the wires.' (Looking is free.) → **s25 The Wire Map**

### s11 · p.11 · Two Promontories
*The TimeBand screen - May 10, 1869*

A free place picker. The Promontory is a long finger of land in the Great Salt Lake. Promontory Point is at its tip by the water; Promontory Summit is up in the hills to the north, where the railroad climbs. Even 1869 newspapers mixed them up. Times offered: sunrise or noon.

**Science:** A summit is the top of a climb.

**Choices:**
- If you go to Promontory Point, at the tip of the land by the lake, tap 'Promontory Point.' → **e_wrong_place The Wrong Promontory** *(trip, -1 charge)*
- If you go to Promontory Summit at sunrise, tap 'The Summit at sunrise.' → **s12 Sunrise at the Summit** *(trip, -1 charge)*
- If you go to Promontory Summit at noon, tap 'The Summit at noon.' → **s13 Promontory Summit** *(trip, -1 charge)*

### s12 · p.12 · Sunrise at the Summit
*Promontory Summit - May 10, 1869, sunrise* · trip clock 60 min

Cold morning. A street of tents and shacks. At the end of the track there is a gap just long enough for two rails, one per company. The ceremony is about six hours away.

**Science:** Cold air makes your breath into a little cloud: the water in it turns into tiny drops.

**Choices:**
- If you sit by the ties and wait for the spike, tap 'Wait for the spike.' → **e_time_up Time's Up** *(sets via=morning)*
- If you jump ahead to noon, tap 'Jump ahead to noon.' → **s13 Promontory Summit** *(trip, -1 charge)*

### s13 · p.13 · Promontory Summit
*Promontory Summit - May 10, 1869, about noon* · trip clock 60 min

Jupiter (Central Pacific, wood, funnel stack) and No. 119 (Union Pacific, coal, straight stack) stand a short gap apart. Hundreds of people: workers, soldiers, bosses, a few women, an army band and the Tenth Ward Band from Salt Lake City. Brigham Young is in southern Utah; Bishop John Sharp and Ogden's mayor Lorin Farr came for him. A telegraph table, a photographer.

**Choices:**
- If you go see the two engines, tap 'Go see the engines.' → **s14 Two Engines**
- If you go to the gap where the last rails go down, tap 'Go to the last rail.' → **s17 The Last Rail**
- If you go to the man with the big camera, tap 'Go to the photographer.' → **s22 The Photographer**
- If you stay at the back of the crowd, tap 'Stay at the back.' → **s29 The Back of the Crowd**

### s14 · p.14 · Two Engines
*Promontory Summit - about 12:10 p.m.* · trip clock 50 min

The engines hiss. A steam engine is a giant kettle: fire boils water, steam pushes pistons, pistons turn wheels. Jupiter burns wood and its funnel stack catches sparks; No. 119 burns coal. Engineers George Booth (Jupiter) and Sam Bradford (No. 119). Pipes drip by Jupiter's front wheels.

**Science:** Steam power and pressure: steam takes up much more room than water, so it pushes hard.

**Choices:**
- If you stand by Jupiter's big front wheels to record, tap 'Stand by the front wheels.' → **e_steam Lost in the Steam**
- If you climb up into Jupiter's cab, tap 'Climb into Jupiter.' → **s15 Jupiter's Cab**
- If you climb up into No. 119's cab, tap 'Climb into No. 119.' → **s16 No. 119's Cab**

### s15 · p.15 · Jupiter's Cab
*Inside Jupiter's cab - about 12:20 p.m.* · trip clock 40 min

The fireman feeds the firebox with wood. A glass tube shows the water; a gauge shows steam pressure. The whistle cord hangs overhead. You can see the gap and the telegraph pole.

**Science:** A pressure gauge shows how hard the steam is pushing.

**Choices:**
- If you pull the whistle cord, tap 'Pull the whistle cord.' → **e_safety_return Safety Return** *(sets via=whistle)*
- If you rest your arm on the cab window and record from here, tap 'Record from the cab.' → **g_jupiter From Jupiter's Cab**
- If you climb down and go to the last rail, tap 'Go to the last rail.' → **s17 The Last Rail**

### s16 · p.16 · No. 119's Cab
*Inside No. 119's cab - about 12:20 p.m.* · trip clock 40 min

The fireman shovels coal. No. 119 came by surprise: a flood in Weber Canyon damaged a bridge, the first engine could not cross, and No. 119 came to the rescue from Ogden.

**Science:** Coal packs more heat into a small pile than wood.

**Choices:**
- If you throw a lump of coal into the fire, tap 'Throw in some coal.' → **e_safety_return Safety Return** *(sets via=coal)*
- If you hold still in the cab and record from here, tap 'Record from the cab.' → **g_119 From No. 119's Cab**
- If you climb down and go to the photographer, tap 'Go to the photographer.' → **s22 The Photographer**

### s17 · p.17 · The Last Rail
*At the gap - about 12:20 p.m.* · trip clock 35 min

An Irish Union Pacific squad carries one last rail; a Chinese Central Pacific squad in clean blue shirts carries the other. Under them is the polished laurel tie with a silver plate and drilled holes. Gold is soft, so the golden spike just drops in the hole and gets a tap; a plain iron spike, wired to the telegraph like the hammer, does the real job.

**Science:** Gold is soft. A hard hit would bend it.

**Choices:**
- If you reach out and touch the golden spike, tap 'Touch the golden spike.' → **e_safety_return Safety Return** *(sets via=spike)*
- If you saw Ten-Mile Day, you may know some of these workers. Stand with the Chinese crew. Tap 'Stand with the Chinese crew.' → **s18 The Chinese Crew** *(needs ten_mile)*
- If you stand with the Union Pacific's Irish crew, tap 'Stand with the Irish crew.' → **s19 The Irish Crew**
- If you go to the telegraph table, tap 'Go to the telegraph table.' → **s20 The Telegraph Table**

### s18 · p.18 · The Chinese Crew
*Beside the last rail* · trip clock 30 min

The crew came from Victory camp this morning; their boss is H. H. Minkler. Thousands of Chinese workers built the Central Pacific through the Sierra Nevada snow and the desert. The speeches and most photos will leave them out.

**Choices:**
- If you stand still with the crew and record, tap 'Record with the crew.' → **g_crew The Crew Who Laid It**
- If you go to the telegraph table, tap 'Go to the telegraph table.' → **s20 The Telegraph Table**

### s19 · p.19 · The Irish Crew
*Beside the last rail* · trip clock 30 min

The Union Pacific track crew, many born in Ireland, under foreman Guilford. They laid track from Nebraska. A spare maul leans on the ties; a worker explains the long handle.

**Science:** A long handle makes the hammer head move fast. A fast, heavy head hits hard (a lever).

**Choices:**
- If you pick up the spare maul and swing it, tap 'Swing the spare maul.' → **e_safety_return Safety Return** *(sets via=maul)*
- If you stand still with the crew and record, tap 'Record with the crew.' → **g_irish Mauls Up!**

### s20 · p.20 · The Telegraph Table
*By the telegraph pole - about 12:27 p.m.* · trip clock 25 min

W. N. Shilling sits at the key. Pressing the key lets electricity flow down the wire; the clicks reach Omaha, Chicago, Washington, New York, and San Francisco almost at once. He taps 'Almost ready. Hats off. Prayer is being offered.'

**Science:** Telegraph: electricity in a wire carries a signal almost instantly. On, off, on: dots and dashes.

**Choices:**
- If you reach over and tap the telegraph key, tap 'Tap the key.' → **e_safety_return Safety Return** *(sets via=key)*
- If you learned the dot-dash code, stay close and listen. Tap 'Listen for the code.' → **s21 Hats Off** *(needs knows_code)*
- If you want to hear the news arrive somewhere far away, tap 'Look at the wires.' (Looking is free.) → **s25 The Wire Map**

### s21 · p.21 · Hats Off
*By the telegraph table - about 12:45 p.m.* · trip clock 15 min

The prayer by Reverend John Todd. Speeches. Spikes presented. Shilling taps: 'All ready now. The spike will soon be driven. The signal will be three dots for the start of the blows.' Leland Stanford lifts the wired hammer.

**Choices:**
- If you press record and hold the band near the key, tap 'Record the clicks.' → **g_telegraph D-O-N-E**
- If you climb on the table to see better, tap 'Climb on the table.' → **e_safety_return Safety Return** *(sets via=table)*
- If you jump to Washington, D.C., to hear the same clicks arrive there, tap 'Jump to Washington.' → **s28 Washington, D.C.** *(trip, -1 charge)*

### s22 · p.22 · The Photographer
*Near the engines - about 12:15 p.m.* · trip clock 45 min

Andrew J. Russell, the Union Pacific's photographer, with a big wooden camera and a darkroom wagon. Each picture is made on a sheet of glass. The camera needs a few seconds of light, so people must hold still or they blur. A second photographer is from Salt Lake City.

**Science:** A camera collects light. Dim light needs more time, so anything that moves turns into a blur.

**Choices:**
- If you run in front of the camera and wave, tap 'Run in front and wave.' → **e_in_photo In the Picture**
- If you stand behind the camera and record, tap 'Stand behind the camera.' → **g_camera Hold Still!**
- If you meet the photographer from Salt Lake City, tap 'Meet the other photographer.' → **s23 Charles Savage**

### s23 · p.23 · Charles Savage
*Near the tracks* · trip clock 40 min

Charles R. Savage came from England and has a studio in Salt Lake City. He is a Latter-day Saint. His glass plates are heavy and break easily. He says Salt Lake City will hear the news by telegraph at the same moment.

**Science:** Glass is hard but brittle: it doesn't bend, it breaks.

**Choices:**
- If you offer to carry his box of glass plates, tap 'Carry his glass plates.' → **e_safety_return Safety Return** *(sets via=plate)*
- If you jump to Salt Lake City to hear the news arrive there, tap 'Go to Salt Lake City.' → **s26 Salt Lake City** *(trip, -1 charge)*

### s24 · p.24 · The Tenth Ward Band
*Near the crowd* · trip clock 25 min

The Tenth Ward Band from Salt Lake City in bright uniforms (a ward is a Latter-day Saint congregation). Horns are long, curled tubes; buzzing lips shake the air inside. A drummer sets his drum down.

**Science:** Sound is shaking air. A longer tube makes a lower note.

**Choices:**
- If you pick up the sticks and play the drum, tap 'Play the drum.' → **e_safety_return Safety Return** *(sets via=drum)*
- If you stand by the band and record, tap 'Record with the band.' → **g_band Music at Promontory**
- If you jump to Salt Lake City, where the band came from, tap 'Go to Salt Lake City.' → **s26 Salt Lake City** *(trip, -1 charge)*

### s25 · p.25 · The Wire Map
*The TimeBand screen*

Telegraph wires spread across the country like a web. The clicks reach everywhere almost at once. But in 1869 every town sets its clocks by its own sun, so when it is 12:47 at Promontory it is about 2:47 in Washington. Dr. Finch also shows how DONE looks in dots and dashes.

**Science:** Sun time: the Sun reaches the East first. (Railroads later made time zones, in 1883.)

**On arrival:** set knows_code=True

**Choices:**
- If you go to Salt Lake City, about 90 miles from Promontory, tap 'Salt Lake City.' → **s26 Salt Lake City** *(trip, -1 charge)*
- If you go to Washington when its clocks say 12:47, tap 'Washington at 12:47.' → **e_too_early Too Early in Washington** *(trip, -1 charge)*
- If you go to Washington when its clocks say 2:47, tap 'Washington at 2:47.' → **s28 Washington, D.C.** *(trip, -1 charge)*

### s26 · p.26 · Salt Lake City
*Salt Lake City, Utah Territory - May 10, 1869, just after noon* · trip clock 60 min

Flags, bands on corners, cannons ready on Arsenal Hill. The city has no railroad yet; the line comes to Ogden. Dr. Finch: they will build the Utah Central to Ogden and finish it in January 1870. The big new Tabernacle stands nearby.

**Choices:**
- If you wait on the street for the signal, tap 'Wait for the signal.' → **g_salt_lake Salt Lake City Hears**
- If you walked with the handcart company, look for people who walked here too. Tap 'Find the handcart pioneers.' → **s27 People Who Walked** *(needs walked_trail)*
- If you go to the telegraph office, tap 'Go to the telegraph office.' → **s30 The Telegraph Office**

### s27 · p.27 · People Who Walked
*A street corner in Salt Lake City* · trip clock 50 min

An old woman tells her grandson she pulled a handcart in 1856; it took all summer, and now people can come by train in days. Annie would be seventeen now. You can't tell if she is here.

**Choices:**
- If you tell her you walked with a handcart company too, tap 'Tell her you walked too.' → **e_safety_return Safety Return** *(sets via=tell)*
- If you stand by her and record, tap 'Record with the crowd.' → **g_salt_lake Salt Lake City Hears** *(sets via=handcart)*

### s28 · p.28 · Washington, D.C.
*Western Union office, Washington, D.C. - 2:40 p.m. (Washington clocks)* · trip clock 60 min

A crowd in the telegraph office. The manager, Mr. Tinker, hooked a bell to the wire so every click rings it. 'We have got done praying. The spike is about to be presented.' Chicago answers: 'We understand; all are ready in the East.'

**Science:** A bell-sounder: electricity pulls a little hammer to ring a bell.

**Choices:**
- If you ring the bell yourself to hurry things up, tap 'Ring the bell yourself.' → **e_safety_return Safety Return** *(sets via=bell)*
- If you hold still by the bell and record, tap 'Record the bell.' → **g_washington Washington Hears**

### s29 · p.29 · The Back of the Crowd
*Promontory Summit - about 12:30 p.m.* · trip clock 40 min

All you see are coats and hats. Sound spreads out and gets quieter with distance; the wind carries the speeches away. A hill would show everything, but it is far. The band is warming up.

**Science:** Sound spreads out as it travels, so it gets quieter far away.

**Choices:**
- If you climb the hill to see everything from far away, tap 'Climb the hill.' → **e_too_far Too Far Away**
- If you say 'excuse me' and squeeze to the front by the telegraph table, tap 'Squeeze to the front.' → **s21 Hats Off** *(sets via=squeeze)*
- If you follow the sound of the band, tap 'Follow the music.' → **s24 The Tenth Ward Band**

### s30 · p.30 · The Telegraph Office
*Telegraph office, Salt Lake City* · trip clock 55 min

A young woman sits at a telegraph desk. In Utah, many young women learned the code and ran offices on the Deseret Telegraph, a line built by Latter-day Saints. She listens to the sounder, pencil ready.

**Science:** A telegraph sounder clicks when electricity pulls its little arm.

**Choices:**
- If you tap the telegraph key while she listens, tap 'Tap the key.' → **e_safety_return Safety Return** *(sets via=key2)*
- If you stand quietly by her desk and record, tap 'Record with her.' → **g_deseret The Operator**

## Endings

Every ending has **Start over** and **Back to my last choice**. Every GOOD ending sets `recording_saved` and is followed by a **You were really there** page of real 1869 photos.

### g_telegraph · p.31 · GOOD: D-O-N-E · viewpoint: At the telegraph table with W. N. Shilling

Stanford swings and hits the tie; Durant misses. Shilling taps the dots anyway. A worker drives the spike, and at 12:47 Shilling sends D-O-N-E. You record the clicks and the roar.

### g_jupiter · p.32 · GOOD: From Jupiter's Cab · viewpoint: Central Pacific engine Jupiter

From the cab you see the hammer swing and hear the cheer. George Booth pulls the whistle; No. 119 answers. The engines roll nose to nose and the engineers christen each other's engine.

### g_119 · p.33 · GOOD: From No. 119's Cab · viewpoint: Union Pacific engine No. 119

You record the whistles and cheers from No. 119, then feel it roll across the joined rails, the first engine to cross, before Jupiter crosses too.

### g_crew · p.34 · GOOD: The Crew Who Laid It · viewpoint: The Central Pacific's Chinese track crew

You record with the crew who laid the last rail. Afterward J. H. Strobridge invites them to dinner, and the guests stand and cheer them.

### g_irish · p.35 · GOOD: Mauls Up! · viewpoint: The Union Pacific's Irish track crew

The crew that laid track from Nebraska lifts their mauls and cheers at DONE. 1,086 miles from Omaha, 690 from Sacramento.

### g_camera · p.36 · GOOD: Hold Still! · viewpoint: Behind Andrew J. Russell's camera

After DONE, the engines meet, Montague and Dodge shake hands, and Russell calls 'Hold still!' You record the making of 'East and West Shaking Hands.'

### g_band · p.37 · GOOD: Music at Promontory · viewpoint: With the Tenth Ward Band from Salt Lake City

You record the spike, the cheer, and the band's music, feeling the drum in your chest.

### g_salt_lake · p.38 · GOOD: Salt Lake City Hears · viewpoint: A street in Salt Lake City

The signal arrives: flags, bands, and cannons from Arsenal Hill (smoke first, boom after). Thousands will gather in the new Tabernacle. Eight months later, Brigham Young drives the Utah Central's last spike.

Variant line (by route):
- handcart: The old woman who pulled a handcart wipes her eyes.
- _default: A man next to you says his family came by wagon. It took them months.

### g_deseret · p.39 · GOOD: The Operator · viewpoint: A young woman telegraph operator in Salt Lake City

The sounder clicks D-O-N-E. The operator writes it down and calls out the news, and the room cheers.

### g_washington · p.40 · GOOD: Washington Hears · viewpoint: The Western Union office in Washington, D.C.

Three dots ring the bell, then the blows, then DONE at 2:47 Washington time. The crowd cheers; in New York, cannons fire 100 times.

### e_safety_return · p.41 · BAD: Safety Return · cause: Tried to change what happened

The band buzzes and takes you home, and locks. Each variant line explains why that thing had to stay as it was.

*What could you try differently? Watch, and keep your hands still. The band can only record a moment you leave just as it was.*

### e_out_of_charges · p.42 · BAD: Out of Charges · cause: Tried a trip with no charges left

The dots are dark. The band uses its backup power to take you home.

*What could you try differently? Every trip used a charge. Which trips mattered most?*

### e_in_photo · p.43 · BAD: In the Picture · cause: Ran in front of the camera

You'd be a blur in a famous photo, a girl who was never there. The band pulls you home.

*What could you try differently? Where could you stand to watch the picture being made, without being in it?*

### e_wrong_day · p.44 · BAD: The Wrong Day · cause: Went on May 8, the planned day

Nothing happens on May 8: the Union Pacific train is stuck (unpaid workers chained Durant's car at Piedmont, Wyoming; rain hurt a bridge). Your clock runs out.

*What could you try differently? The date on the golden spike was the plan. Which day did it really happen?*

### e_wrong_place · p.45 · BAD: The Wrong Promontory · cause: Went to Promontory Point instead of Promontory Summit

Salt water, birds, and rocks. No railroad. The band takes you home.

*What could you try differently? The railroad climbed up to the top. What's another word for the top of a climb?*

### e_steam · p.46 · BAD: Lost in the Steam · cause: Stood by the engine's cylinder cocks

The engineer opens the drain cocks; whoosh, a cloud of steam. The band's lens fogs and the crowd hides the moment.

*What could you try differently? Steam is very wet. Where could you watch from, away from the puffs?*

### e_time_up · p.47 · BAD: Time's Up · cause: Waited longer than the one-hour trip clock

The trip clock reaches zero and the band brings you home before the big moment.

Variant line (by route):
- camp: The fire was warm, and the camp was quiet. Then the clock ran out.
- tenmile: The track kept growing. But the day had twelve hours, and your clock had one.
- morning: The ceremony was six hours away. Your clock had one hour.

*What could you try differently? The band can only stay one hour. How could you get there closer to the moment?*

### e_too_early · p.48 · BAD: Too Early in Washington · cause: Went to Washington at 12:47 Washington time

Washington's clocks say 12:47, but in Utah it's not even 11. Nothing will come for two hours. The clock runs out.

*What could you try differently? The Sun reaches the East first. Were Washington's clocks ahead or behind?*

### e_too_far · p.49 · BAD: Too Far Away · cause: Watched from the hill, too far away to hear

You see the hammer swing, but the sound is faint and the wind is loud. The recording is mostly wind.

*What could you try differently? Sound gets quieter far away. How could you get closer?*

### e_blast · p.50 · BAD: Stand Clear! · cause: Ran toward the blasting

'Blast! Stand clear!' The band's safety rule pulls you home before the boom.

*What could you try differently? Blasting is for grown-ups who know the rules. Where else could you watch the workers?*

## Choices that test a science or history idea

- s07/s08: rails need gaps (heat) → pushing them together is a Safety Return.
- s05: May 8 (date engraved on the spike) vs May 10 → The Wrong Day.
- s11: Promontory Point vs Promontory Summit (a summit is the top of a climb) → The Wrong Promontory.
- s14: standing by the cylinder cocks (steam) → Lost in the Steam.
- s22: running in front of a slow camera → In the Picture.
- s25: sun time, Washington 12:47 vs 2:47 → Too Early in Washington.
- s29: sound gets quieter with distance → Too Far Away.
- s04/s09/s12: the one-hour trip clock → Time's Up.

## Counts

- Story scenes: 30
- Endings: 20 (10 GOOD, 10 BAD)
- Choice branches: 81
- Total pages: 50 (plus a 'You were really there' photo page after each GOOD ending)

Flowcharts: `story_map.mmd` (full) and `story_map_compact.mmd` (short labels; thick arrows cost a charge). Facts and sources: `FACTS.md`.
