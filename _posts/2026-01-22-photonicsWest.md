---
title: "Photonics West 2026 impressions"
author: Nico Stuurman
date: 2026-01-22
---

The [Photonics West](https://spie.org/conferences-and-exhibitions/photonics-west) conference includes a gigantic tradeshow spanning 2 halls of the Moscone Center and some of the space in between. I visited on two consecutive afternoon, trying to at least walk by every booth, and picking up on interesting new and/or affordable technologies useful for our [imaging core](https://calm.ucsf.edu).  So, this is an extremely subjective and quite random summary of things that I would like to remember:

- Vialux.  Their new [Prime Core](https://www.vialux.de/ViALUX-Website/modular-dlp-technology-optics.html) provides on axis illumination for a DLP.  It can be combined with any of the DLPs they carry.  This could work quite well for integration with a microscope, you would basically need to figiure out how to mount it to the back port of a scope (needs a lens analogous to the tube lens in the camera path) and how to pipe in the light source.  The light entrance is a ~ 2x2 mm window behind which the light is homogenized, so just putting some kind of fiber or light guide real close to that window should work.  The unit is ~$12k, the most affordablce DLP is $7k.  You could possibly use one of ther LEDs, but a full 6-7 line LED illuminator can be bought for ~$15k, so for $34k plus lenses and mounting hardware you would have a fully controllable DMD attached to your microscope.

- [QubeDot](https://qubedot.com).  Startup our of Germinay that knows how to make microLEDs and can design arrays at sizes up to 1 x 1cm and emitter sizes of 1-1000 microns, with all pixels individually controllable (i.e. you can send images to these things).  Many wavelengths are possible.  These things could be very interesting to project images into the microscope as an alternative to DLPs.  It all depends on the price point, and that will likely depend on volume, so I hope that someone will take this on and couple these to the illumination path of a microscope. 

- [Refined](https://refined-lasers.com/application/) has solutions for Coherent Raman scattering and CARS imaging.  I have no direct need, but do not want to forget about this.

- Likewise, [Specto](https://spectophotonics.com/) has products to enable / facilitate Brillouin Spectrometry / Microscopy.

- [Pi Imaging](https://piimaging.com) makes SPAD arrays and cameras based on SPAD arrays.  They have a 1k x 1k array with 16 micron pitch APDs build in a camera that is price competitive with high end scientific garde CMOS cameras.  The readout is a little different here as they do single photon counting and read out binary images with an integration time of 100ns (I hope I remembered this number correctly). So, a 1 ms "exposure" would consist of 10,000 binary images of 100ns integration each and the dynamic range would be 1:10,000.  The dark count rate is 100counts per second, but I am not sure if this is per APD or for the whole array.  Even if it is per APD, the average dark count for the 1 ms exposure would be 0.1, so these things basically have no background.  Also, they do global shutter exposure, so no more waiting for that rolling shutter to reach the whole Region of Interest.  They are clearly aware that we would like more and smaller AODs, so it looks like we will have a low noise future in imaging.

- [FLIM Labs](https://flimlabs.com) develops harwdare to make FLIM accessible to everyone.  the person I talked to (Alessandro?) came from Enrico Gratton's lab.  A combination of FLIM Data acquisition card, Picosecond-pulsed laser and SPDA Single-photon detector costs ~$18k.  All you would need to convert an existing microscope into a FLIM capable system is a glavo scanning unit.  I am very tempted to buidl something with this to bring FLIM capabilities to our core.

- Black materials are always fun (who has the blackest black?). [Koyo Orient](https://the-black-market.com) from Japan (b.t.w, I love that web-address!) has very dark materials and paint.  They gave me a sample with maximum of 0.3% reflectivity that costs about $30 per square meter.

- [Zaber](https://www.zaber.com/) has a system with an automated microscope, plate hotel and robot arm to feed the microscope for something significantly under $50k.  It should fit in an incubator and would make an awesome live cell automated imaging platform.  They have a laser autofocus for their microscope as well.  They work very well with Micro-Manager.

- [Omicron](https://omicron-laser.de) makes lasers and laser combiners taht also workj well with Micro-Manager.  They have nice compact 4 and 6 laser launches that are quite affordable. Laser Light engine for epi-fluorescence, LED illuminator

- [FingerLakesr]() Has a Filter Wheel again!

- [Hamamatsu]() Light source

- [Excelitas]() Was PCO.  New camera with sunukar specs as the Hamamatsu Quest2 (based on the same chip).  Also showed: 
    - Image Splitter
    - Wavelength scanning devices


- [Alibanal]() groups: Laser shutters


