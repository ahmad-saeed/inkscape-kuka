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
2. Mark and position your text. If you have more objects (lines, circles, …) to embed in your G-Code, you have to mark them all. 

...Only marked objects will be used to generate the KRL Code.

![](./screenshots/1.png)

3. Click `Path -> Object` to Path or press `Shift + Ctrl + C` to convert the text into a path. 

...The Plugin will use this path to generate the KRL Code.

![](./screenshots/2.png)

4. Click `Extensions -> KUKA Tools -> Path to KRL` to start our plugin.
5. Enter your settings.
6. Click Apply to generate the KRL Code.

![](./screenshots/3.png)

After that the KRL Code will be stored and the motion path will be outlined.