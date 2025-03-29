---
title: "PlayerOne cooled CMOS camera"
author: Nico Stuurman
date: 2025-03-28
---

The [Sony STARVIS and STARVIS2](https://www.sony-semicon.com/en/technology/security/index.html) image sensors are back-illuminated, have high QE and low readnoise (where STARVIS2 increases full well depth over STARVIS).  Even though these sensors are marketed towards security cameras, they should make great sensors for astronomy and microscopy applications.  

I do not know if any companies marketing cameras containing STARVIS sensors directly for microscopy applications, but there are plenty for the amateur astronomy market.  These are all cooled (enabling longer exposures) and should work fine for fluorescense microscopy as well.  I am aware of a few companies selling these, and it appears they are all manufactured by the company [Touptek](https://www.touptekphotonics.com/) and then repackaged for these other companies.  [Micro-Manager](https://micro-manager.org) has support for [ZWO](https://www.zwoastro.com/) and as of recently, [PlayerOne](https://player-one-astronomy.com/) cameras.  I was curious how well these would work and convinced one of our faculty to order one to improve their epi-fluorescence microscope.

We settled on the [PlayerOne ARES-M Pro](https://player-one-astronomy.com/product/ares-m-pro-usb3-0-mono-camera-imx533/) camera.  This has about 9M pixels that are 3.76 micron squared each, it has a maximum QE of 91%, and read-noise close to 1 electron.  We ordered one of these plus a power supply from PlayerOne, and a [M42 to C-Mount adapter from Amazon](https://www.amazon.com/Adapter-Connection-Microscope-Industrial-Accessories/dp/B0D83S2TM7?gQT=0&th=1).  Total cost was less than $1,100.

![](/microscope-thoughts/media/ARES_M_Pro.jpg)

I tested the camera first at my desk and should have taken some pictures of the camera, Micro-Manager properties, as well as images taken with the camera, but I forgot.  The PlayerOne programmers (who contributed the Micro-Manager device adpater code March 2024) had done a great job.  The Micro-Manager website has [instructions](https://micro-manager.org/PlayerOne) on getting the camera to work.  After configuration, all relevant properties showed up in the MM Property Browser.  You can switch the cooler on and off, set a target temperature, and even control the anti-dew heater.  The camera gain is an important parameter.  For fluorescence, you likely will want to run the camera at a gain of 125, which yields a read-out noise of ~1.4e, but has a higher dynamic range than what you get at the highest gaion (with lowest read-noise).  Only thing I did not find was a way to switch between Normal mode (slightly higher read-noise but faster), and LRN mode (lowest read-noise but also lower frames per second).


The camera mounted easily to the microscope (using the C-Mount adapter) and with a diameter of about 16mm fills a significant fraction of the field of view of most microscopes.  The small pixel size means that you will get full resolution out of high na, low mag objectives (but always do the calculations for your specific setup). Images at the scope looked good, and it was easy to configure the whole system.  Only glitch was a single crash during live mode.  Most likely an uncaught C++ excpetion, I'll need to debug that if it happens more often. 

These specifications at this price point are truely remarkable.  The only thing missing is the ability to externally trigger the camera and a TTL signal from the camera signalling that the camera is exposing.  

Regretfully the camera is already doing its work at the microscope.  I'd love to spend some more time with one of these to measure electron conversion factor myself, as well as make a per-pixel gain map.  

Overall conclusion: These cameras are a significant upgrade from machine vision cameras for most microscopes, and are at a similar (low) price point.  What is not to like?

