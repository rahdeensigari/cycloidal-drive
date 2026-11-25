# November 11 - Overview

I'm not actually going to start designing yet today, but I want to set some of my design criteria and intent. I've made a lot of robotics actuators in the past, and I intend for this one to be my fifth and hopefully most powerful, reliable, and most efficient iteration. While all of the actuators that I've made in the past have been reduced through planetary gearboxes, I instead plan on using a cycloidal drive for this, as it better reflects what are in commercial robotic actuators. I'm also going to drive this with an Eaglepower LA8308 90KV drone motor and an ODrive S1, as I have experience with both of these and know that they work reliably.

<img width="280" height="233" alt="image" src="https://github.com/user-attachments/assets/482a4036-5579-48e9-915d-37d7496bd456" /><img width="307" height="254" alt="image" src="https://github.com/user-attachments/assets/dd94ee3c-b149-4337-81ea-5d6bbe6ab0f0" />

The eventual goal with this is to either create a quadrupedal robot or a 6-dof robotic arm.

**Total Time Spent: 0.24 Hours**

# November 12 - Started CAD

I'm going to jump straight into CAD today. As with any other good CAD design, I'm going to start with a parametric layout sketch to define the dimensions of the actuator before I start more high fidelity modelling. First, considering that the motor I plan on using is 91.8mm in diameter, I want the overall actuator to have a diameter of around 120mm. I started by sketching the position of both the motor and the controller:

<img width="627" height="502" alt="image" src="https://github.com/user-attachments/assets/887d0fab-a237-4a8d-8d7b-ebbc6acb05f8" />

I then spent some time researching the actual mechanics on cycloidal drives. I'm going to settle with a 10:1 reduction to maximize torque while still keeping the actuator backdriveable and meeting the criteria of a quasi-direct-drive actuator. Luckily, I actually found a featurescript that can generate the cycloid disk for me, as well as the layout sketches for all of the pins (of course, I did research the actual formula to create the shape, it is quite interesting and I would recommend reading [it](https://blog-assets.solidworks.com/uploads/sites/3/Building-a-Cycloidal-Drive-with-SOLIDWORKS.pdf).

<img width="774" height="636" alt="image" src="https://github.com/user-attachments/assets/979b97b3-3535-4bec-b557-7a32c81d17e7" />

**Total Time Spent: 1.04 Hours**

# November 13 - Layout Sketch and Cylcoids

I started today by figuring out how I am going to incorporate the outside pins. My plan is going to be to use steel dowel pins that I'm going to adhere to the walls of the frame with CA. The optimal design would be to use actual bearings, but I don't think that is necessary for this.

<img width="385" height="514" alt="image" src="https://github.com/user-attachments/assets/744ad147-1d1f-465d-ad70-e3fd9da80259" />
<img width="100" height="47" alt="image" src="https://github.com/user-attachments/assets/34b2a094-b67d-4bf0-b773-c90170095d0a" />

After that I worked on the eccentric bearing. Honestly it took me a while to think of how I was going to do this, but I do think I eventually figured something out. The main problem that I was thinking of was designing it in a way to where I could actually assemble the bearings and the cycloids, and additionally in a manner to where I could mount it effectively to the motor. The way I'm going to do this is by having the bearing mount in several parts then simply using a bolt and a nut to connect everything together. Here's a little sketch I made:

<img width="709" height="521" alt="image" src="https://github.com/user-attachments/assets/d292a9fd-6ed3-41b1-abd6-6ead594b732a" />

I also just went ahead and created the actual cycloid profile with the featurescript from earlier in my layout part studio. I also set the material to 7075 Aluminum, because that's the most ideal material for something like this:

<img width="882" height="802" alt="image" src="https://github.com/user-attachments/assets/76c06b62-379d-4299-9ba9-7b89507cb26a" />

Additionally, here are my current variables that I'm using to keep this as parametric as possible, most of these were found through actual parts off McMaster-Carr or values that just meet my design requirements:

<img width="642" height="501" alt="image" src="https://github.com/user-attachments/assets/4c71af1f-6a50-4907-a590-08834e2cf8e7" />

