---
title: "Using a Decompiler to change the MM Device Interface Version"
author: Nico Stuurman
date: 2025-05-09
---

Some companies (like Cairn and Mightex, but there are others) wrote device adapters for their equipment but did not share the source code with the Micro-Manager team.  Therefore, you need to ask these companies for the binary device adapter (or if your are lucky, download from their website). This works until the device interface version changes. When changes are made to the device interface, the Micro-Manager team changes the device interface version.  At runtime, the Micro-Manager Core demands an exact version match between its device interface version and the device interface version of the device adapter.  This is done to avoid crashes of the application, for instance by calling functions in the device adapter that do not exist.  

Even though it makes sense to demand an exact device interface match, it can happen that it is perfectly safe to change the device interface version of a device adapter as long as you are sure that nothing affecting this specific device adapter was changed during the change in device interface version.  You can check this by checking the git logs of the [Micro-Manager Core and Device Github repository](https://github.com/micro-manager/mmCoreAndDevices), or you can try and see if things work or crash.

So, how can you change the device interface version of a Micro-Manager Device Adapter?

First check the Device Interface version of the Micro-Manager version that you are running.  Go to the Micro-Manager Help menu item "About Micro-Manager".  

![](/microscope-thoughts/media/AboutMM.png)

Look for "Device API version", which here is 73.

If your device adapter has another version, it will not show up in the Hardware Configuration Wizard at all.  When you open the Corelog file, you can find lines with the following text:
```2025-05-09T11:36:02.920432 tid11308 [IFO,App] Cairn_Optospin
2025-05-09T11:36:02.921563 tid11308 [IFO,App] Error: Unable to load Cairn_Optospin library: Failed to load device adapter "Cairn_Optospin" from "C:\Program Files\Micro-Manager-2.0\mmgr_dal_Cairn_Optospin.dll" [ Incompatible device interface version (required = 73; found = 71) ]
```
So, we need to change the device interface version of the Cairn_Optospin from 71 to 73. Mark Tsuchida assured me that the only thing that changed was the addition of support for pump devices.  Since the OptoSpin is not a pump, it should be safe to hack the binary to increase the device interface version.

Here, we use the Open Source Decompiler tool [Cutter](https://cutter.re/).  Download the application and extract the zip file.  Launch by double clicking "Cutter.exe" within the unzipped archive. 

IMPORTANT! Before you start, make sure that you have a copy of the original device adapter file somewhere.

On the startup screen, select the file you want to edit .

![](/microscope-thoughts/media/CutterOpenFile.png)

On the next screen, check "Load in write mode(-w)". 

![](/microscope-thoughts/media/CutterLoadWrite.png).

The screen should look something like this:

![](/microscope-thoughts/media/Cutter1.png).

On the left side (all the stuff labeled "fcn", scroll down looking for "sym.mmgr_dal_Cairn_Optospin.dll_GetDeviceINterfaceVersion.  Double click on that line.  

![](/microscope-thoughts/media/Cutter2.png).

In the right side panel, click on the line just below "GetDeviceInterfaceVersion()".  From the menu select "edit" > "bytes".  Here, that has the value "b847000000".  The "47" is hexadecimal for 71.  Change the 7 into a 9, click OK, and you are done.  


![](/microscope-thoughts/media/Cutter3.png).

Exit Cutter (you can Discard you changes, as those changes would be saved to a Cutter project, your own changes are already saved.

When you now open Micro-Manager and enter the Hardware Configuration Wizard, the device should show up.

![](/microscope-thoughts/media/MM_HCW_Cairn.png)

Good luck!
