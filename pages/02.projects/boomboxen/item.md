---
title: Boomboxen
taxonomy:
  category: project
  tag: [ project, hardware, audio ]
---

This is my first attempt at a battery-powered portable audio system, built in Summer 2015.

===

# Prototype Concepting
A few weeks ago I got the urge to build some kind of portable stereo that would serve equally well on the workbench and as a ghetto blaster. I bounced ideas between paper sketches and simple 3D models, shopped around for potential parts, and came up with a design that could be started with what I had on-hand, plus speakers and batteries.

Eventually a good tripath or class D amp would be ideal, but I already have a small car amp to get started. At least a couple hours of use by either amp from a single charge was the goal, so I looked into the small 12V SLA batteries used in UPSes. Two were modeled in Tinkercad, the UB1250 (5Ah) and UB1280 (8Ah). Since a decent amp would require 24V I opted for 2 of the smaller UB1250.

The box would be built from a piece of 3/4” teak ply, roughly 11” x 44”, and I decided to keep it simple by minimizing the number of cuts. First cut off the 2 ends, rip the remaining length into top+bottom & front+back, cut each in half, and finally trim the ends to match. Combined with dimensions of major components (batteries, speakers, amp) this determined the enclosure dimensions. A final 3D model was used to verify everything should fit.

TODO: embed CAD file

# Construction
Last weeekend I assembled a working prototype based on the concept I drew up, and it’s been used a few hours at a time in various settings since. The sound is impressive, especially at moderate volume. There’s some background noise that I’m still trying to track down, hopefully just the low quality amplifier. Originally I planned to have a USB outlet in parallel with the amp, but the interference is much worse with both audio and USB power connected to the source, so I’ll need a workaround.

I’m surprised how long a single 5Ah battery lasts with the class A/B amp, and the class D should improve it significantly. For that the batteries will be in series to create 24V. Until then I had planned to run the batteries in parallel, but I might keep it simpler until then and just switch between the batteries, which I’ll describe more below. This week I’ll take some measurements over time to generate a baseline power profile.

The enclosure turned out a little less clean than I was hoping but it still serves its purpose, and I like the way it looks. I’m debating whether to bevel/round the edges and attach corner protectors.

TODO: embed construction gallery

## Connectors

  -  3.5mm stereo audio input
  -  12V lighter socket
  -  5V USB socket

## Switches

  -  SPST: Amp remote (on/off)
  -  DPDT: Amp power (battery 1/2)
  -  DPDT: Aux power (battery 1/2)

The Aux switch will determine which battery is connected to the 12V & 5V sockets, and an external 12V source can be connected for charging the boombox. Once I have the class D amp I plan to make a control panel that slides into a cutout on top. That will provide a nice volume, rather than always running at full throttle and depending on the source to regulate volume to a tolerable level. It’s going to need some kind of handle too.

Previously I assmebled the components to create a portable soundsystem. This weekend I completed the setup with a control panel, electrical, and carry handle. Finished weight is 22 lbs 11 oz.

## Control panel

The control panel is thick plexiglass with cutouts for switches, power outlets, fuses, and a voltage display. A slot was cut into a recess made in the top of the enclosure, and another slot in the back panel locks the control panel in place. This was more difficult than I anticpated, even with the RotoZip, because the corners are inaccessible with the routing attachment in place. Those areas were done freehand.

##Batteries

Batteries are secured with a few strategically placed nails. They lock in tight, preventing movement left/right or up/down, and the speaker + rear panel prevents front/back movement.
Electrical

There are currently two 12V batteries and two circuits: amplifier & external power

Each circuit can be connected to the left or right battery by a switch. Additional switches control amplifer on/standby (via the Remote signal) and USB charger on/off. The voltage meter reads the current voltage of the amplifier circuit. In retrospect I’ll probably move this to the Remote signal so it turns off when the amp is off (also acting as amp power indicator).

The amp is screwed down with 2 of its original 4 feet, so a metal band will be required to tie down the upper half soon.

## Carry handle

The handle is made from 1/2” black pipe. It’s simple and rugged, and it’s hollow so cables and/or a carry strap can run through it.

Check out the gallery for photos of control panel, electrical, finished enclosure, and carry handle.

TODO: embed gallery 2

Recorded through my phone, not the best mic but you get the idea.

TODO: embed video
