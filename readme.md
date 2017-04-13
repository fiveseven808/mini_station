Readme:

The Mini-Station is a raspberry pi powered keychain that can play all of the emulators supported by retropie!

This repository will contain the schematics, BoM and related scripts for the project so that it can be easily reproduced.

Open source projects used:
Adafruit - Nanoscreen
RetroPie
fbtft
fbcp




Current plan:
Well, it seems that rewriting nanoscreen will be harder than initially thought
The init sequence requires the dc line to be toggled when sending init commands vs the ssd1331 that just needs dc held low
This makes things hard since I don't know how to code in C well...

What I will do now I guess is to design around the ssd1331 display since i know it will work. the unfortunate part is that with this screen, everything is entirely unreadable. this is in contrast to the ssd1351 display where you can at least make out most words, even without the nice scaling done by nanoscreen

I have multiple cases and more can be ordered by gearbest so we can try multiple approaches. i.e. a ssd 1351 based one vs a 1331 based one. a 1351 based one will be a little big larger than the case i've provided, so adjustments will need to be made or protections for the display need to be added. i do not have access to a 3d printer so I am not sure I will follow through with this.

Here's the current pros and cons of each design choice:

SSD1331 based mini-station:
+ Will be just as small as Adafruit's mame station, if not smaller
+ Probably the smallest portable and playable (but not readable) emulation station
+ Scaling code will allow runs of higher resolutions without much issue, meaning we can have Wii-U type functionality with the system running on a tv as well as the onboard display
+ Power consumption will not get any lower than this...
+ Can make use of the Raspberry pi boxes I have on hand with all components fitting into the box
+ Landscape and Portrait configurations possible
+ Possible to bypass 3.3v onboard reg to pull from pi's psu with less efficiency losses
- Can't read text on screen at all...
- Screen is definitely small

SSD1351 based mini-station:
+ Huge 1.5" display!!!
+ Less CPU consumption using fbtft and fbcp
+ Can read most/all text on screen!
- Framerate needs work
- Power consumption is significantly more than SSD1331
- Larger battery needed for any usefulness
- Can't run in parallel with hdmi output since there's no scaling
- Colors don't seem as vibrant (but could be an init sequence thing)
