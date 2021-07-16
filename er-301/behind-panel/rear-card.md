---
layout: default
title: Rear SD Card
parent: Behind the Panel
grand_parent: ER-301
---

The rear SD card holds the firmware, bootloaders, and some system configuration data.  The contents of the SD card are completely managed by the system.  Therefore, under normal circumstances, the user will not need to touch these files.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# Manual firmware update
You can accomplish a firmware update by directly copying the system files to the rear SD card using your computer.  

{% include pitfall.html
content="You would only use this method if the builtin [Firmware Updater](/er-301/admin/firmware) fails for some reason."
%}

1. Power down your case and remove the ER-301 so that you can get at the rear SD card.
1. Remove the rear SD card and take it over to your computer.
1. Unzip the downloaded firmware archive file to find three files: **MLO, SBL, and kernel.bin**.
1. Copy these 3 files to the root directory of the rear SD card.  It is OK to overwrite any existing files of the same name.
1. Make sure to follow the proper procedure for ejecting an SD card for your computer's OS.  There is a chance you will corrupt your SD card if you simply pull out the SD card from the card reader without first unmounting it.
1. Place the SD card back into the card slot on the rear of your ER-301.
1. Install your ER-301 back into your case and power up.
1. Your ER-301 should now successfully boot up and thus allow you to complete a full firmware update via the front card as usual.

# Preparing a new card from scratch
First make sure you have a card that satisfies these requirements:
* FAT32-formatted SD card (up to 32GB) 
* Class 10 speed or better.

Then, you will need to copy the contents of the firmware archive to this card and set the first partition as active so that it can be used for booting.

Here is a Linux script that can be used to perform the necessary operations:

```bash
#!/bin/bash

########################
# IMPORTANT: Change these to match your situation!
FIRMWARE_PATH="er-301-v0.6.14-stable.zip"
CARD_DEVICE="/dev/mmcblk0"
CARD_PARTITION="/dev/mmcblk0p1"
########################

CARD_PATH=`findmnt --source ${CARD_PARTITION} --noheadings --output TARGET`
LABEL="ER301-REAR"

echo "The $CARD_PARTITION is mounted at $CARD_PATH."
echo "Firmware Source: $FIRMWARE_PATH"
echo "Performing filesystem check"
sudo fsck.fat -a ${CARD_PARTITION}
unzip $FIRMWARE_PATH -d $CARD_PATH
sync
echo "Setting volume label to $LABEL."
sudo fatlabel ${CARD_PARTITION} $LABEL
echo "Setting boot flag on partition 1."
sudo parted --script $CARD_DEVICE set 1 boot on
sync
echo "Done."
```


