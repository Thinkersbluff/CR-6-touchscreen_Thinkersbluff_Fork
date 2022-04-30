# CR6Community-TouchScreen-Firmware Development and Maintenance
# - Recommended Tools and Resources

## Introduction
Here, we describe the tools and resources that the CR6Community development team has used to derive and maintain the current CR6Community-TouchScreen-Firmware.

## DWIN's Own Recommendations
For reference, in [episode#1 of her YouTube Tutorial series](https://www.youtube.com/watch?v=_k3zu6JFv6I), DWIN Marketing Director Guo Maria recommends that you assemble the following tools and resources, to support project development and maintenance:

1. The DWIN Graphic User System (DGUS) Tool (v7.624 or higher)
   
    * The DWIN display on the CR6 printer is normally programmed and configured by loading binary files into a folder named DWIN_SET on a micro SD card inserted into the display, and then turning ON power.

	* The DGUS Tool is the Integrated Development Environment (IDE) provided by DWIN (the company), with which one must build, generate and maintain those files.

2. A DGUS Host Environment

	* A convenient simulation of the actual DWIN Screen Hardware(or actual representative hardware), on which the application can be validated and debugged

3. The DGUS Font Generator

	* A DGUS tool for generating the .HZK font file to be flashed to the display
	
4.  SSCOM v5.13

	* A DWIN Serial Communications tool, through which one can connect a DWIN display to a developer's PC, to support application development
	
5.  T5L Development Guide

	* An DWIN application programmer's guide to DWIN displays based on the T5L ASIC, such as the CR6 TFT
	
6.  Factory Demo Project

	* A sample DWIN Application project provided by DWIN (the company) as a template to help their customers figure out - by example - how to program their own applications.
	
7. Product Data Sheet

	The Product Data Sheet for the particular DWIN display being used to host the application.
	

## CR6Community Development Team Recommendations

### Which version of DGUS Tool to use?
Download, install and use [DGUS Tool v8.2.1.14](https://github.com/CR6Community/CR-6-touchscreen/releases/download/v2.0.8.1-cr6-community-release-6.1/DGUS_Tool_V8.2.1.14.7z) or higher.

#### Why v8.2.1.14?

The CR6Community dev team used DGUS Tool v8.0.1.1 to build and maintain versions 4 through 6.1 of this firmware. 

In the first few months of 2022, however, the team learned that Community members were having difficulties when flashing CF6.1-Final to new CR6 printers. They reported screens going blank or becoming non-responsive to touch.  

The team's investigations revealed that:
- the newer machines were being delivered with DGUS2 v4.5 installed, rather than the v3.5 for which the team had previously generated and verified correct operation of the CR6Community firmware.  
- DWIN displays running DGUS2 v4.5 were calibrated differently than earlier displays, which appeared to account for the screen going blank, if the DGUS v3.5 files were flashed to the display, and for the screen not responding to button presses if CF6.1-Final was flashed to the display running and calibrated for DGUS2 v4.5 

The team also learned that DWIN_SET firmware built with DGUS Tool v8.2.1.14 would run on any version of DGUS2 from v2.0 and higher, but that a DWIN_SET built with DGUS Tool v8.0.1.1 is NOT compatible with DGUS2 v4.5 or higher.

**All future updates of the CR6Community-TouchScreen-Firmware must now therefore be performed using DGUS Tool v8.2.1.14 or higher.**

### What DGUS Operating Environment to Use?

* One option is to use an actual display, installed on the printer
* A second option is to use an actual display connected to a PC through SSCOM
* A virtual machine environment also exists

### Which FONT tool(s) to use?

The DGUS Tool suite includes the FONT Generator tool with which to generate the .HZK file to be flashed via DWIN_SET

In the event that one wishes to use a different font style, one may also wish to generate a new font library as the input to the DGUS Font tool, using something like FontForge

### Is SSCOM necessary?

The use of SSCOM is optional.  It may offer advantages to developers who wish to work on DWIN projects while travelling.

### Which T5L Guide to use?

The CR6Community development team used [version 1.0 of the T5L_DGUSII Application Development Guide, dated 2Sept2020](https://github.com/CR6Community/CR-6-touchscreen/blob/extui/doc/vendor/T5L_DGUSII%20Application%20Development%20Guide20200902.pdf).

### Which Demo Project to use

?

### Which Product Data Sheet to use?

?

## Other documentation

Vendor documentation is mirrored to the [doc/vendor](doc/vendor) folder.

The vendor's English-Language support site is here: https://www.dwin-global.com/

The vendor's Marketing Director has posted numerous T5L/DGUS tutorials on YouTube at: https://www.youtube.com/playlist?list=PLRmlyfAByHzeay1LwW9FkcwaUOE20abk2


In addition, [this is a nice resource](https://github.com/rubienr/MarlinDgusResources/tree/creality-ender-5-plus/projects).