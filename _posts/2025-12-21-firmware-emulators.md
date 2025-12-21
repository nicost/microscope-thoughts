
---
title: "Firmware Emulators for Microscope Devices"
author: Nico Stuurman
date: 2025-12-21
---

My friends and I have talked now and then about the possibility of emulating microscope devices to facilitate developing code to interface with these devices and to test code (possibly in an automated way). Communication with many of these devices takes place through old-fashioned serial interfaces, where the protocol is often described in the manual or developer's documentation. Therefore, using an [Arduino](https://www.arduino.cc) (or other easily available and programmable micro-controller) for emulation is an attractive option.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/Arduino_Uno_-_R3.jpg/250px-Arduino_Uno_-_R3.jpg)

Writing such firmware code is tedious, and so far I had not gotten around to doing so. Encouraged by Curtis Rueden, I recently started using [Claude Code](https://claude.ai) in my coding work and like it quite a bit. The [Snout scope](https://calm.ucsf.edu/nic-equipment) at the [CALM at UCSF](https://calm.ucsf.edu) has a Prior stage controller that randomly locks up (i.e., it stops responding to serial commands and needs to be power cycled to regain communication), which made me contemplate completely rewriting the [Micro-Manager](https://micro-manager.org) Prior device adapter.

Combining these two thoughts, I prompted Claude to write Arduino firmware to emulate the Prior stage controller, letting it read the serial communication section of the Prior ProScan manual. Unprompted, it even produced a Python script to test the emulated device. The code compiled on the first try, was loaded onto an Arduino UNO using the Arduino IDE, and the test script passed all tests. I then tested it using the Micro-Manager UI and created a configuration file for the Prior XY and Z stage. I could create that config file, but on loading it there were a couple of errors. It turns out that the Arduino waits for about 2 seconds after the serial port opens before it starts running the firmware code. Adding a delay in the initialize function of the Micro-Manager Prior adapter worked around this problem. This is a somewhat fundamental limitation with this approach, unless you are OK giving up on convenience and disabling the ability to load firmware through the serial interface onto the board.

Next, I realized that setting XY positions resulted in the emulator going to that position immediately, rather than after a delay dictated by the speed setting. One more prompt to Claude and that behavior was included.

I created a [GitHub repo](https://github.com/nicost/Firmware_Emulators) and uploaded the code (I may look for a better place under the Micro-Manager repository). If anyone has other device emulators, please get in touch to increase visibility!

This was one of my most satisfying uses of AI to create code yet. Clearly, LLMs are well-poised to translate documentation into code that follows the spec. Now on to writing a new device adapter;)





