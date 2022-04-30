# Contributing to the CR6-TouchScreen-Firmware
# - IDE/Workflow Recommendations

## Introduction
This series of documents is an attempt to capture and preserve a set of instructions sufficient to lower the technological barrier for interested users of the CR6Community firmware to maintain and extend the touchscreen UI.

### Scope
If we tried to squeeze everything into the one document, it would be too big a labour to read.
We choose instead to produce a series of small documents, each of limited scope.

The scope of this document is, "Required Resources."

### Other documents in this series
Released:
TBA

In WIP:
* Recommended Tools and References
* UI Translation/Localization
* About Fonts
* DWIN display Configuration Guidelines

Planned:
* TBA

### How to Contribute to this series
We are open for contributions to every document in this series. 

Please feel free to participate in any of these ways:
- Start a discussion in the #lcd-discussion channel on the CR6Community Discord
- Comment on an existing Issue
- Open a new Issue
- Fork this repository and submit a PR with your proposed additions/deletions/modifications

## IDE Recommendations: Create a controlled development environment for working with this firmware

NOTE: You may have a different preferred way of organizing and executing your work, so this particular organization is just one suggested approach that works well for the author:

 - Use GitHub to maintain configuration control of your files (you will need your own GitHub account to do this, so if you don't already have one, we recommend that you open one.)
 - Clone the CR6-Touchscreen repository, to host your personally tailored files and to prepare Pull Requests, when you wish to propose one of your edits to the upstream team
 - Use the GitHub Desktop application to Clone your forked repository and keep a local copy on your computer
 - Point the DGUS tool at the GitHub Clone version of your repository (By using the tool to open the DWprj.hmi file in the local repository clone)
 - Edit the project files in the DGUS tool.
 - When you save modified files to the local repository, switch to the GitHub Desktop app and process a PR to upload those edits to the online copy of your forked repoository

 
### How to install the DGUS Tool

STEP 1: Download the [DGUS v8.2.1.4 software](https://github.com/CR6Community/CR-6-touchscreen/releases/download/v2.0.8.1-cr6-community-release-6.1/DGUS_Tool_V8.2.1.14.7z).

STEP 2: Unzip the DGUS tool file into a dedicated directory on your computer.   

To run the tool, find and launch the executable DGUS_Tool_V8.2.1.14.exe
