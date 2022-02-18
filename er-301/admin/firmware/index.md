---
layout: draft
title: Updating Firmware
parent: Admin
grand_parent: ER-301
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# How to update

{% include pitfall.html
content="Warning! In general, quicksaves and presets made with newer firmware versions are not backwards compatible."
%}

{% include pitfall.html
content="It is important that power to the ER-301 is not interrupted during the installation step or you will be left with corrupted files on your rear SD card."
%}

Unless there is a problem, you will always update the ER-301's firmware via the SD card on the front.  This means that there is no reason to remove the module from your case.  Furthermore, it is not necessary to power down during this firmware update procedure.

**Follow these 8 steps to change your ER-301's firmware:**
{% include gallery.html
count=8
file1="download.png"
caption1="Step 1: [Download](https://github.com/odevices/er-301/releases) the firmware (zip) file. (**Mac Users:** Your browser might automatically try to unzip the file for you when you download. To prevent this, please right-click and choose **Download Linked Files**.)"
file2="sd-card-reader.jpg"
caption2="Step 2: Copy the zip file (without unzipping) to the FRONT microSD card. Any location is fine but you might want to create a folder called 'firmware' so that you can easily find and move between different firmware versions."
file3="switch-eject.jpg"
caption3="Step 3: Make sure the STORAGE switch is in the EJECT position and insert the microSD card into the FRONT slot of the ER-301."
file4="switch-admin.jpg"
caption4="Step 4: Move the STORAGE switch from EJECT to ADMIN (i.e. mount the card)."
file5="screen.png"
caption5="Step 5: Navigate to the UPDATE FIRMWARE screen."
file6="press-update.png"
caption6="Step 6: Press UPDATE (S1)."
file7="select.png"
caption7="Step 7: Select the zip file that you downloaded and press ENTER. The selected firmware will be installed on your ER-301's rear SD card."
file8="reboot.png"
caption8="Step 8: Once the files are installed, press REBOOT (S3)."
%}

# Forward compatibility of presets and quicksaves

I am always doing my best to preserve forward compatibility of your saved work.  However, and this is especially true of the early firmware versions, sometimes in order to move forward with the road map I am forced to make breaking changes.


## v0.3

You can try but loading v0.2 presets and quicksaves will usually fail.

## v0.4

Partial support for v0.3 presets/quicksaves.  At the very least, you will need to copy and change the extension of the older *.lua files as follows:

* Unit presets: *.unit
* Chain presets: *.chain
* Quicksaves: *.save

## v0.5

No breaking changes.

## v0.6

Some changes in how local routings are stored.  Most presets and quicksaves are not affected but if you used a lot of complicated local routings then I would double check whether or not the connections are still there.

# Where are my units?

Starting in v0.6, units are installed as packages via the Package Manager.  This includes the factory-provided "core" units.  The firmware updater for v0.6 and forward has been updated to be aware of these packages.  However, previous firmware versions are not package-aware.  The result is that when you update to v0.6+ firmware from say v0.4 or v0.5 firmware, you will not have most of the core units installed.

In order to fix this, you just have to install the firmware again from inside the package-aware (i.e. v0.6+) firmware.  There are on-screen instructions that tell you to do this but some fail to notice them.

# Where are my quicksaves?

As long as you don't skip a minor version when updating, the firmware updater will attempt to copy your quicksaves over to the new firmware system folder on the front card: ```ER-301/v{major}.{minor}```.  However, this will not happen in the following situations:

* You skipped a minor version when updating.  For example you updated from v0.4.26 to v0.6.16 skipping v0.5.
* The system folder (```ER-301/v{major}.{minor}```) for the new version already exists.  This means you have already updated to this (major.minor) version in the past.

The workaround is to bring your front SD card over to a PC and copy:

```ER-301/v{old version}/quicksaves``` to ```ER-301/v{new version}/quicksaves```

Here is a concrete example.  You were working with v0.4.27 and then you updated to v0.6.16, skipping v0.5.  In order to manually bring your quicksaves over to the new version, you would copy as follows:

```ER-301/v0.4/quicksaves``` to ```ER-301/v0.6/quicksaves```