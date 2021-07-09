---
layout: default
title: Hardware Revisions
parent: Behind the Panel
grand_parent: ER-301
nav_order: 7
---

You can find the ER-301 board revision number printed on the back near the OUT1 and OUT2 jacks.

# Revision 7 

Units sold from October 2016 to May 2018 are revision 7.  This is the first publicly available hardware release.

# Revision 8 

Never released.

# Revision 9 

Never released.

# Revision 10 

Units sold from June 2018 and onwards are revision 10.  The differences are quite minor:

* I removed the 5V Source Switch to prevent damage to the ER-301 hardware via the 5V bus line when using the BUS setting.  The result is that the ER-301 no longer uses the 5V bus line.
* I added an I2C header to allow integration with the Monome Teletype without having to perform any hardware modifications.

{% include figure.html
width="100%"
file="er-301/revisions/compare-rev10-rev7.jpg"
caption="A comparison of revision 10 (left) and revision 7 (right)."
%}
