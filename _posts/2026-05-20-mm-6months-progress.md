---
title: "Half a year of progress in Micro-Manager development"
author: Nico Stuurman
date: 2026-05-20
---


# Faster progress on Micro-Manager development thanks to new AI coding tools

Like so many other software projects, [Micro-Manager](https://micro-manager.org) has benefitted enormously from the new AI coding tools.  Development is often faster than documenting, and to rectify that a bit I am planning to write a couple of posts about new features in Micro-Manager.  For me, but also for you the reader, first a short overview of accomplishments in the last 6 months or so.

## Device Adapters added:
- [Evident IX85](https://evidentscientific.com/en/products/inverted/ixplore-ix85)
- [Rapp UGA42](https://rapp-opto.com/products/photomanipulation-systems/scanner-based-photomanipulation-uga-42-series/) (plus Rapp lasers)
- [Spinnaker C](https://www.teledynevisionsolutions.com/products/spinnaker-sdk/?model=Spinnaker%20SDK&vertical=machine%20vision&segment=iis) (should be less dependent on Spinnaker version than the original Spinnaker adapter, by Mark Tsuchia)
- Utilities - StageState device (so that a linear stage can be used as a state device, by Mark Tsuchida)
- [Thorlabs TSP01](https://www.thorlabs.com/item/TSP01) temperature and humidity sensor (by @aandreev0)
- iSIMWaveForms (by Kyle Douglass)
- ReflectorFocus: Focus maintennace device that needs a camera, shutter and stage in the configuration.

## User Interface added or expanded:
- High Content Screening plugin: adds WellZoom window that shows zoomed in well including location of the stage within the well. 
- MultiChannelShading: makes it possible to remember shading settings for different magnifications (i.e for different objectives).
- Added 3DScript to the 3D (ClearVolume) viewer.  Also added a reel editor that generates a script from keyframes.  Enables export to a movie using ffmpeg.
- Adds support for 32bit (float) images in the viewer.
- Much better support of RGB images in the viewer, including various facilities to set white and black point.
- Adds Stitch plugin: automatically stitch acquisitions of multiple, overlapping positions.  Includes automated image flipping/rotation based on affine transform, alignment and blending.
- Adds Explorer plugin, similar to SlideExplorer and MicroMagellan, but fully integrated with the Micro-Manager UI. Allows for export of stitched and blended images. 
- Adds NavigationByMap: load a map of the sample, acquired anywhere at any resolution, set 3 points that correspond to locations on the current microscope and navigate to any position in the map.
- iSIM plugin (by Kyle Douglass).
- Deskew Explorer: Explorer for Snouty-type Light sheet microscopes, takes a volume at each position, projects and places in an Explorer.


I'll go into detail for a few of these new features in the near future.