Ok so I did a little bit of research and I have some decently big changes to make. Instead of using dowel pins for the outer rollers, I am going to actually use real bearings. This means that I can actually 3D print the cycloids now, and the money I save from that should hopefully compensate for the price of the bearings. I'm also going to have 8mm bearings riding inside of the output holes on the cycloid.

I just spent an exorbitant amount of time trying to get this featurescript to work, and so far I have not been very successful to say the least. I tried to model the second disk, but the output pins were misaligned, which I discovered was a result of some weird trick I was doing to get the disk to be aligned with the origin in a way that made it to model making it so that the eccentricities of the two disks were messed up:

<img width="1247" height="1091" alt="image" src="https://github.com/user-attachments/assets/5ade893f-a7d8-458a-9312-c7ad286631f8" />

However, even after I discovered that I was still having difficulties. I still cannot figure out how to get the holes between the two disks to line up properly. I'm sure there's some math I can do to figure it out, but I really can't think of anything right now. I'll come back to this tommorow:

<img width="765" height="830" alt="image" src="https://github.com/user-attachments/assets/22ca7db6-01e9-4487-9a4e-5b62a4b91fc5" />

**Total Time Spent: 1.94 Hours**

# November 14 - Figured out Cycloids and Printed Prototype

I think it was just late last night because I fixed the alignment issue in like two seconds, all I had to do was use the transform tool to rotate the cycloid and shift it over to where it lines up with the bearing. You can see that the pins line up too now:

<img width="751" height="717" alt="image" src="https://github.com/user-attachments/assets/1e36a8ae-54e5-400a-bf27-f691c975ebc8" />

Also, really quickly, before I continue the design I want to make a 3D printable test of the concept as a whole. To do this, I started by just making a new part studio where I remade the cycloid, this time with all of the pins:

<img width="882" height="700" alt="image" src="https://github.com/user-attachments/assets/aa2f6006-0099-40f5-a871-9e2ebf784f36" />

I then created the second disk based off of the first and offset the output disk to match (the eccentricity was messed up in all of the photos so far, I fix this later):

<img width="621" height="494" alt="image" src="https://github.com/user-attachments/assets/27f1c89d-7d4a-4692-adf9-a1bc1c2a51c5" />

Kind of a skip forward, but I did finish the design of the prototype:

<img width="710" height="696" alt="image" src="https://github.com/user-attachments/assets/6da77ba1-aca0-4e2a-b1a1-8abeccb04164" />

First note, I tried to add at least a 1/8mm clearance between any parts that move to account for 3D printing tolerances, such as the cycloid disks and the internal pin holes. Everything structural is snap fit, if I need to get it on better I'll just glue it. I also separated the eccentric bearing and the handle to let me assembly it easier. I went and printed everything out at minimal settings, 2 walls and 5% adaptive cubic infill:

<img width="1095" height="817" alt="image" src="https://github.com/user-attachments/assets/703a3533-3050-479b-b1cd-d3a1abe05f39" />

Parts printed:

<img width="4080" height="3072" alt="image" src="https://github.com/user-attachments/assets/d8364de9-cefc-426e-be4f-b831f2be9dc0" />

But, some of the pins didn't have enough clearance, and the arm and the bearing didn't have enough strength to hold up, so I reprinted those parts with proper clearances and printing settings. I did have some difficulties when I was assembling everything, the top plate still didn't fit, so I just decided to not include it. Additionally, one of the outer pins broke off, but it still worked fine without it. Another thing was that I think I clocked the disk weirdly when I assembled it for the first time because the output bearings didn't line up, but after redoing the assembly it worked fine. With everything assembled, the geometry seemed to line up fine, meaning that I'm ready to translate this to my real design.

<img width="4080" height="3072" alt="image" src="https://github.com/user-attachments/assets/492b8918-8f5b-482c-84f0-acf211727f5f" />

**Total Time Spent: 1.23 Hours**

# November 15 - Continued Layout Sketch

With the geometry proved, I could continue my layout sketch further. I started by figuring out the mechanics of how I was going to mount the outer roller bearings. I was originally going to have them riding on a bolt threaded into the base, but I did some research and I think that a more elegant solution would be to use dowel pins. I was originally going to have the bearings riding directly on the dowel pins, but after some research I realized that this would not work as the pins have a positive tolerance while the bearings have a negative tolerance on the bore, resulting in an interference fit that would not really work for this application:

