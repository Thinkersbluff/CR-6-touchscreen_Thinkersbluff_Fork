# CR6Community-TouchScreen-Firmware Development and Maintenance
# - Translation / localization

Internationalization support in DGUS DWIN is very cumbersome. The background images of each page has the text hardcoded. To translate and have it first-class, you would need to duplicate all the bmps, give it a separate ID, and maintain that mapping in firmware as well or make every label an icon, which is a lot of work. The development team has no capacity to maintain localizations.

If you like to translate the user interface to your own language, you must fork this repository and maintain your own version of the touch screen firmware.

The complete workflow would look like this:

1. Fork this repository.
2. Work on the extui branch (this is the branch for all work going forward)
3. In your fork, follow [the steps in the images section of this file](#images--screen-images-sources) to change the current bitmaps and translate them. There are XCF files available as the source of these bitmaps, usable in Gimp, to make life easier but you can do what you want.
4. When we change something, it is up to you to replicate those screen changes. Therefore I recommend only to update the screen backgrounds and don't use the DWIN editor for anything other than for the purpose of generating the ICL file.
5. Translated touch screen builds are up to you to provide which would then need to be made from the same moment as we are releasing builds.

Good luck, and if you maintain your own translated firmware, please let us know!