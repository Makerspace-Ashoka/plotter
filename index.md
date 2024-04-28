---
title: DIY Plotter
---

## Finding Inspiration

Youtube. Search, "How to build a pen plotter". Found a couple videos:

- https://youtu.be/WgsTyhX311E?si=pykW71T5uxcJOCAv
- https://youtu.be/CW3tCkms7oM?si=zcMRKgs8F6E5Ye7R

Then I found a corresponding instructable:

- https://www.instructables.com/DIY-Homework-Writing-Machine-Using-Arduino-2D-Pen-/

## Gathering Materials

Thankfully, the instructable had a Bill of Materials: https://docs.google.com/spreadsheets/d/1K6GGZx7ZxFlsE_SG4vm4hw3O7Y4HbJr1x2MOWS65IPo/edit?usp=sharing.

Since it was my first time, I had no clue why we needed all these parts. I compiled a shopping list, keeping some nuts and bolts as extras.

With the help of lab staff, I gathered:

**Mechanical Parts**:
+ GT2 Timing Belt
+ GT2 Pulleys (20 teeth 5mm bore)

**Electrical Parts**:
+ Arduino Cable

**Nuts & Washers**:
+ M3, M4, M5 Hex nuts
+ Random washers

Then I went down to Chawri Bazaar to get what I needed. It was really tought to source loose pieces of things I needed in this wholesale market. It wasn't difficult to find people who had things, it was simply impossible to buy 100-500 qty. packs of each item.

However I found one shop which allowed me to get bolts if I bought at least 10 of each. From here I got:

**Bolts:**
+ M3 12mm, 16mm
+ M4 12mm, 16mm
+ M5 12mm, 16mm, 20mm, 45mm

**Nuts:**
+ M5 Nyloc Nuts

Tried very hard to find Aluminium V-slot extrusions (2020, 2040). All the shops near Ajmeri Gate and Paharganj were again wholesalers, so they needed you to buy at least 15ft of any item.

So I ordered these from amazon:
+ 2020, 2040 V slot extrusions (500 mm)
+ M4 Sliding Nuts
+ Openbuilds POM wheel kits (bigger ones)

Later, I visited Lajpat Rai Market to source electronics. As per lab staff's recommendation, Bonus Electronics had everything I needed at quite a reasonable price! From here I got:

+ Arduino Uno R3
+ CNC Shield V3
+ Short-circuit jumpers for the shield
+ NEMA 17 4.2 kg-cm Stepper Motors
+ DRV 8825 Stepper Drivers
+ 12V 2A DC Adapter

Make sure you also buy an Arduino cable (USB A to B) if you don't have one!

### Update: (More Shopping)

1. The steppers had different connectors than intended, had to buy a fresh set online from [robocraze.com](robocraze.com).
2. The stepper drivers weren't giving a Vref reading, got a pair of A4988 and DRV8825 (just incase) from [roboticsdna.in](roboticsdna.in).
3. Similarly ordered: 3D printer springs, Idler pulleys, M5 sliding nuts.
4. Bought two cheap click pens for their springs.

## Substituting materials

The instructable used button head bolts, but I had bought allen head (hex) bolts. Upon reviewing the build process, I realised this didn't matter.

For the POM wheels, I'd need low-profile bolts. These have heads that don't jut out of the surface of the hole they're in, allowing you to put whatever on top. I later realised these would come with any POM wheel _kit_ that I bought!

I couldn't find rubber feet (used for anti-vibration) for the frame, so I hope to 3D print the frame's feet using ABS. This was inspired by: https://youtu.be/wbEcyv422MU. (This step might just be unnecessary!)

### Update:

#### Low profile bolts and spacers

I needed long (45mm) M5 low profile bolts, the ones that came with the wheels are much shorter. Thankfully, I have M5 45MM bolts (allen heads), so I made space for these in my CAD design for the gantry plate of the 2040 V slot.

The wheel kits also had only one spacer each. I'd need two spacers for the wheels in the 2040 gantry, so I'll just use M5 nuts as spacers for now.

#### 3mm rods for pen lifter

Couldn't find these. Possible alternatives:
- Cut a long 3mm wide nail
- Cut 3mm allen keys

# CAD

As I went throught the video above, I started reverse engineering the design on CAD, since my submissions required STEP files.

It took me two nights, and a lot of guesstimating + calliper use to finally come up with the STEP/STL files that can be found in my repository.

It wasn't that difficult to eyeball the widths of the bigger parts (feet for e.g). For the finer parts like the Arduino Holder, Pen lifter (using the servo wing), NEMA 17 mount and Idler mounts it was easy to find CAD for these parts themselves, and with the help of CAD assemblies, I referenced these parts and tried to make accurate designs.

I had already received most of the materials ordered, and having a list of parts was helpful. For the holes, I just referred to my inventory and inferred which bolts would go where.

The pen lifting mechanism was the most time taking. I had to sketch out surfaces in almost all planes,split bodies and drill precise holes. I assumed three general widths for the clip:
- your average parker jotter (small ~0.4mm diameter),
- the click pen with rubber grips (medium ~0.65 mm diameter)
- and the whiteboard marker (large ~1mm diameter).

# Assembly

Okay, so now since we have all the materials we need:

### For the frame:

+ 2020 V Slot

+ 2040 V Slot

### Mechanical Parts:

+ POM Wheel Kits

+ GT2 Timing Belt

+ GT2 Pulley (20 teeth)

+ Idler Pulley

### Electronics:

+ NEMA 17, MG90 Servo

+ Arduino, CNC Shield, DRV8825


### 3D Printed Parts

+ X axis feets + mounts + arduino plate

+ X axis wheel plates

+ Y axis mounts

+ Y axis wheel plate

+ Pen Lifter (with springs, metal shaft)

+ Pen Clip

### Nuts, Bolts:

+ M3

+ M4

+ M5

# Wiring & Electricals

## Arduino + Shield + Drivers

### 1. Setting up the drivers

- Connect all the 3 resolution pins using short circuit jumpers
- Align EN of the shield and the driver
- Set Vref of DRV8825 to 0.5 V (since the current limit for my stepper is 1A)

### 2. Enabling the CNC shield

- put a jumper across EN and GND

### 3. Connect the shield to the arduino

### 4. Connect the motors to the drivers

### 5. Connect the servo

## Making Appropriate Connectors

### Separating + and - from the DC adapter's barrel plug

- Cut the DC barrel plug
- Strip roughly 3 cm of the black wire
- Strip the red and white wires
- Use a multimeter to confirm polarity (Red: +, White: -)


# Adding the code

Thanks for reading. Hope this inspires you to build smth on ur own!
