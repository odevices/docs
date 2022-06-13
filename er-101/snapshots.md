---
layout: default
title: Manipulating Snapshots
has_children: false
nav_order: 1
---

# Manipulating Snapshot Files

The XML files that are created by the ER-101 Programmer are easily generated and modified if you are comfortable with XML and even easier if you are comfortable with dotNET/C#.  While this page is a bit sparse at the moment, I will try to collect here knowledge and utilities for would-be hackers of ER-101's snapshot files.

* [The ER-101 Common Library](/assets/ER101Common.zip): this is the same library (as a Visual Studio C# project) that the ER-101 Programmer uses to parse and generate snapshot files.  You will want to start with the LoadFromXML(...) and SaveToXML(...) methods in the ER101 class.

Download an example of a snapshot file from [here](/assets/er-101-example-snapshots.xml).  

## Uploading voltage tables

It is also possible to design your voltage tables on the computer and upload them via USB to your ER-101.  It just involves a little familiarity with XML files:

## Step 1

Using the ER-101 Programmer application, download your ER-101's snapshots as one large XML file.

Download the application from here: http://old.orthogonaldevices.com/er-101/Programmer

## Step 2

In the XML file there is a "snapshots" node that contains 16 "Snapshot" child nodes, one for each of the snapshots on your ER-101.  Each "Snapshot" node contains a "tracks" node with the following structure:

```xml
<tracks>

    <Track>
        <voltagesA>
            (voltage values here)
        </voltagesA>
        <voltagesB>
            (voltage values here)
        </voltagesB>
    </Track>

    <Track>
        <voltagesA>
            (voltage values here)
        </voltagesA>
        <voltagesB>
            (voltage values here)
        </voltagesB>
    </Track>

    <Track>
        <voltagesA>
            (voltage values here)
        </voltagesA>
        <voltagesB>
            (voltage values here)
        </voltagesB>
    </Track>

    <Track>
        <voltagesA>
            (voltage values here)
        </voltagesA>
        <voltagesB>
            (voltage values here)
        </voltagesB>
    </Track>

</tracks>
```

Notice there are 4 tracks and each track has two voltage tables (A and B).  The values in voltage table are the actual 16-bit integers that are sent to the DAC (0 corresponds to 0.000V, 8000 corresponds to 1.000V and so on).  You can edit the values with a text editor or custom script and then upload the modified XML file back to your ER-101 (again using the Programmer application).

The basic equation for converting frequency to voltage:

frequency = (frequency of C0 or 16.35Hz) * (2 ^ voltage)
voltage = log2 (frequency/16.35)

The basic equation for converting cents to voltage:

cents = voltage/1200
voltage = cents*1200

The basic equation for converting voltage to a DAC code that goes into the voltage table:

code = voltage*8000

## Step 3

Once you have your modified snapshots back in your ER-101, you can copy the voltage tables to other tracks or even to the USER reference voltage tables.

FYI, the ER-102 makes this process a lot simpler because the reference voltage tables are actually just individual files on your SD card. 