<img width="434" height="546" alt="image" src="https://github.com/user-attachments/assets/5826151c-02f6-420b-8646-04151dd8c4bf" /><img width="600" height="562" alt="image" src="https://github.com/user-attachments/assets/d87c7615-6632-4a78-a60c-cf441daa0fe1" />

An easy way to fix this is just to have the dowel pin covered by a 3D printed sleeve that bearings ride on, with spacers to get the bearing to the right position. This is also a common trick we use in FRC, which is where I got the idea. While I was trying to figure that out in my layout sketch, I kind of got distracted and started working on the inner pins instead, so I guess I will talk about that. The first thing I did was add a third part to the eccentric shaft that is lined up to the origin. This is where the internal output bearing will ride on (I still need an outer one as well). The flange is to space everything apart:

<img width="602" height="258" alt="image" src="https://github.com/user-attachments/assets/0aa1c9c2-37a0-4871-bfff-dd6d8df7673d" />

The disk that goes around that bearing is the output disk, and is also where the internal pins are going to be mounted. I was originally planning to use dowel pins to retain these as well, but I realized that these had to be retained on both sides, so I have to use bolts instead. This also means that I'm going to have to do have some sort of carriage on the bottom as well. I can do something clever here by having the bottom carriage be retained via a bearing wrapping around the motor output, but it does still have to be retained from the outside as well. Fitting all of this in a compact space is going to be a challenge; I will continue this tomorrow.

**Total Time Spent: 0.92 Hours**

# November 16 - Layout Sketch + Part Modelling

I started today by defining some of the geometry for the dowel pins that I'm going to use, I'm probably going to use 2mm wide pins. I also thought about a little bit and what I'm probably going to do is have an interference fit on the bottom for the dowel pins to fit into and have a clearance fit on top so I can still disassemble this thing after I make it:

<img width="300" height="613" alt="image" src="https://github.com/user-attachments/assets/7a953140-cd06-41f1-b4ea-ad52ce1d2181" />

Honestly, I'm still not good enough at visualization to continue fully defining this layout sketch without getting some basic geometry modelled first, so I want to at least model enough to where I can get a good enough idea of what I plan to make to where I can continue the layout sketch. The first thing I did to do this was to import the motor into the assembly to get a general idea of where it's going to be placed:

<img width="762" height="845" alt="image" src="https://github.com/user-attachments/assets/36b6f901-9c95-4c87-83a1-9a2661f3db8d" />

