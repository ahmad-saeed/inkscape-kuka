# inkscape-path-to-krl-exporter

## Description
An Inkscape extension, used to convert the contours of text and images in Inkscape to KRL Code to be used with KUKA KR C4 controllers.


## Adding the extension to Inkscape
To install the extension:
* Download `kukakrl.inx` and `kukakrl.py`
* Copy the files into the extensions directory shown in the picture below.

![c:\Program Files\Inkscape\share\extensions](./screenshots/0.png)

After a restart of Inkscape, the new extension will be available.


## Example: Converting Text to KRL
1. Write your text with the text tool. The bottom left corner is the 0,0 location of the defined base or offset.
2. Mark and position your text. If you have more objects (lines, circles, …) to embed in your KRL Code, you have to mark them all. Only marked objects will be used to generate the KRL Code.

![](./screenshots/1.png)

3. Click `Path -> Object` to Path or press `Shift + Ctrl + C` to convert the text into a path. The Plugin will use this path to generate the KRL Code.

![](./screenshots/2.png)

4. Click `Extensions -> KUKA Tools -> Path to KRL` to start our plugin.
5. Enter your settings.
6. Click Apply to generate the KRL Code.

![](./screenshots/3.png)

After that the KRL Code will be stored and the motion path will be outlined.


## User Guide to extension settings
###   Tool:
Under most circumstances, a Kuka user first defines the TOOL and the BASE then refers to them in KRL using $TOOL, and $BASE system variables.
The Tool can be defined through one of these two main procedures:
* Automatically be calling the data variables created after performing any of the tool calibration processes from `Start-up > Calibrate > Tool`.
Example: `$TOOL = TOOL_DATA[1]`  where 1 is the saved tool number.
* Manually by entering their numeric XYZABC offset and orientation values.
Example: `$TOOL = {X 280, Y 0, Z -10, A 30, B 90, C 0}` where XYZ is the translational offset, and the ABC are Euler angles between the new base and the FLANGE coordinate system.

For this extension, you can only choose the tool number that matches yours, but if you desire to write the values manually, you can edit the created SRC file and add your values.

###   A° B° C° Orientation Angles (Euler Angles):
For this extension, A, B, and C represents the relative orientation of the selected tool relative to the selected base in certain motion path. 
Example: `LIN {X 0, Y 0, Z 0, A 90, B 180, C 0}`

This transformation can be performed by:
* Rotating the tool about its z-axis with an angle A (90 degrees)
* Rotating the tool about its y-axis with an angle B (180 degrees)
Note that the ABC angles are the same as Euler angles, but with a little bit different names, as the rotation about tool’s z-axis is named C in Euler’s.
