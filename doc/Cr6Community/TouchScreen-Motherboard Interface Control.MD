# CR6Community-TouchScreen-Firmware Development and Maintenance
# - TouchScreen/Motherboard Interface Control

## How buttons are handled with code

In the currently - cleaned up - source code of the touch screen handling in Marlin, the events of the touch screen are handled as described below. This may change in the future. This picture says it all:

![DWIN button-code correlation](doc/button_type.png)

For buttons:

- Virtual Pointers for buttons are defined in `extui/lib/dgus_creality/DGUSDisplayDef.h`
- In `extui/lib/dgus_creality/DGUSDisplayDef.cpp` in the `ListOfVP` the Virtual Pointer are connected to a callback handler
- Because the Creality display used the same VP all over the place, sometimes in completely different functions or values (and this is quite some work to clean up!), these "legacy" VPs are delegated to `DGUSCrealityDisplay_HandleReturnKeyEvent`
- For legacy VPs handlers are defined per page in `extui/lib/dgus_creality/PageHandlers.cpp`
    - The "Key Data" is used to distinguish between the actual key pressed and passed to these functions as `buttonValue`

For dynamic updatable values:

- Dynamic updatable values are Virtual Pointers with a value that is pushed from the display when it is changed, and pushed to the display during the Marlin `idle` loop
- The Virtual Pointers are defined in `extui/lib/dgus_creality/DGUSDisplayDef.h`
- Per dynamically updated virtual pointer there is in `extui/lib/dgus_creality/DGUSDisplayDef.cpp`:
    - A registration in `ListOfVP`, with:
        - The VP ID
        - A pointer to the memory location to read the value from in Marlin (can be `nullptr`)
        - A callback that is triggered when the VP changed in the display and is pushed to firmware
        - A callback that is triggered to format the VP for transfer to the display. This is because strings need to be sent differently than floats, or if your VP does not point to a direct value in memory.
    - A mention in the specific `VPList` for the current page as referenced in `VPMap`. This is to optimize that we don't update VPs that are not displayed anyway.
- Some values like the M117 text are transient and are pushed directly to the display, but are still present in the `ListOfVP`


# Legacy version of Creality's CR6 TouchScreen firmware

If you like to see how the touch screen code is handled in the Creality firmware and the original Community Firmware release 3 and lower, please check the [cf3-legacy](https://github.com/CR6Community/CR-6-touchscreen/tree/cf-3-legacy) branch. 

This branch is no longer maintained and only exists for historical reference purposes.