While I was already in the assembly, I also derived the encoder mount from another [project](https://github.com/rahdeensigari/bldc-qdd-actuator) that I made that also used the same motor. I did have to change it slightly though, as for some reason it was too long originally. It is also important to note that I am of course using a diametric magnet here for the encoder to work properly. I'm going to have the ODrive mounted directly under this to read the poles from the magnet:

<img width="644" height="545" alt="image" src="https://github.com/user-attachments/assets/4a46c671-dce0-4f9b-8235-995eda586fe4" />

Speaking of which, I also had to change the height of the base to allow for the magnet and the encoder to be spaced 1mm apart, which is the distance that ODrive themselves recommend for proper functionality (that short green line at the bottom is the encoder profile):

<img width="1054" height="349" alt="image" src="https://github.com/user-attachments/assets/7cbd45e4-0f03-4808-8b99-5a3062f88a8a" />

Anyways, with that out of the way I kind of want to start modelling stuff. Specifically I want to start with the base that the motor is mounted on. I can do something clever here, since the motor is slightly curved at the top, I can split the top of the base into two parts then protrude the top part out a bit and slightly cover the motor. This gives me more material around the dowel pin, as currently it would be quite close the the walls of the mount:

<img width="637" height="668" alt="image" src="https://github.com/user-attachments/assets/1c1fe62c-db09-406c-8399-8d3ac5213dde" />

I achieved this by deriving the outer part of the motor into my part studio then using that as a reference for the curve (the outrunner is colored red to signify that it is a derived part, albeit it is pretty obvious nevertheless):

<img width="562" height="800" alt="image" src="https://github.com/user-attachments/assets/409cad6f-4609-4e24-b339-edcea743581e" />
<img width="757" height="690" alt="image" src="https://github.com/user-attachments/assets/f262dd6f-92d6-45f7-bf6a-77406cf81f80" />
<img width="1334" height="568" alt="image" src="https://github.com/user-attachments/assets/b0ed0533-7945-44e6-aa49-f822af1b2bb5" />

On second thought, 2mm might be too small for the dowel pins. I'm going to bump the diameter up to 2.5mm instead. I also added the holes for these in the top flange part. I want to this to be a tight fit, so I'm only adding 0.125mm to account for 3DP tolerances:

<img width="933" height="766" alt="image" src="https://github.com/user-attachments/assets/8adf92d1-9a40-4016-b782-a26492659e93" />

**Total Time Spent: 1.52 Hours**

# November 17 - Developed Motor Mount and Output Pins

I started first by adding mounting holes for the motor in the bottom of the base. These are counterbore M4 clearance holes that use the bolts the motor comes with to fasten the motor to the base:

<img width="1123" height="719" alt="image" src="https://github.com/user-attachments/assets/e750d4f9-f144-4a95-8158-d92537857941" />

Next, I added bolts to connect the base and the top flange together. I achieve this by using an M3 flathead bolt with an embedded nut at the bottom of the base. Depending on how the design develops, I may remove these later in favor of a larger bolt connecting all of the stages together. It was also a challenge to space these holes apart, as there are 11 outer pins, making it functionally impossible to have three evenly spaced holes that don't interfere with the pins. To fix this, I had to have some of the holes be at a different angle from each other. I spent way too long trying to figure out an alternative way to do this but eventually just decided on having them be different angles apart:

<img width="1069" height="967" alt="image" src="https://github.com/user-attachments/assets/906d4272-4070-420e-894f-f16d40b919c2" /><img width="301" height="321" alt="image" src="https://github.com/user-attachments/assets/61a2e78d-85a5-4609-96bc-1266dd20fb6d" />

The last thing I was able to do for today was work on the outer pin assembly. The first thing I did was have the dowel pins cut deeper into the flange, most likely meaning I am going to have to use longer pins. I haven't done the top mount for the pins yet so I can't determine their exact length until that is complete. As for the bearing stack, I was originally going to have a long outer spacer over the pin with a diameter of 4mm, but I quickly realized that for this to work properly the spacer would need to have 1mm thick walls, which is more finnicky then I would have liked. Instead, I decided to switch to 6mm ID bearings which gives me more thickness for the internal spacer. Since these spacers are thinner, this also means that I can double stack the bearings on each pin. For the spacers themselves, I was (as mentioned before) going to have an internal spacer around the dowel pins that the bearings were mounted on, but I quickly realized that a better way to do this would be to have three parts for each pin, one part for the bottom that spaced the bearing up while acting as the internal spacer, another that did the same thing for the second bearing, and a final spacer (which may just be the terminating disk):

<img width="598" height="840" alt="image" src="https://github.com/user-attachments/assets/75daebbc-d6ab-4687-af09-ff260e695d34" />

Kind of poor journal quality today, everything I did was done at school where GitHub is blocked so I couldn't journal in real time like I normally do.

**Total Time Spent: 2.43 Hours**

# November 19 - 20 - Developed Outer Pins, Changed Gear Ratio, Worked on Eccentric Shaft

First, for the output pins, I added shims between the bearings and put everything together in the main assembly:

<img width="934" height="953" alt="image" src="https://github.com/user-attachments/assets/a55d0716-5b84-4794-8d0c-c1d8019e4628" />

I've also decided to make a pretty big change, and that is to reduce the gear ratio from 10:1 to 9:1. I have a couple of reasons for doing this, but the main one is that it makes sourcing the outer pin bearings easier as I don't need to buy another pack just to get an extra 4 bearings, and it also makes things such as the motor mount flange retention that I was dealing with in the last journal entry significantly easier. Luckily, my CAD is pretty parametric, so all I had to do to change this was change the lobe count variable then make some minor fixes to some sketches. I also decreased the overall diameter to 115mm and did 5 holes for the motor mount flange connection instead of 3:

<img width="864" height="884" alt="image" src="https://github.com/user-attachments/assets/9561afc8-ba62-43a2-8ecb-97b356240bed" />

I then started to model the eccentric bearing shaft. Each segment of this needs to be its own separate part for it to be able to get assembled. First I made the actual base where the motor gets mounted to. I have four countersunk holes that attach the base directly to the motor, with a flange eccentric to the center of the shaft where the inner race of the first disk bearing lies on:

<img width="614" height="573" alt="image" src="https://github.com/user-attachments/assets/e7be3d0d-ca70-4abe-a2d9-42f4c4a6c4c2" />

Next was the actual shaft where the cycloids themselves rest on. This part is separated into two segments, one for each disk. There are also two flanges in the middle where the inner race of the bearing is retained by. I also subtracted the diameter of the shaft for the bearings by 1/8mm to account for the negative tolerances on the bearing as well as 3D printing tolerances:

<img width="485" height="472" alt="image" src="https://github.com/user-attachments/assets/d5ca5ed2-5685-41ce-8abc-e2f6fee90b73" />

I then modelled the motion of both cycloidal disks in the assembly. Of course, I can't upload a video of it working here, but I did use mate animations to ensure that everything will move as intended:

<img width="734" height="679" alt="image" src="https://github.com/user-attachments/assets/d4ad0b06-775e-439f-af72-7e5e8ca96f1b" />
<img width="874" height="816" alt="image" src="https://github.com/user-attachments/assets/00505914-e4f0-42fa-8fda-f7a901ebd7ca" />

**Total Time Spent: 1.92 Hours**

# November 21 - Developed Eccentric Shaft and Inner Pins

I lost a lot of progress on this journal entry because I reloaded the web page, so I'm just going to have to briefly summarize what I did. The first thing that I did was split the segment of the eccentric shaft where the actual disks are connected to into one individual segment for each disk. This will make printing and assembling this much easier. I also decided to get rid of the mounting holes I had for the motor mounting base and the flange, and I'm instead going to have external connection holes that go through every part of the assembly to connect it together as I have done in many of my previous actuators. Doing this also gives me a way to rest the actuator while testing. After that I proceeded to modelling the inner pins, which is going to be the hardest part of this design. For the actual pin bearings themselves, I'm going to use 8mm OD 5mm ID ball bearings using the same dowel pin method as I did for the outer bearings. The more important part however is how I'm going to retain the pins. I need two plates, one on the bottom and one on the top where the pins can be mounted onto. For the bottom plate, I'm going to use the first shaft segment as a place to mount a bearing onto where the plate is going to be retained. For this I'm going to use a 6807zz bearing (on a side note, the difference in price between McMaster and Amazon when it comes to bearings is astounding):

<img width="906" height="682" alt="image" src="https://github.com/user-attachments/assets/049826e4-f42a-4b80-b8e0-df4db3a865ad" />

I also spent a decent chunk of time organizing everything into subassemblies, specifically the eccentric shaft and the disks. Unfortunately this broke the animations I had earlier, but this will be fixed once I finish the rest of the eccentric shaft:

<img width="892" height="895" alt="image" src="https://github.com/user-attachments/assets/e94603be-6d5c-46e1-a004-f495abf511d7" />

I also created this guard around the outer roller pins. I left 0.5mm of clearance between the bearings and the print and 3mm between the actual disk:

<img width="991" height="831" alt="image" src="https://github.com/user-attachments/assets/7122b2bb-1dd3-4b7a-9fbe-fb6e8607e541" />

Here is a section view of everything so far:

<img width="1268" height="786" alt="image" src="https://github.com/user-attachments/assets/bc6dc4a3-3090-4555-97bc-8091044a2440" />

**Total Time Spent: 1.63 Hours**

# November 22 - Developed Inner Pins and Output

I want to work more on the inner pins. First I started by defining the bearing locations in my layout sketch for parametricity:

<img width="245" height="858" alt="image" src="https://github.com/user-attachments/assets/10436ceb-9878-4d4b-95a1-79c1ac83dcf6" />

After that I started working on the output plate that carries all of the inner pins bearings. I decided that I'm still going to have the bearing riding on a 3D printed sleeve, but this time held together by an M3 bolt. This simplifies assembly and holds everything together much nicer than dowel pins. This plate sits on top of the bearings and is where any attachment like an arm is mounted from. It also needs to be supported by two bearings, one in the middle where the eccentric shaft ends, and one bearing on the outside (haven't added the outer bearing yet):

