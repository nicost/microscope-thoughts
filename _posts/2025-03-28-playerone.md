---
title: "PlayerOne"
date: 2025-03-28
---

The [Sony STARVIS and STARVIS2](https://www.sony-semicon.com/en/technology/security/index.html) image sensors are back-illuminated sensors with high QE and low readnoise (where the STARVIS2 apparently increased full well depth).  Even though these sensors appear to be marketed towards security cameras, they should make great sensors for astronmy and microscopy applications.  

I do not know if any companies marketing cameras containing these sensors directly for microscopy applications, but there are plenty for the amateur astronomy market.  These are all cooled (enabling longer exposures) and should work finr flr fluorescense microscopy as well.  I am aware of a few companies selling these, and it appears they are all actually manufactured by the company [Touptek](https://www.touptekphotonics.com/) and then repackaged for other companies.  [Micro-Manager](https://micro-manager.org) has support for [ZWO](https://www.zwoastro.com/) and as of recently, [PlayerOne](https://player-one-astronomy.com/) cameras.  I was curious how well these cameras would work and convined one of our faculty to order one to improve their epi-fluorescence microscope.

We settled on the [PlayerOne ARES-M Pro](https://player-one-astronomy.com/product/ares-m-pro-usb3-0-mono-camera-imx533/) camera.  This has about 9M pixels that are 3.76 micron squared each, it has a maximum QE of 91%, and a read-noise close to 1 electron.  We ordered one of these plus a power supply from PlayerOne, and a [M42 to C-Mount adapter from Amazon](https://www.amazon.com/Adapter-Connection-Microscope-Industrial-Accessories/dp/B0D83S2TM7?gQT=0&th=1).  Total cost was less than $1,100.

I tested the camera first and should have taken some pictures of the camera, Micro-Manager properties of the camera, as well as images taken with the camera, but I forgot.  The PlayerOne programmers (who contributed the Micro-Manager device adpater code March 2024) had done a great job.  The Micro-Manager website has [instructions](https://micro-manager.org/PlayerOne) on getting the camera to work.  After configuration, all relevant properties showed up in the MM Property Browser.  You can switch the cooler on and off, set a target temperature, and even control the anti-dew heater.  The camera gain is an important parameter.  For fluorescence, you likely will want to run the camera at a gain of 125, which yields a read-out noise of ~1.4e, but has a higher dynamic range than what you get at the highest gaion (with lowest read-noise).  

These specifications at this price point are truely remarkable.  The only thing missing is the ability to externally trigger the camera and a TTL signal from the camera signalling that the camera is exposing.  
