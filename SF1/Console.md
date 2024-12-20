# Console
This section describes the in-game developer console.
The console accepts text paste commands from the Windows operating system.
Some console commands will mark your save as "[MODDED]" and disable achievements.

#### Parameter Types
- **bool:** A boolean type represents the values `true` and `false`. Command parameters often require the integer representation of boolean values which are `0` for `false` and `1` for `true`. Sometimes `true` can be expressed as any value *other than* zero.
- **int:** A numeric integer value type represents whole numbers such as `-1`, `0`, `1`, and so on.
- **float:** A numeric floating point value type represents decimal numbers such as `-1.05`, `0.5`, `0.0`, `0.75`, `1.0`, and so on.
- **string:** A text value type represents a sequence of characters, more often referred to as a string of characters. Command parameters accept unquoted strings such as `Hello`, but if your string contains spaces then quotes are required, such as `"Hello World"`.
- **editor-id:** The friendly string name for a data record. Best practice dictates that data record editor ids should never contain spaces, and therefore often to do not require quoting. But spaces in editor identifiers are technically allowed.
- **form-id:** The numeric hexadecimal identifier associated with a data record. Leading zeros may be excluded from hexadecimal identifiers.
- **reference-id:** The numeric hexadecimal identifier which references a created instance of a data record. Leading zeros may be excluded from hexadecimal identifiers.


### PRID
The term PRID stands for "picked reference identifier".
This is represented on the console UI by the *selected reference* top-center of the menu.
The mouse left click will pick a new PRID on screen.
You may have to move fairly close to the intended mouse pick target.
The mouse scroll wheel will cycle the current PRID between the next and previous available references on screen.

```
PRID
PRID <reference-id>
```

Typing `PRID` with any parameters will clear the current PRID picked reference.
Providing a reference identifier will pick that reference as the current PRID.


#### PRID Suffixes
These are suffixes which appear next to the developer console menu's picked reference identifier.
These suffix tags provide some information about persistance and status.
- `[EP]`
- `[PP]`
- `[D]` The reference has been marked for deletion. See also the console command `MarkForDelete`.
- `[P]`
- `[T]` *?possibly applied to created references? Seen on ship GBFM references.*


#### Named References
Commands which operate on an object such as `<object-reference>.AddItem <form> <amount>` can be called with named references such as `Player.AddItem F 3`.
This adds three Credit Sticks to the player Actor where `Player` is the named reference.
The form-id for a Credit Stick is `0x0000000F` which can be short handed to just `F`.
Leading zeros can be omitted on hexadecimal values.



## Configuration
This section describes INI settings which can be used to configure the developer console.



### Console Highlight Selected
Applies a highlight shader to the selected console reference.
The values are red, green, blue, alpha.
Below represents a red shader with 20 alpha.

```ini
[Menu]
aConsoleSelectedRefColor="255,0,0,20"
```



### Execute Startup Console Commands
Runs the given console command at game start.
Commands executed by `sStartingConsoleCommand` will appear on the console history buffer.

```ini
[General]
sStartingConsoleCommand=SET 000a7d31 TO 8
```

Multiple commands can be run when separated by a semicolon.
```ini
[General]
sStartingConsoleCommand=SET 000a7d31 TO 8;tgm;tmm 1
```

The execute batch command can also be run from this setting.
```ini
[General]
sStartingConsoleCommand=bat MyCommandFile
```



## Commands
This section describes the most commonly used developer console commands.
Console commands are not case sensitive.


### Command: `QuitGame` (`qqq`)
> Exit game without going through menus.
```
QuitGame
```



### Command: `Help`
> Show this help.
```
Help
```



### Command: `ToggleFullHelp`
This changes the behavior of the `Help` command to be more verbose.
The `Help` command will now display all commands with a description on the buffer when now parameters are given.
```
ToggleFullHelp
```



### Command: `FindForm` (`find`)
Finds all forms that partially match the given editor-id and displays the form-id for each.
This is useful when looking of a global variable's (`GLOB`) form-id by using it's editor-id.
> Find a form
```
Find <editor-id>
FindForm <editor-id>
```



### Command: `SetConsoleOuputFile`
> Sets the given file as target for console output.
```
scof <string>
SetConsoleOuputFile <string>
```
Prints the console output to the given text file.
This does not appear to work as it did in previous game titles.
The spelling in `SetConsoleOuputFile` is the actual command name even though it is a misspelling of "output".

An example parameter for a `cof.txt` file.
```
SetConsoleOuputFile "cof"
```



### Command: `ClearConsole`
> Clears the console log
```
ClearConsole
```
This does not clear the console buffer history, but it may potentially clear the file created by the non-functional `SetConsoleOuputFile` command.



### Command: `RunConsoleBatch` (`bat`)
> Run a console batch file
```
bat
RunConsoleBatch
```

Executes a developer console command *batch file*.
The contents of a console command batch file are the same command you would enter in-game and are executed one by one.
A console command batch file is simply a text file of any name located withing the `Starfield\Data\` folder.


In this example, the file is called `Starfield\Data\MyCommandFile.txt`.
The command takes a file name without the `txt` extension.
Be sure to use a quoted string if the value contains spaces or a directory separator.
```bat
bat MyCommandFile
```

It is also possible to execute a console command batch file from a sub-folder such as `Starfield\Data\MyModName\MyCommandFile.txt`
Be sure to escape directory separators with a `\\` double back slash.
```
bat "MyModName\\MyCommandFile"
```


### Command: `WaitBatchFile`
> Pause a "Batch File" for a set amount of time.
```
WaitBatchFile
```
This console commands is useful in console batch files where a mouse pointer cannot be used to set the selected reference.


### Command: `StopBatchFile`
> Stop a running batch file
```
StopBatchFile
```
This console commands is useful in console batch files where a mouse pointer cannot be used to set the selected reference.


### Command: `PickPlayer`
> Select the player character
```
PickPlayer
```
This command will set the console PRID to the player.
This console commands is useful in console batch files where a mouse pointer cannot be used to set the selected reference.


### Command: `PickMenuPaperDoll`
> Select the menu PaperDoll
```
PickMenuPaperDoll
```
This does the same as `PickPlayer`, but selects the `DataMenu` representation of the player which is called the "paper doll".
This console commands is useful in console batch files where a mouse pointer cannot be used to set the selected reference.


### Command: `PickRefByID`
> Select a reference by id for the console.
```
PickRefByID
```
This console commands is useful in console batch files where a mouse pointer cannot be used to set the selected reference.


### Command: `PickLastRef`
> Select the last created ref for the console.
```
PickLastRef
```
This console commands is useful in console batch files where a mouse pointer cannot be used to set the selected reference.


### Command: `PickNextRef`
> Select the the next ref in the center of the screen outside the console
```
PickNextRef
```
This console commands is useful in console batch files where a mouse pointer cannot be used to set the selected reference.


### Command: `PickNextActor`
> Select the the next actor in the center of the screen outside the console
```
PickNextActor
```
This console commands is useful in console batch files where a mouse pointer cannot be used to set the selected reference.


### Command: `PickClosestActor`
> Select the the closest actor to the player
```
PickClosestActor
```
This console commands is useful in console batch files where a mouse pointer cannot be used to set the selected reference.


### Command: `PickClosestShip`
> Select the the closest ship to the player's ship
```
PickClosestShip
```
This console commands is useful in console batch files where a mouse pointer cannot be used to set the selected reference.


### Command: `PridBreak`
> When a debugger is attached, this breaks execution & puts the prid target on the stack
```
PridBreak
```