<img width="539" height="398" alt="image" src="https://github.com/user-attachments/assets/36139c2b-78c8-4f0d-9981-50ae6fa1a876" />

I then started modelling the actual spacers for the bearing stacks. This is really similar to what I did for the outer pins, so I'm not going to dwell on this too much. Basically the only difference is that I'm using a bolt instead of a dowel pin, and the shim needs to be 3D printed because I couldn't find any COTS shims that would work.

<img width="463" height="733" alt="image" src="https://github.com/user-attachments/assets/467ee0c5-0c54-47a1-8dbb-7a166aa0c799" />
<img width="324" height="539" alt="image" src="https://github.com/user-attachments/assets/0c1f1116-94bb-44ad-b517-830909cac574" />

**Total Time Spent: 1.85 Hours**

# November 23 - Continued Inner Pins, Shaft

Continued inner pins today, specifically the bottom connector piece. How I plan to do this is to have a flange on the bottom to retain the entire assembly, with holes on the bottom for inset nuts:

<img width="590" height="366" alt="image" src="https://github.com/user-attachments/assets/02e4bafb-7f01-4170-aa3d-758ee02914b6" />
<img width="512" height="435" alt="image" src="https://github.com/user-attachments/assets/64a64fa4-9d45-44c7-bf1f-9314f57ceffc" />

