This document covers how to use the VS Code live debugger to inspect Papyrus scripts at runtime.
A live debugger allows us to suspend execution of a running Papyrus script while the game is running.
We can then step through each instruction, examining the state of variables and the flow of execution step-by-step.
This powerful tool helps in understanding how scripts behave in real-time, aids in troubleshooting, and optimizing code.

## Editing the game initialization file
Before VS Code can attach to the game process we must ensure our `StarfieldCustom.ini` file has the appropriate values applied.

@ `%USERPROFILE%\Documents\My Games\Starfield\StarfieldCustom.ini`
```ini
[Papyrus]
iRemoteDebuggingPort=20548
bEnableRemoteDebugging=1
bLoadDebugInformation=1
```

Optionally, verbose logging can be enabled but the standard level of detail is easier to understand in most cases.
A log file for the remote debugger is created in the my documents folder within the `%USERPROFILE%\Documents\My Games\Starfield\Logs\Script\RemoteDebugger.0.log` folder.
```ini
[Papyrus]
bRemoteDebuggingLogVerbose=1
```

Using these settings will keep the game un-paused, active, and running while alt-tabbed to another window, such as VS Code.
This will make using breakpoints, monitoring logs, and switching windows while debugging much easier.
```ini
[General]
bAlwaysActive=1
bPauseOnAltTab=0
```


## Installing the VS Code Papyrus extension
To install the bundled Bethesda extension to VS Code, follow these steps.

1. Launch Visual Studio Code as described in the previous section.
2. Go to `View` -> `Extensions` then find the triple-dot hamburger menu called "Views and More Actions...". Look at the top-right corner of the extensions panel.
3. From the drop-down menu select `Install from VISX`. A .visx is a *Visual Studio Extension Installer*.
4. Navigate to `Starfield\Tools\VSCodePapyrusAddon\` and select the `vscodepapyrus-1.6.2.vsix` file.


## Creating a VS Code launch.json
Now we will tell VS Code to automatically generate a launch.json configuration file.
These tells VS Code how it should attach it's debugger to the game.

1. Ensure you have opened VS Code into the `steamapps\common\Starfield\Data\Scripts\Source` folder.
2. From the main menu in VS Code, navigate to the **Run** -> **Run and Debug** item.
3. From the drop down command palette select **Create a launch.json file**, then choose `Papyrus for Starfield`.

A `launch.json` will now be generated for your workspace automatically.

Alternatively create a `Starfield\Data\Scripts\Source\.vscode\launch.json` file with the following content.
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Attach to game",
            "type": "papyrus-starfield",
            "request": "attach",
            "address": "localhost",
            "port": 20548
        }
    ]
}
```


## Source Breakpoints
A breakpoint is used to suspend execution of a Papyrus script while the game is running.
We can choose the exact line of our source code the debugger will suspend on by setting a *breakpoint*.
This is represented by a red dot in the document-well of your Papyrus script source.

When a running script "hits" this breakpoint, the script execution is "paused" and some additional UI will appear in the VS Code debug panel.
We can then step through each instruction (line) while examining the state of variables and the flow of execution step-by-step.
This is referred to as "stepping" through code.

In the following sections I will walk you through debugging a specific script.

1. Open the the script `VendorActivatorScript.psc`. Navigate quickly by pressing `CTRL` + `SHIFT` + `P` and then pressing `Backspace` to clear the existing `>` character. Now begin typing the script name and select the file.
2. Find the `OnActivate` event and place a breakpoint on the first instruction at line `35`. You can quickly jump to a line number but clicking the current line status bar widget, then typing the desired line number in directly.

Now you are ready to launch the game and see the live remote debugger in action.


## Launching Starfield
When used with the debug quick start command, `VendorActivatorScript` is the prime script to try out the extension breakpoints.
Note that you do not need to have the associated PEX extracted from BA2 archives in order to hit a source breakpoint, but you do need the source for all files you intend to "step" through.

1. Launch Starfield and wait until you reach the main menu.
2. From the Starfield **main menu**, open the developer console and run: `SET 000A7D31 TO 8`. The form `000A7D31` is a `GLOB` type called `MQ101Debug`.
3. Switch back to VS Code and navigate to the debug panel. From the drop down menu select **Attach to game** with the green arrow icon.
4. Now switch back to Starfield and click the *New Game* button on the main menu. After a short loading screen you will be standing in the *New Atlantis* spaceport.
5. When you debug spawn into the New Atlantis star port, walk straight ahead and activate the *Trade Authority Kiosk*.
6. You will see the breakpoint line in VS Code has now become highlighted and a variable explorer, watch list, call stack, and breakpoint tracker are visual in the debug panel. This is how you know your breakpoint has been hit.

When script execution "hits" your breakpoint that stack alone alone will pause while many other scripts and the game continue to operate.

With your hit breakpoint, lets try "stepping into" the code. You should also see a floating mini-menu in VS Code with icons semi-resembling the play, pause, rewind, and stop of a classic video cassette recorder (VCR).
The functionality here is somewhat similar. use the downward pointing arrow to "step into" the next instruction of your code and observe how the variables panel in VS Code updates with live values.

This allows use to examine the state of variables and the flow of execution step-by-step.
This powerful tool helps in understanding how scripts behave in real-time, aids in troubleshooting, and optimizing code.

One last step..
- Enjoy your debugging.
