---
layout: default
title: Front Panel
parent: ER-301
---

{% include figure.html 
  file="er-301-panel-annotated.png" 
%}

# Overview 
Here I describe the various elements present on the 30hp front panel of the ER-301.  

**Panel Flavors**<br>
As with all of my modules, I offer 3 flavors of panels: Original Flavor, Nostalgia and People's Choice.  You can see photos of these different panel types here: [Photos of Panel Flavors](http://www.orthogonaldevices.com/er-301/panels)  

 **Panel Design Data**<br>
Also, if you wish to make your own custom panel you can download the panel design data from here: [ER-301 Panel Design Data](http://www.orthogonaldevices.com/files/er-301-panel-rev2.zip?attredirects=0&d=1)

# The Knob
{% include figure.html
  file="er-301-knob.png"
  caption="A context-sensitive knob to handle all parameter adjustments."
%} 
The Knob is an endless encoder with a resolution of 100 pulses per revolution and a very long-life of more than 1 million revolutions.  The two main purposes of the Knob are scrolling through the UI and setting parameters.  The Knob's focus is always indicated by the dancing cursor which depending on the situation might be selecting something in the Main Display or the Sub Display.

The Knob's sensitivity can be toggled via the nearby fine/coarse button (aka KNOBMODE button).  The exact meaning of fine vs coarse will depend on the type of parameter that is being manipulated.

 **Super Fine** and  **Super Coarse**: Holding SHIFT while turning the knob will accentuate the fine or coarse setting.  In other words, if you are in fine mode then holding SHIFT will make the adjustments even more fine (generally 10 times more fine).  If you are in coarse mode then holding SHIFT will make the adjustments even more coarse (generally 10 times more coarse).
<br clear=all>

# Main and Sub Displays 
[There are two OLED displays on the ER-301: a Main Display and a Sub Display.  The Main Display is where most of the action occurs while the Sub Display provides context for whatever is focused in the Main Display.  The Main Display contains 256x64 4-bit monochrome pixels or 16 levels of brightness.  The Sub Display features 128x64 1-bit pixels, thus pixels are only either on or off.

<br clear = all>

# Soft Buttons 
[[File:er-301-soft-buttons.png|thumb|300px|The ER-301 has 9 soft buttons: M1-M6 and S1-S3. Each soft button is associated with a vertical column on the display above it.]([File:0001.png|thumb]])]

Soft buttons do not have fixed functions.  The effect of pressing a soft button will change depending on what is displayed on the screen above it.  The ER-301 has 9 soft buttons: 6 underneath the Main Display and 3 underneath the Sub Display.  For this reason, the Main Display is naturally divided into 6 vertical columns and the Sub Display is divided into 3 vertical columns; one column above each soft button.

The result of pressing a soft button will depend on the context but in a sensible (and hopefully self-evident) manner.  The following examples cover pretty much all of the types of scenarios that you might encounter:

*  **Focus** the knob to the item in the column above the button.
*  **Dive** down into a new screen.
*  **Perform** the operation indicated in the column above the button.
*  **Choose** an item from a (horizontal) list of items.
*  **Expand** or  **Collapse** the view of an item.

<br clear=all>

# Hard Buttons 
[ER-301 has 6 hard buttons whose basic functions are the same regardless of the UI context.]([File:er-301-hard-buttons.png|thumb|300px|The)]
{| class="wikitable" style="vertical-align:middle"
|style="width: 125px"|[|This button is called the KNOBMODE button.  It has 2 purposes depending on the context.

 **When a parameter control is focused**: This button is used to toggle knob sensitivity between fine and coarse settings.  

 **When a waveform display is focused:** This button is used to swap between time (horizontal) zoom or amplitude (vertical) zoom.  Hold this button down and turn the knob to zoom.  Press and release to switch between horizontal and vertical zooming.
|-
|style="width: 125px"|[[File:er-301-cancel-button.png|left]([File:er-301-fine-coarse-button.png|left]])]
|Used to abort an action. In general, it is the opposite of the ENTER button.  Also, pressing CANCEL right after changing the value of a parameter with the knob, will return the parameter to its original value.
|-
|style="width: 125px"|[|The HOME button reverts encoder focus to the "beginning" or "top" of the construct that is currently focused.  For example, if you are focused inside a unit then pressing the HOME button will shift the focus to the unit's header area.  If you press HOME again, then the focus shifts to the chain's header area, and so on.  Holding SHIFT while pressing the HOME button will zero out a focused parameter.
|-
|style="width: 125px"|[[File:er-301-enter-button.png|left]([File:er-301-home-button.png|left]])]
|The ENTER button confirms a selection or operation.  This is not to be confused with focusing an item which is always done via the soft buttons.  For example, choosing a sample to load in the file browser or, during unit renaming, committing text that you just typed as the new name of a unit.

The ENTER button can also be used to cycle through the available views of a highlighted unit or control.
|-
|style="width: 125px"|[|Whenever you have focused an item (for manipulation) or dived into a new area (such as a modulation chain of a unit) you can return to the previous focus by pressing this UP button.  It is very much like the BACK button a modern web browser.
|-
|style="width: 125px"|[[File:er-301-shift-button.png|left]([File:er-301-up-button.png|left]])]
|The SHIFT button is used to access alternate functions that some buttons have.  These will be noted as they come up in the documentation.
|}
<br clear=all>

# Channel Buttons 

[are 4 channel buttons, one for each output channel.]([File:er-301-channel-buttons.png|thumb|There)]

Pressing a Channel button (while in User mode) focuses the corresponding channel.  The currently focused channel is indicated by one of the orange LEDs next to each Channel button. This will also focus the output chain associated with the selected channel when in edit mode.  If the output chain is mono (i.e. the focused channel is not linked with another channel) then this is the only way to focus that chain.  Otherwise, if the processing chain is stereo (which means the focused channel is linked with a neighboring channel) then pressing either Channel button will show the same processing chain.  Any scopes or meters in the focused chain's GUI will display only the focused channel's signal (particularly relevant for a stereo chain).  

Some other functions that use the channel buttons are as follows:

## Stereo Side Selection
When choosing a local source, you can specify the side of a stereo pair by focusing the corresponding channel before you make your selection.

## Channel Muting
Pressing SHIFT plus one of the channel buttons will mute (or unmute) the given channel.  The channel LED will flash to indicate that the channel is muted.  

## Linking Channels
Pressing two (neighboring) channel buttons will link (or unlink) those two channels.

<br clear=all>

# Gx Inputs 
[G1-G4 inputs are unipolar 12-bit inputs designed to accept a wide variety of timing signals.]([File:er-301-Gx-inputs.png|thumb|The)]
These inputs are designed for "soft gate" signals:
* Unipolar CV such as envelopes.
* Gate signals of any magnitude and duration.
* Trigger signals of any magnitude and duration.

You cannot use these inputs for pitch CV because they are not calibrated.

[<br clear=all>

# INx Inputs 
The jacks labeled IN1 through IN4 are 16-bit inputs sampled at 60kHz with extra anti-aliasing analog filters in front of the ADC for clean and accurate digitization of audio signals.
[[File:er-301-INx-inputs.png|thumb|IN1-IN4 are inputs designed specifically for audio.]([File:Gx-mapping.png|400px]])]

* Programmable input ranges: -7V to 7V (default), -3.5V to 3.5V, and -1.75V to 1.75V.
* Channel gains and offsets are not calibrated thus these inputs should not be used for 1V/oct pitch control.
* Sampled at 60kHz using a 16-bit ADC with less than 1 LSB of error.
* DC-coupled
* The full range of each input is mapped internally to a floating-point value between -1 and 1 and values outside of the input range are hard-clipped:

{% include tip.html content="The analog anti-aliasing filters on inputs IN1-IN4 introduce a small amount of DC offset (approximately -5mV to 5mV).  However, when necessary you can remove this DC offset by placing a Fixed HPF unit in the signal path.  This is also how you can make (any) input AC-coupled." %}
<br clear=all>

# OUTx Outputs 
The jacks labeled OUT1 through OUT4 are 24-bit AC-coupled outputs sampled at 48kHz or 96kHz depending on the firmware loaded into the ER-301.

* Full-scale output range: -7V to 7V.
* AC-coupled for maximum headroom and accurate low-distortion reproduction in the audible frequency ranges.
* Flat frequency response from 3Hz to the Nyquist rate (24kHz when using 48kHz firmware, 48kHz when using the 96kHz firmware).
* Internally, the output is mapped from a floating-point value between -1 and 1 to the full -7V to 7V range.  Values outside of this range are hard-clipped:
[[File:er-301-OUTx-outputs.png|thumb|OUT1-OUT4 are 24-bit/96kHz AC-coupled outputs designed for audio.]([File:INx-mapping.png|400px]])]
[<br clear=all>

# ABCDx Input Matrix 
[[File:er-301-ABCD-matrix-inputs.png|thumb|These 12 inputs can each handle a wide variety of bipolar audio-rate modulation signals as well as 1V/oct pitch control.]([File:OUTx-mapping.png|400px]])]
These 12 inputs are all the same with the following properties:

* Responds to voltages between -10V and +10V.  Clips voltages outside of this range.
* Calibrated for accurate pitch tracking.
* Sampled at 60kHz using a 16-bit ADC with less than 1 LSB of error.
* DC-coupled
* Can be used to record hiqh-quality audio but you will experience aliasing if your audio contains substantial energy above 30kHz (e.g. pulse and saw waves from analog VCOs).  Instead, use the IN1-IN4 inputs to digitize audio that may alias above 30kHz.
* The voltage at each input is digitized and mapped internally to a 32-bit floating-point value that is exactly 0.1x (1/10th) of the voltage value (i.e. 1V => 0.1, 10V => 1.0 and so on)


{% include tip.html
content="It helps to think of the internal values as being a percentage of full-scale.  In other words, an internal value of 0.1 means 10% of full-scale.  If you received a value of 0.1 from an external input that the original voltage was 10% of the full input range for that input.  If you send a value of 0.1 to an external output (OUT1-4) than the amplitude will be 10% of the full-scale output range."
%}

<br clear=all>

# Mode Switch 

{% include note.html
content="Currently only  **edit** and  **scope** modes have an implementation.  The hold mode has no effect and is equivalent to  **edit** mode."
%}

The planned **hold** mode will keep all chain parameters fixed until you press Shift+Enter (Commit) to commit the values to their target values. 

