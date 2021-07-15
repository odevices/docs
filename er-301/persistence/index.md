---
layout: default
title: Persistence
parent: ER-301
nav_order: 3
---

Here we discuss the various mechanisms by which the ER-301 helps you save and recall your creations.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# SD Card 
The SD card slot on the front of the ER-301 is used to hold all of the data that belongs to the user such as samples and presets.  There is an additional SD card slot on the back of the module but this one is reserved for system use (e.g. firmware and system settings) and does not need to be accessed by the user during regular use.

## Requirements 
* Accepts micro SD (uSD) cards.
* Any [speed class](https://en.wikipedia.org/wiki/SD_card#Class), but Class 10 (C10) and above is recommended.

## Mounting and ejecting 
{% include figure.html
  file="storage-switch-eject.jpg"
  caption="You can remove or insert the SD card when the **safe** LED is lit."
%}
The STORAGE toggle switch next to the SD card slot can be used to safely eject and mount a card.  

To mount a card:
1. Make sure the STORAGE switch is in the eject position and the safe LED is lit.
1. Insert the card.
1. Move the STORAGE switch from the eject position to either admin or user.

To eject a card:

1. Move the STORAGE switch to the eject position.
1. If no files are actively being accessed, then the safe LED will light up and it is now safe to remove the card.
1. If files are actively being accessed, then the safe LED will NOT light up and you should NOT remove the card.  A list of active files that are preventing the ejection will be displayed.


# Quicksave 
A quicksave stores *all* of the essential state of the ER-301 in one place for recalling later, such as:  
* Channel grouping
* OUT1-OUT4 chains and contained units
* Pinned controls
* Global chains and contained units
* Multitrack recorder configuration
* Sample pool contents (links only)
* Mute state of OUT1-OUT4 chains
* Contents of the Recents category in the Unit Chooser

{% include pitfall.html
  content="**Admin > System Settings**<br>These configuration settings are stored on the rear SD card.  So they are completely independent of the front SD card and thus independent of the quicksaves."
%}

At anytime and anywhere, pressing SHIFT+M1 (silkscreened as QUICKSAVE) will bring up the (modal) quicksave screen.  The last quicksave slot that was loaded or saved will be highlighted.  Pressing CANCEL will allow you to leave the screen without any effect.  Highlight the desired quicksave slot with the knob and/or M soft buttons.  Once highlighted, the sub display shows a summary of the contents of the quicksave slot, as well as 3 commands:
* **save** (S1): store the current state to the highlighted slot.
* **rename** (S2): edit the name of the highlighted slot.  Press CANCEL to leave the rename screen without changing the slot's name and press ENTER to set the new name of the slot.
* **load** (S3): restore the contents of the highlighted slot.

{% include gallery.html
  count=3
  file1="quicksave-screen.png"
  caption1="The quicksave screen shows 24 slots where you can store and recall the state of the ER-301."
  file2="renaming-quicksave.png"
  caption2="Renaming a quicksave slot."
  file3="renamed-quicksave.png"
  caption3="The quicksave slot after renaming."
%}

{% include tip.html
content="**Quicksaves as Templates** <br> In addition to using quicksaves to save your ''completed'' patches, it is also very useful to use quicksaves to put the ER-301 into a convenient state for creating a new patch."
%}

{% include tip.html
content="**Restore last quicksave on boot?** <br> There is a setting in Admin>Settings where you can choose to have the last accessed quicksave automatically recalled when powering up the ER-301."
%}

Quicksaves are saved to a folder called ```ER-301/sc/quicksaves```.  Inside this folder, there is a folder for each slot (e.g. slot1, slot2, and so on).  This slot folder contains up to 4 files (e.g. Q01.save to Q04.save). The most recent quicksave data saved to this slot will be Q01.save, whereas the previous 3 saves will be in Q02.save to Q04.save as backups."

Quicksaves (in fact **all** presets) are serialized as loadable Lua code which defines a table containing all of the data pertinent to the preset.  Although should never be necessary, with some practice and knowledge of Lua, it is possible to edit these files by hand.

# Chain Presets
[Chains of units](/er-301/chains) are stored as chain presets for later recall.  A chain preset consists of:
* a list of unit presets (one for each unit in the chain)
* the [source](/er-301/chains/#source) assignment (if applicable)
* the location of the focus cursor

You can create a chain preset from any chain by focusing the chain's header to get access to its header menu and pressing **Save (S3)**.  To load a chain preset into a given chain, again focus the chain's header but this time press **Load (S2)** and select a chain preset file via the file browser screen.  The current contents of the chain will be replaced by the units contained within the chain preset.

{% include gallery.html
  count=2
  file1="/er-301/chains/mono-chain-header.png"
  caption1="When the chain header is focused a menu of chain operations is shown in the sub-display."
  file2="/er-301/chains/chain-presets-folder.png"
  caption2="Pressing a chain's **Save** command will bring you to this screen where you can specify the destination file for the chain preset."
%}

Chain presets are saved to a folder called ```ER-301/<version>/presets/chains``` by default but you can save them anywhere you like.  A chain's Load and Save commands will open by default to this folder so it might be easier to keep your chain presets there.  

# Unit Presets
The complete state of an individual [unit](/er-301/units) can be stored in and recalled from a unit preset.  A unit preset will persist the following items:
* the values of all parameters
* fine vs coarse setting of each parameter
* sub-chains of parameters that have them
* the name of the unit (if renamed)
* bypassed or not

{% include gallery.html
  count=2
  file1="/er-301/units/unit-menu.png"
  caption1="The preset load/save commands are located in a unit's extended menu, accessed by focusing the unit's header."
  file2="/er-301/units/save-unit.png"
  caption2="Pressing **Save Preset** will bring you to this screen where you can specify the destination file for the unit preset."
%}

You can create a unit preset from any unit by pressing the M soft button beneath its header (i.e. focusing the header) to reveal the "Save Preset" command (among other commands).  Pressing the M soft button underneath "Save Preset" command will open a file saving screen where you can choose an existing file (to overwrite) or create a new file.  Later you can load this preset into an existing unit (of the same type) by using the "Load Preset" command.

# Global Chains Presets
You can save and later recall all of your global chains using global chain presets.  Simply, focus the global chain header to reveal the "Load Chains" (S2) and "Save Chains" (S3) commands.

{% include gallery.html
  count=2
  file1="/er-301/admin/globals/menu.png"
  caption1="Hovering over (or focusing) the area all the way to the left, will reveal 3 commands in the sub display."
  file2="/er-301/admin/globals/save.png"
  caption2="Activating the **Save Chains** command will bring us to this screen where we can choose an existing destination file or create a new one."
%}

{% include tip.html
  content="To load individual chains into the global chain area, just create a chain of the desired type (mono vs stereo) and then use its **Load** command to populate it via a chain preset."
%}

# Multitrack Recorder Presets
{% include gallery.html
  count=2
  file1="/er-301/admin/multitrack/screen.png"
  caption1="The Multitrack recorder has its load/save preset commands available in the sub display when you are configuring its channels."
  file2="/er-301/admin/multitrack/load-preset.png"
  caption2="Pressing the **Load Preset** button will bring you to this screen where you can select a previously saved configuration preset."
%}
