The machine's design was inspired and reverse engineered from this youtube video:
[https://youtu.be/CW3tCkms7oM?si=zcMRKgs8F6E5Ye7R].

Corresponding usage was available on this video: [https://youtu.be/bhzCfIEzs0w?si=ZM_HDrldhI3U40fd].

# Summary of Work

+ Gather Materials
+ Reverse engineer + CAD design based on the video above
+ Assembly + CAD redesign
+ Uploaded GRBL ([GitHub](https://github.com/bdring/Grbl_Pen_Servo)) and used [UGS](https://universalgcodesender.com/) to demo machine usage.

Here's what I learnt from this build:

# What was used and why

## Steppers and timing belts

Stepper motors allow precise movement control and they are used across different types of CNC machines. For this purpose, precisely manufactured mechanical parts like the GT2 pulley and timing belt have been used in this build.

When used with the correct set of electronics (the stepper drivers and Arduino CNC shield in my case), they provide an interface which tells the computer their exact location and how much rotation corresponds to how much movement.

Software configuration or hardware devices like limit switches can be used to define a range of motion for each axis in the machine.

There are other potential alternatives too, which can be further explored.

## Choice of stepper drivers

While the DRV8825 are slightly superior too A4988s in terms of their maximum current/voltage ratings and they allow for 1/32 microsteps, they were not quite necessary since there are only three switches in the CNC shield (beneath each driver) for setting the resolution. Since, both the DRV and A4988 are slightly noisy drivers, it was better to just use the A4988 since they are cheaper than DRV8825.

## Idler vs GT2 on the 2020 profile

In the final build, I swapped out the Idler pulley on the 2020 profile for a GT2 pulley instead (unlike the 2040 profile where the Idler remained). This was because I hadn't made the mount for the Idler long enough, so the Idler was kinda close to the profile. The pulley's width made the timing belt rise out of the aluminium channel and grate against the edges.

## Pen Lifter Mechanism

In one the designs, the pen lifter mechanism was a simple holder where the pen is inserted and a screw holds it in place.

This takes a while to change pens, and the screw can also scratch the pen. Also, the pen clip mechanism has the option to adjust the tilt for a pen, which is nice plus.

However, one down side of the refill-based pen lifter is that it is flimsy, so when the pen moves up and down there can be artificacts in the image drawn.

## Arduino with CNC shield

The arduino and CNC shield are cheaply available parts which served the purpose of the build. Additionally, the firmware used in this build (i.e, GRBL) is fairly well-documented and easy to use with the arduino.

## Software

There are two steps when using the machine:
+ First an image needs to converted to G-Code. While I found Inkscape and some corresponding extensions, it would take a lot of time to adequately resolve compatibility issues, so I used a readily-available G-Code file instead. (Credits: [https://github.com/misan/gcodeFont])

+ Then a G-Code Sender connects to the GRBL firmware running on the arduino and sends the file above to the plotter which then plots it.