I also integrated a spacer for the bearing stack on it:

<img width="302" height="383" alt="image" src="https://github.com/user-attachments/assets/d7bcc911-ab1a-466d-9f0c-fee4707753e2" />
<img width="551" height="774" alt="image" src="https://github.com/user-attachments/assets/7790d42c-b817-4526-a098-f89f92023d26" />

I am going to print this part out of PLA as a test though, because I feel like this is kind of pushing my manufacturing capabilities, and of course one of the main things I hope to gain from this is an increase in my DFM skills. (Update, it printed fine):

<img width="3072" height="4080" alt="image" src="https://github.com/user-attachments/assets/3760ac79-bdf1-42ac-8ce5-eacc56bdb66b" />

Also after talking to some people about it I decided to actually use a trapped nut (meaning I pause the part while it's printing then put the nut in) rather than relying on friction while assembing:

<img width="419" height="342" alt="image" src="https://github.com/user-attachments/assets/2a79546f-0bd9-46cd-b166-e39d150020e3" />

With that I completed the inner pin setup:

<img width="636" height="578" alt="image" src="https://github.com/user-attachments/assets/088421b3-a4c8-49e8-8a7f-6ceaf1a74390" />
<img width="826" height="872" alt="image" src="https://github.com/user-attachments/assets/abb55277-890a-4a6b-83b0-eca8fd0d373f" />

After that, I created the final shaft segment and added the through hole. I'm going to retain them with a similar method as I did the inner pins with the inset nuts:

<img width="486" height="498" alt="image" src="https://github.com/user-attachments/assets/242e6a35-ad91-4383-8815-683dedc13260" />

I also spent a lot of time trying to figure out how to get the animations to work in the main assembly, but ultimately could not figure it out. I'll tackle that tommorow.

**Total Time Spent: 1.8 Hours**

# November 24 - Figured Out Mates and Output Disk

I spent ~20 minutes figuring out the mate animations from yesterday. How I eventually got it work was by using gear relations with the distinct revolute mates. Obviously I can't post a video here but just trust that it works:

<img width="855" height="948" alt="image" src="https://github.com/user-attachments/assets/6a4360a5-22bd-4f85-9a45-4cae3a4d2027" />

I'm actually pretty close to being finished here. The last major thing I want to add is a secondary output bearing. This was something that was lacking in my old actuator designs that I think will allow for more stability. The problem is that the only bearing big enough for this is really big. Unfortunately, I'm just going to have to make it work. I increased the height of the output and added a flange at the top for the bearing to be retained by. Also, I have the countersunk bolts inset so that I don't need to order another length and can just use the same length for everything:

<img width="1072" height="260" alt="image" src="https://github.com/user-attachments/assets/8d249d5c-0bed-4024-9fb1-e2d7a89185f5" />

**Total Time Spent: 0.53 Hours**