In  **edit** mode, UI focus is set to the (up to) 4 output chains that determine the behavior the ER-301's output signals.  You use the [Channel buttons]([#Channel_Buttons|4)] to select which chain and channel to focus for modifications.

In  **scope** mode, you have access to some simple scope displays for all of the inputs ([[[#INx_Inputs|INx]([#Gx_Inputs|Gx]],)], [including a loop-back of the outputs ([[OUTx_Outputs|OUTx]([#ABCDx_Input_Matrix|ABCDx]]))]) and the signals coming from any Global chains.

# Storage Switch 

The STORAGE switch accomplishes two tasks:

# Switching between the  **user** and  **admin** UI contexts.
# Ejecting and mounting the SD card.

The ER-301 will attempt to eject the SD card when you move this switch in to the  **eject** position.  This will succeed only if no process is using the card.  In this case, the card is unmounted and the  **safe** LED will light.  If there are files that are still actively being accessed then the card will not be unmounted and instead a screen is shown that lists the current files in use.  In this case, the ER-301 will continue attempting to eject the card while the switch is in the  **eject** position.  Once all the files blocking the ejection are closed, the ER-301 will be able to successfully unmount the card.

The opposite process, mounting an SD card, is achieved by moving the STORAGE switch out of the eject position.  If you inserted the SD card while the STORAGE switch was in the  **user** or  **admin** position, then you will have to switch to the  **eject** position first and then switch back out in order to mount the card.

In short, only insert or remove the card while the switch is in the  **eject** position.

# SD Card Slot 
(See [[ER-301/Persistence]] for more details.)

The SD card slot on the front of the ER-301 is used to hold all of the data that belongs to the user such as samples and presets.
