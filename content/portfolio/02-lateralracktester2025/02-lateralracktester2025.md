---
date: '2025-09-01T08:31:00-05:00'
draft: false
title: 'Lateral Rack Tester (2025)'
weight: 2
---

## Project Background
Every bicycle rack sold by Trek must adhere to the ISO 11243 test standard, which dictates a suite of static and fatigue tests with both vertical and horizontal forces in reference to the standard mounting position of the rack on the bicycle. 

This project was replacing an existing lateral fatigue test machine which had some limitations and elements of its design that needed to be redesigned. 
* The enclosure of the machine was too small to allow modern larger e-bikes and cargo bikes
* The mechanism of the oscillation induced many extra oscillations and caused direction change too quickly, imparting extra load on the racks and in some cases prematurely failed bolts utilized

## Summary / Description of the Machine
* Image of CAD
* GIF of motion

The final deliverable of the machine was a machine frame built out of AngleLock [[Lateral Rack Tester (2025)#First implementation of AngleLock]], a Beckhoff control system, with safety off switches and E-Stops. The machine could oscillate (x kg) at (x millimeters above the axis of rotation) at 1 Hz with an arc of +/- 10 degrees or +/-15 degrees. A counterbalance was utilized to assist the servo motor and smooth out machine. The height of the counterbalance from the axis of rotation was fixed but the mass could be adjusted using readily-available strength training barbell plates. The low mass accuracy of the barbell plates was not an issue for this application.

Fixtures were created to accommodate a wide range of bicycle frames, rear bicycle racks by themselves, front bicycle racks by themselves, and headtube mounted front bicycle racks by themselves. 

As of this writing the machine has gone through tens of millions of cycles and tested dozens of different test samples. 


## Project Features

#### First implementation of the Beckhoff control system
After the Test Department decided to move forward with the adoption of [[Operations#Selection of Beckhoff Control System]] the Lateral Rack Tester was the first machine that we developed with Beckhoff.  
The machine utilized Beckhoff rotary servo motors, EtherCAT field boxes (EP series), and an integrated HMI/controller. The utilization of field boxes allowed the control panel to be placed anywhere, with only a single servo motor/encoder cable and EtherCAT cable going back to the control box, with all other sensor wires not extending beyond the machine itself. Safety toggle switches and E-Stops were implemented. 
The control system was written in Structured Text in TwinCAT3 version 4024.

#### Calculation of torque requirements, inertia, counterbalance, and working with Beckhoff to get the correct gearbox and servo

Although the majority of the time the machine would only be handling standard bicycles and rack loads an additional requirement of the machine was to be able to handle cargo bikes at their maximum weight carrying capacity. This significantly increased the size of the components required.
The torque requirement was calculated by...
#### FEA and fatigue analysis for shaft selection
Due to the high number of cycles for a standard test and due to the fully reversing nature of the test, a fatigue analysis was required for the shaft. **FEA** in **Onshape** was utilized to calculate the principal(?) or Von Mises (?) stresses. These values were then used in (some formula) to determine the (something). The general rule of thumb of steels having a fatigue strength around half of their Ultimate strength was utilized to confirm we had a factor of safety of x. A shaft made of Steel (some alloy). 
#### First implementation of Gates Timing belt, and selection of components
At the beginning of the project, several mechanism options were considered between traditional mechanisms that convert rotational motion into oscillation, or a rotational or linear servo or stepper in combination with a gearbox and gearing or a timing belt could be used. After all of the options were considered it was decided that a timing belt would be the best path forward (for reasons). After consulting the Gates Design Manual (link?) a Power Grip GT4 belt was selected and the subsequent calculations performed to select the components required. 
#### Usage and calculation of Fenner keyless bushings
In our effort to reduce the number of machined parts required to keep lead times low, we wanted to be able to purchase a **COTS** shaft with constant diameter. This presents problems with how to locate parts along the shaft, especially in this machine where some parts are pillow block bearings allowing rotation of the shaft, but other parts must be coupled to teh shaft, and the motion of the shaft is continuously reversing. Additionally, the required length of the test platform also required a long shaft so that the load could be evenly distributed along the shaft. A COTS shaft that was long enough could be obtained with keyways at the ends but not along the entire length. Designing splines or other machined features was avoided due to the aforementioned lead time concerns. I located Fenner Keyless Bushings (link?) and did some preliminary calculations to see if they would work. This was also a contributing factor in determining our final shaft size. I performed the final calculations and consulted with the engineering staff at Fenner to verify that the fully reversing conditions of my application would not be a problem, or would not require an additional compensating factor in the calculations for the torque ratings of the bushings. 
I utilized the design guidelines from Fenner to design the bushing carriers 
(Image of carriers)
After tens of millions of cycles the drives have not slipped from their installed position.
#### First implementation of AngleLock
After discovering AngleLock [[Operations#Selection of New Vendors]]and determining they would be worth trying with fixturing or on a new machine, I decided to go forward with utilizing AngleLock for the entire machine. I consulted with AngleLock on the expected hold-force rating of a variety of their fasteners and designed the machine around the requirements. 

This was a success. The lead times were short for all components. The adjustable assembly has been very beneficial. The AngleLock system allows new fixturing to be designed and manufactured quickly, usually out of laser cut sheet metal parts. 

#### Requirements of the child carrier

The first test sample to go on the machine was a bicycle frame with an integrated rack that allowed the mounting of third-party child carriers. The child carrier standard was a new standard that had not been tested before in the lab and the mass of the child carrier was placed a further distance from the axis of rotation than any other test sample. Because the radius value of intertia is squared, any distance from the axis of rotation has a large influence on the total system inertia. This was another design requirement of the machine
The test standard required custom made bags of sand to be used. I located a vendor who could create custom bags out of cordura and fill them with sand to the required mass specification. I created the drawings for the "legs" and "body" of the child as required by the standard. 

#### Many (some number?) adjustable fixtures to accomodate a wide range of rack types