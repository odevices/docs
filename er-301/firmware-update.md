---
layout: default
title: Updating Firmware
parent: ER-301
nav_order: 8
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

{% include pitfall.html
content="Warning! There is a possibility that quicksaves and presets made with newer firmware versions are not backwards compatible. So to be safe you should make a copy of your ```ER-301/<version>``` directory before switching firmware.  In very old versions, this folder was called ```ER-301/sc```."
%}

# Easy Method 
Unless there is a problem, you will always update the ER-301's firmware via the SD card on the front.  This means that there is no reason to remove the module from your case.  Furthermore, it is not necessary to power down during this firmware update procedure.

**Follow these 8 steps to change your ER-301's firmware:**
{% include gallery.html
count=8
file1="er-301/firmware/download.png"
caption1="Step 1: [Download](https://github.com/odevices/er-301/releases) the firmware (zip) file. (**Mac Users:** Your browser might automatically try to unzip the file for you when you download. To prevent this, please right-click and choose **Download Linked Files**.)"
file2="er-301/firmware/sd-card-reader.jpg"
caption2="Step 2: Copy the zip file (without unzipping) to the FRONT microSD card. Any location is fine but you might want to create a folder called 'firmware' so that you can easily find and move between different firmware versions."
file3="er-301/firmware/switch-eject.jpg"
caption3="Step 3: Make sure the STORAGE switch is in the EJECT position and insert the microSD card into the FRONT slot of the ER-301."
file4="er-301/firmware/switch-admin.jpg"
caption4="Step 4: Move the STORAGE switch from EJECT to ADMIN (i.e. mount the card)."
file5="er-301/firmware/screen.png"
caption5="Step 5: Navigate to the UPDATE FIRMWARE screen."
file6="er-301/firmware/press-update.png"
caption6="Step 6: Press UPDATE (S1)."
file7="er-301/firmware/select.png"
caption7="Step 7: Select the zip file that you downloaded and press ENTER. The selected firmware will be installed on your ER-301's rear SD card."
file8="er-301/firmware/reboot.png"
caption8="Step 8: Once the files are installed, press REBOOT (S3)."
%}

{% include pitfall.html
content="It is important that power to the ER-301 is not interrupted during the installation step or you will be left with corrupted files on your rear SD card.  If this happens see the advanced method (below) for how to restore your rear SD card to a bootable state."
%}

{% include pitfall.html
content="If you have v0.4.20 installed then this procedure will fail because the builtin firmware updater is broken in this version.  Please use the Advanced Method below instead."
%}

# Advanced Method 
You can also accomplish a firmware update by directly copying the system files to the rear SD card using your computer.  Use this method when you are unable to boot into the ER-301's operating system or you are unable to get the ER-301 to recognize (i.e. mount) your front SD card.

1. Power down your case and remove the ER-301 so that you can get at the rear SD card.
1. Remove the rear SD card and take it over to your computer.
1. Unzip the downloaded firmware archive file to find three files: **MLO, SBL, and kernel.bin**.
1. Copy these 3 files to the root directory of the rear SD card.  It is OK to overwrite any existing files of the same name.
1. Make sure to follow the proper procedure for ejecting an SD card for your computer's OS.  There is a chance you will corrupt your SD card if you simply pull out the SD card from the card reader without first unmounting it.
1. Place the SD card back into the card slot on the rear of your ER-301.
1. Install your ER-301 back into your case and power up.

# Making your rear SD card bootable 
If for some reason you are unable to use the rear SD card that came with your unit, in addition to the steps outlined in the advanced method, you will need to make the new SD card 'bootable'.  In technical terms, you will be marking the first partition on your card as active.

On a Windows PC:
1. Insert the SD card into your computer's card reader.
1. Type 'diskpart' at the command prompt.
1. Type 'list disks' at the new prompt, and note the index of the SD card.
1. Type 'select disk <index>' where <index> should be replaced by the index number determined in the previous step.
1. Next type 'select partition 1' to select the first partition.
1. Finally type 'active' to mark the first partition as active.
1. You may now unmount the SD card and remove it from the card reader.

On a Mac computer the process of making an SD card bootable is difficult, so instead try flashing a bootable disk image to the SD card as described in the next section.

# Restoring your rear SD card from a disk image 
Here are bootable disk images for 8GB and 4GB SD cards:
* [er-301-v0.2.18-image-8GB.zip](http://www.orthogonaldevices.com/files/er-301-v0.2.18-image-8GB.zip?attredirects=0&d=1)
* [er-301-v0.2.18-image-4GB.zip](http://www.orthogonaldevices.com/files/er-301-v0.2.18-image-4GB.zip?attredirects=0&d=1)

Download this file and unzip to your computer.  Write the contained img file to your SD card.  You can find an excellent detailed tutorial on how to do this over on SparkFun:
[SparkFun: SD Cards and Writing Images](https://learn.sparkfun.com/tutorials/sd-cards-and-writing-images)

Or if you prefer to jump to the chase, here are some tools that will get the job done:
* Mac: [ApplePi-Baker](https://www.tweaking4all.com/hardware/raspberry-pi/macosx-apple-pi-baker/)
* Windows: [Win32DiskImager](https://sourceforge.net/projects/win32diskimager/)
