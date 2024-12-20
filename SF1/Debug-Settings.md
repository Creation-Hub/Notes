# Initialization Settings
This section describes how to interact with initialization settings.

### Get INI Setting
Takes a string including key followed by the section.
> Prints an INI setting value to the console.
```
GetINISetting
GetINISetting "sTestFile1:General"
```

### Set INI Setting
> Sets an INI setting value.
```
SetINISetting
SetINISetting "iConsoleSizeScreenPercent:Menu" 10
```

### Save Settings to User Plugin INI
Saves user runtime INI values to a plugin INI fragment.
If your test plugin is `MyMod.esp`, the INI will be saved `MyMod.ini`.
> Writes all the .ini files.
```
SaveIni
SaveIniFiles
```

### Refresh INI Setting
> Refresh INI settings from file.
```
RefreshINI
```


# Game Settings (`GMST`)
This section describes how to interact with game settings.

### Get Game Setting
> Gets the value of the given GameSetting.
```
GetGameSetting (GetGS)
```

### Set Game Setting
> Sets the value of a GameSetting.
```
SetGameSetting
```


# Global Variables (`GLOB`)
This section describes how to interact with global variables.

### Show All Global Variables
Prints all global variables and their values to the console.
> Show all global variables.
```
ShowGlobalVars
```

### Get Global Variable
Prints the value of the the specified global variable to the console.
Parameter takes an Editor ID string.
> What is the value of the specified global variable?
```
GetGlobalValue <string-glob>
```

### Set Global Variable
Sets a value of a variable.
Use `FindForm` to get the form-id (fid).
```
SET <form-id> TO <float>
```
