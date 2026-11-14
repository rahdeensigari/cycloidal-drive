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

# November 13 - Continued Working on CAD

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
