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
