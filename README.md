Shared Thing-o-Matic Printer
=============================

This repository holds documentation and settings for my modified Thing-o-Matic printer.

What is this?
-------------

It's a somewhat souped up Makerbot Thing-o-Matic printer. It prints with 3mm ABS plastic filament, at a layer height of 0.15 mm.

Modifications include:

1. Makergear stepper extruder
2. Aluminum and Kapton build surface
3. ScribbleJ firmware
4. LED lighting
5. Fan to cool the extruder pinch wheel but NOT the extruder barrel.
6. Makergear 0.25mm nozzle
7. RepRap-style software toolchain

IMPORTANT RULES
---------------

1. Never leave the printer unattended. If you step out, point a webcam at it or have a housemate check on it.
2. Don't crash the nozzle into the build surface! If you aren't totally sure your Z-height is correct, recalibrate it.
3. Keep an eye out for signs of stripped filament. You should see the pinch wheel pushing filament cleanly, not tearing it. If there are plastic flakes on the drive gear, you're getting close to stripping it.
4. Keep an extra close eye on your print until the first layer is done. Most problems happen before this point.

How do I use it?
----------------

The general workflow:

1. Use Slic3r to convert an STL (triangle mesh) model to GCode (tool path). You can optionally view the GCode to check its sanity using a tool like Pleasant3D.
2. Place the GCode on an SD card, with the filename `sjfwauto.gcd`
3. Ensure that the build surface is clean and flat. Replace the Kapton tape if it has any tears.
4. Insert the SD card and turn on the printer.
5. The printer will warm up, home the axes, warm up some more, then start extruding to get the nozzle uniformly full of molten plastic.
6. Use tweezers to keep this thread of plastic out of the way of your build
7. Watch the model build. Actually keep an eye on the printer, it's not the most reliable machine ever.
8. Wait for the model to cool before removing it. It will be much easier, and you won't risk bending the plastic while it's still hot.
9. Clean up, and turn the printer off.

Slic3r Config
-------------

The easiest way I've found to work with a Slic3r config from this repository is to just create a symbolic link. For example:

```
ln -s ~/src/thing-o-matic/Slic3r ~/Library/Application\ Support/Slic3r
```

Now you should see some aptly named presets in Slic3r. Use the "Scanbot HQ" (high quality) print settings, "Plain ABS" filament, and the "Scanbot" printer. If you modify the settings in Slic3r, you can check them back into git and submit a push request.

What to watch out for
---------------------

The most common failure is for the pinch wheel to tear a hole in the plastic filament instead of pushing it. This could mean that the extruder is too cold, the feed rate is too fast, or the printer just doesn't like the cut of your jib. The 0.25mm nozzle is beautiful when it works, but it can be temperamental.

If this happens, you'll need to manually control the printer using Pronterface to heat the barrel, run the extruder backwards, trim the stripped portion of filament, then reload it.

There are plenty of other failure modes possible. There are really no safety features on this printer, so if there's a software bug or the thermostat fails, it's quite possible for it to light your ABS filament on fire. This is bad. Try not to let this happen.

FAQ
---

Can I use this with ReplicatorG? Not easily. The stock Makerbot firmware is kind of terrible and doesn't handle stepper extruders especially well. The ScribbleJ firmware is designed for a Reprap-style toolchain. It's probably possible to use ReplicatorG, but Reprap tools like Pronterface and Slic3r were easier to adapt to this printer's oddball configuration.

Should I use the "Exhaust" fan on the side of the printer? Probably not. It tends to cool models faster than necessary, reducing layer adhesion. I tend to only use it after the model has finished printing, if at all.

Can I print directly over USB rather than over SD card? Maybe. I don't, because the FTDI drivers for Mac OS are terrible. Your mileage may vary, but I've had problems with the print stuttering due to uneven througput over the USB port. The SD card is much more reliable, if a bit clunky. But on the bright side, you don't have to keep a computer tethered.

Can I control the printer manually, for maintenance purposes? Yes. Hook up a USB cable and use "Pronterface", the Reprap GUI tool.

How do I switch colors? Not easily.. you'll need to use Pronterface to back out the existing filament, then reload new filament. You need to do this with the extruder heated, and manually step the extruder forward enough to see the new filament extruding before you try a print. The spool box is a bit annoying to open, so I tend to just lay the filament coil near the printer when using other colors.

Who do I call when this shit breaks?
------------------------------------

Micah Elizabeth Scott, <beth@scanlime.org>

If you have any improvements to this documentation or the settings, pull requests would be much appreciated :)
