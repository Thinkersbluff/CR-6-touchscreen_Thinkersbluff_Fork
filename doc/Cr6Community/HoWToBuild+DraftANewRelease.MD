# CR6Community-TouchScreen-Firmware Development and Maintenance
# - How To Build and Draft a New Release

### How to open a DWIN project in the DGUS Tool

1. Download and unzip the project Source.zip file into a blank directory on your computer.


3. Launch the DGUS tool and click the "Open Project" icon.
4. Browse to the src\DWIN folder where you unzipped the Source file and click on the file "DWPrj.hmi" to open the project.

![image](https://user-images.githubusercontent.com/36551518/165621529-396f96f3-7194-4192-98b9-61d3b918f172.png)



### Where to find the various Images used by the DGUS Tool to Generate the TFT files

You can find the source files where the screen bitmaps are generated from in the [`src\images_src`](src\images_src) folder.

To update the BMP of a screen put the **generated BMP file you made with your image editor** in the [`src\DWIN\DWIN_SOURCE`](src\DWIN\DWIN_SOURCE) folder. 


#### Updating the touch screen firmware files

It will be picked up automatically by the build process of DWIN when saving or generating the project. However, the ICL file is what actually gets flashed. This is essentially a dictionary of concatenated compressed JFIF files.

Next, re-generate the `23_Screen.icl` ICL file are follows:

![Update ICL file](doc/update-screen-icl.gif)

Things worthy of note:

- Quality is set to 100%, followed by pressing the "Set all" button to apply it to each import file.
- The `DWIN_SOURCE` is used as a source for generating the ICL.
- The ICL is saved twice: once in the `DWIN_SOURCE` folder, once in the `DWIN_SET` folder.

As you can note, you update it in both `DWIN_SET` and `DWIN_SOURCE`. The first is what goes to the touch screen, the latter is what the DWIN editor uses (apparently).

For icon ICL generation the process is the same, except that you pick the icons from a subdirectory of `DWIN_SOURCE`.

### Flash space

DWIN uses a specific set-up of the flash space as described in the manual - as shown below.

![DWIN flash space](doc/flash-space.png)

Essentially what it boils down to:

- The flash space is divided into 256KB sectors
- The number prefix on the ICL/HZK/BIN file name is the sector number where the file is flashed
- A sector can only contain a single file
- A file can span over multiple sectors, and if a file needs 1½ sectors for instance, it will allocate 2 sectors.
- There is no protection against sector overwriting: if you have files overlap sectors, DWIN will happily flash the next file over the previous file

So with the above in mind one must take care to make sure files do not overlap. When you flash everything to the touch screen you must ensure you've deleted the old (renumbered) ICL files from your SD card, otherwise weird things will happen. Background may go missing, etc.

During build a script will run to make sure no sectors have been overallocated. You can also run this script manually.

![DWIN sector allocation check script](doc/sector-allocation-check.png)