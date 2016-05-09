# SmartThings Virtual Open/Closed Tile
SmartThings device handler for virtual switches that double as open/closed sensors, which can be useful for automating Routines via Alexa.

SmartThings "Routines" can be used to automate various switches and modes.  Routines can be automated by time, motion sensor activity, and open/closed sensors, but not switches.   Amazon Echo (Alexa) can be used to turn on/off switches, but cannot currently trigger SmartThings routines directly.  There are a number of ways to solve this, but most involve multiple SmartApps or virtual devices.  For me, the "easiest thing that works" was to create a Virtual Switch that is _also_ an Open/Closed Sensor.  Adding this to "Things" means that we can now use Alexa to trigger the switch AND use the same switch's open/closed sensor to trigger a routine.

To use, you will need to copy this code once to make a device handler.  Then, for each routine you want to automate, you will need to create an instance of the virtual open/closed tile and configure the routine to use it.

To create a device handler (Do this one time only):

*   Copy the [.groovy code from this repository]( https://raw.githubusercontent.com/danroot/smartthings_virtual_open_closed_tile/master/OpenClosedButtonTile.groovy)
*   Go to https://graph.api.smartthings.com/  
*   Go to My Device Handlers
*   Create New -> From Code
*   Paste the code
*   Save. 

To create a device instance and automate a routine (Do this once for each routine you want to automate):
*   Go to https://graph.api.smartthings.com/  
*   Go to My Devices
*   New Device
*   Enter a Name, Label, and Device Id of the routine you would like to automate.  For example "Night Mode"
*   Choose "Open/Closed Button Tile" - likely at the _bottom_ of the list, and not alphabetical
*   Save
*   Open the SmartThings mobile phone app.
*   Confirm the switch shows in "Things"
*   Go to "Smart Apps" -> Amazon Echo (three bars icon top right -> Smart Apps" -> Amazon Echo)
*   Add the new switch
*   Next -> Done
*   Tell Alexa "discover new devices"
*   In SmartThings mobile phone app, go to routines
*   Click the gear over the routine you would like to automate.  For example "Good Night"
*   Scroll to the bottom, under "Additional Settings" -> Automatically perform "Routine Name" when...
*   "Something opens or closes"
*   For "Which?" choose the switch you created.  In this case "Night Mode"
*   For "Does This", choose "Opens"
*   Done. Done.

Automatically reset the switch from another routine (Optional):
*   Under Good Morning, "Turn Off these swtiches", choose "Night Mode"

Test the setup:
*   Be sure you are not already in the mode associated with the routine.  In this case, be sure you are not already in "Night" mode by pressing "Good Morning"
*   Tell Alexa "Turn on Night Mode"
*   She should respond "OK", turning on the "Night Mode" switch, which in turn triggers the "Good Night" routine and whatever automations you have built into that.



