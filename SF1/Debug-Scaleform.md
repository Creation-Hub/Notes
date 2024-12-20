## Configuration
This section describes INI settings which can be used to configure the developer console.


### Debug Text Font
This can be a valid AS3 font class name.
The `$` symbol is valid for AS3 class identifiers.
```ini
[Fonts]
sDebugTextFont=$ConsoleFont
```


## Commands
This section describes the most commonly used developer console commands.
Console commands are not case sensitive.


### Command: `PrintAllActiveMenus` (`pam`)
> Print all active menus
```
pam
```
The `PAM` command prints all active menus in order of their depth.
Each menu's visibility status is shown in parentheses.
The highest numbered menu is the top-most menu.
This is usually the cursor menu when the command is executed from the console menu.
```
PAM
0: MainMenu (visible)
1: Console (visible)
2: CursorMenu (visible)
```



### Command: `ShowMenu`
> Show or create a menu
```
ShowMenu <string-menuName>
```

Shows the given registered menu name.
A new instance of a the menu will be created if one does not exist.
Some menus persist and are hidden, others are created and destroyed as they are open/closed.

This example will open the `DataMenu`.
```
ShowMenu "DataMenu"
```

Note: Passing an unregistered menu-name string will cause a crash to desktop (CTD). There is likely a missing null check in the game.



### Command: `HideMenu`
> Hide or close a menu
```
HideMenu <string-menuName>
```
Hides or closes the given menu name depending on the menu's persistance settings.



### Command: `LoadFlashMovie`
```
LoadFlashMovie <string-swf-file>
```
Proper usage for this command is currently unknown.
The parameters are assumed.



### Command: `InvokeUIEvent`
> Invokes a ui->c++ event.
```
InvokeUIEvent <string>
```

The console command `InvokeUIEvent` can be used to invoke predefined events through the AS3 `BSUIDataManager` type.

The command is contextual and takes a single string parameter.
The valid event names are contextual based on the active menus.
Not every menu will listen for or dispatch the same named events.

Some menus use this AS3 `BSUIDataManager` to both request data and signal state for native game code.
The menu AS3 code can then create handlers for native engine events and data through `BSUIDataManager`.

#### Example
The command `InvokeUIEvent DataMenu_Missions` will open the Missions sub-menu while the `DataMenu` is open in game.
Menus have a `BSUIDataManager` class that can listen for and handle engine data sent to the UI.

It can also dispatch a named messages/requests to the engine.
[InvokeUIEvent with DataMenu_Missions](https://github.com/Creation-Hub/Interface/blob/8b20208309b7a676909d3ab8b1f648ba9b77c3b7/Interface/Source/Bethesda.DataMenu/DataMenu.as#L470)

Here is an example for the `DataMenu`.
- [Example at Bethesda.DataMenu/DataMenu.as#L541-L549](https://github.com/Creation-Hub/Interface/blob/8b20208309b7a676909d3ab8b1f648ba9b77c3b7/Interface/Source/Bethesda.DataMenu/DataMenu.as#L541-L549)
- [Example at Bethesda/Shared/AS3/Data/BSUIDataManager.as](https://github.com/Creation-Hub/Interface/blob/8b20208309b7a676909d3ab8b1f648ba9b77c3b7/Interface/Source/Bethesda/Shared/AS3/Data/BSUIDataManager.as)

The DataMenu dispatches several events through the `BSUIDataManager` class.
In my limited testing the command `InvokeUIEvent DataMenu_Missions` will open the Missions sub-menu while the DataMenu is open in game.
- `DataMenu_SelectedAttributesMenu`
- `DataMenu_SelectedInventoryMenu`
- `DataMenu_Missions`
- `DataMenu_SelectedShipMenu`
- `DataMenu_SelectedMapMenu`
- `DataMenu_SelectedPowersMenu`
- `DataMenu_SelectedStatusMenu`
- `DataMenu_PlotToLocation`
- `DataMenu_OpenPauseMenu`
- `DataMenu_ClosedForSubMenu`
- `DataMenu_Reopened`
- `DataMenu_CloseMenu`
- `DataMenu_SetPaperDollActive`
- `DataMenu_ClosedForSubMenu`
- `DataMenu_StartCloseAnim`
- `DataMenu_Open`

For example, the event names which are used with `BSUIDataManager` on the `DataMenu`.
These are listened for by the main DataMenu class.
- `DataMenuData`
- `PlayerData`
- `PlayerFrequentData`
- `DataInventoryProvider`
- `DataInventoryProvider`
- `QuestData`
- `PersonalEffectsData`
- `EnvironmentEffectsData`
- `FireForgetEventData`
- `DataMenuSkillsData`



### Command: `ToggleMenus`
> Hide all the menus. Used for taking screen shots.
```
ToggleMenus
```


### Command: `TestLoadingMenu`
> Debug function to open/close the Loading menu in the Loading thread.
```
TestLoadingMenu
```


### Command: `SetWorkshopItem`
> Set the Workshop menu's Node Cursor to the currently selected reference, if any.
```
SetWorkshopItem
```


### Command: `MenuPaused`
> Returns 1 if the game is paused at a menu, or 0 if the game is not paused at a menu.
```
MenuPaused
```


### Command: `ShowClassMenu`
> Bring up the class menu in char gen.
```
ShowClassMenu
```


### Command: `ShowLooksMenu` (`SLM`)
> (SLM)	ShowLooksMenu no second parameter will bring up the Looks menu, parameter=1 the Haircut, parameter=2 the Plastic surgery
```
ShowLooksMenu
```


### Command: `ShowNameMenu`
> Bring up the class menu in char gen.
```
ShowNameMenu
```


### Command: `ShowSpellMaking`
> Bring up the spellmaking menu.
```
ShowSpellMaking
```


### Command: `ShowBarterMenu` (`sbm`)
> Bring up the bartering menu.
```
reference.ShowBarterMenu
```
The short hand `sbm` command appears to be non-functional.
Use the full command name of `ShowBarterMenu` with a valid PRID reference.



### Command: `ShowRepairMenu` (`srm`)
> Bring up the repair menu in dialog.
```
ShowRepairMenu (srm)
```



## ActionScript
Use `ExternalInterface` if you're targeting Flash Player 8 or later.
- https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/system/package.html
- https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/external/ExternalInterface.html
