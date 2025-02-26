# TIME ELEKTRO WITH GRZEGROZ

## LIGHT IN MASTER BEDROOM

So, he managed to the dimmer in our room (Lys tak soverom) by changing paramter 13 from "Readout" to "Force auto-calibration without Fibaro Bypass" and then suddenly parameter 33 is shown as "Dimming possible".

## SMOKE DETECTORS

He said that there is a problem when you connect more than 3. Apparently he talked to the support of the smoke detectors an they confirmed. Not sure about the implications.

He said you could press the button on the smoke detector to get them to stop sending signals to the others. It appeared to work on some of them but not all. The one that it did not work on could be due to the fact that the battery level was low.

In HomeAssistant, he went into Kontroll $\rightarrow$ Smoke detector site. Here, we enetered the "Device info" each individual smoke detector and subsequently "Z-Wave device configuration" where Paramter 5 (Status of Automated Meshing of Smoke Alarms) and 6 (Status of Automated Meshing of Battery Alarms) where changed from "Active" to "Inactive".  
