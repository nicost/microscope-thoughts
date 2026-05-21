---
title: "Half a year of progress in the Micro-Manager ecop system"
author: Nico Stuurman
date: 2026-06-20
---


# Faster progress on Micro-Manager development thanks to new AI coding tools

Like so many other software projects, Micro-Manager has benefitted enormously from the new AI coding tools.  Development is often faster than documenting, and to rectify that a bit I am planning to write a couple of posts about the new features in Micro-Manager.  For me, but also for you the reader, first a short overview of accomplishments in the last 6 months or so.

## Device Adapters added:
    - Evident IX85
    - Rapp UGA42 (plus Rapp lasers)
    - Spinnaker C (should be less depenedent on Spinnaker version, by Mark Tsuchia)
    - Utilities - StageState device (so that a linear stage can be used as a state device, by Mark Tsuchida)
    - Thorlabs TSP01 temperature sensor (by @aandreev0)
    - iSIMWaveForms (by Kyle Douglass)
    - ReflectorFocus: Focus maintennace device that needs a camera, shutter and stage in the configuration.

## User Interface added or expanded:
    - High Content Screening plugin: adds WellZoom window that shows zoomed in well including location of the stage within the well. 
    - MultiChannelShading: makes it possible to remember shading setting for different magnifictaions (i.e objective).
    - Added 3DSCript to the 3D (ClearVolume) viewer.  Also added a real editor that genrates a script from keyframwed.  Enables export to a movie using ffmpeg.
    - Adds support for 32bit (float) images in the viewer.
    - Adds Stitch plugin: automatically stitch acquisitions of multiple, overlapping positions.  Includes automated image flipping/rotation based on affine transform, alignment and blending.
    - Adds Explorer plugin, similar to SlideExplorer and MicroMagellen, but fully integrated with the Micro-Manager UI. Allows for export of stitched and blended images. 
    - Adds NavigationByMap: load a map of the sample, acquired anywhere at any resolution, set 3 points that correspond to locations on the current microscope and navigate to any position in the map.
    - iSIM plugin (by Kyle Douglass).
    - Deskew Explorer: Explorer for Snouty-type Light sheet microscopes, takes a volume at each position, projects and places in an Explorer.


I'll go into detail for a few of these issues in the near future.

