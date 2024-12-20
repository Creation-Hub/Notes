# Hot Reloading
This section describes how to hot-reload content while the editor and game are running together.


### Use New Hot Reloading
This game ini setting was discovered which indicates the presence of an old and new hot-reload system.
The default was already set to 1.
Perhaps disabling the new hot loading system will allow the old `HLP` and `FCF` commands to function properly.
```ini
[General]
bUseNewHotloading=1
```


### Command: `HotLoadPlugin` (`HLP`)
> Load or reload the named plugin.
> Useful for getting changes without restarting. See also ForceCloseFiles.
> [Caution: Use at own risk! Modified running quests will be stopped (and restarted if possible). Gameplay and new savegames may be unstable.]
```
HLP "plugin-name.esp"
```


### Command: `ForceCloseFiles` (`FCF`)
> Close masterfile & plugins.
> Useful for letting CreationKit save to a plugin that is also loaded in-game.
> See also HotLoadPlugin.
> [Caution: Use at own risk! Gameplay and new savegames may be unstable.]
```
FCF
```


### Command: `CloseFile`
> Force-closes an open ESP/ESM file.
```
CloseFile
```
This is potentially related to the "new hot reload" functionality.


### Command: `HotloadPlugin`
> Hotload plugins
```
HotloadPlugin
```
This is potentially related to the "new hot reload" functionality.


### Command: `ForceReset`
> Force the game to run a full reset.
```
ForceReset
```
Execution of this command has resulted in crash to desktop (CTD) during user testing.


### Command: `HotReloadUI`
> Hot Reloads the User Interface SWFs.
```
HotReloadUI
```
This console command potentially reloads the currently displayed menus.
Most menus are disposed in memory when closed but some menus will have some persistence.
This will possibly reload the UI in cases like this.
