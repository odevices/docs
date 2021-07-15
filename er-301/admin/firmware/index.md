---
layout: default
title: Updating Firmware
parent: Admin
grand_parent: ER-301
---

# {{page.title}}

{% include pitfall.html
content="Warning! There is a possibility that quicksaves and presets made with newer firmware versions are not backwards compatible. So to be safe you should make a copy of your ```ER-301/<version>``` directory before switching firmware.  In very old versions, this folder was called ```ER-301/sc```."
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

{% include pitfall.html
content="It is important that power to the ER-301 is not interrupted during the installation step or you will be left with corrupted files on your rear SD card.  If this happens see the advanced method (below) for how to restore your rear SD card to a bootable state."
%}

{% include pitfall.html
content="If you have v0.4.20 installed then this procedure will fail because the builtin firmware updater is broken in this version.  Please use the Advanced Method below instead."
%}
