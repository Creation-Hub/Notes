# Game Data Configurations
This section describes how to configure the game with custom data.


### Load Order Default
This is the recommended dependency order for data files.
- `Starfield.esm`
- `BlueprintShips-Starfield.esm`
- `Constellation.esm`
- `OldMars.esm`


## Load Data File: Base Game Master
The base game content data plugin to use.
This is `starfield.esm` by default.
```ini
[General]
sBaseGameMasterfile=Starfield.ESM
```


## Load Data File: Test Data Master
Use the plugin file name and extension.
```ini
[General]
sTestDataMasterName=TestData.esm
```

This is possible related to the blueprint plugin.
```ini
[BlueprintShipPlugin]
bEnableTestDataPlugin=1
```


## Load Data File: Test Plugins
Determines plugin load order.
Use the plugin file name and extension.

```ini
[General]
sTestFile1 = MyModName.esp
```
```ini
[General]
sTestFile1=MyModName01.esp
sTestFile2=MyModName02.esp
sTestFile3=MyModName03.esp
sTestFile4=MyModName04.esp
sTestFile5=MyModName05.esp
sTestFile6=MyModName06.esp
sTestFile7=MyModName07.esp
sTestFile8=MyModName08.esp
sTestFile9=MyModName09.esp
sTestFile10=MyModName10.esp
```


## Enable Loose Files
Enables the loading of loose files which are outside of the archives.
```ini
[Archive]
bInvalidateOlderFiles=1
```


## Enable Additional Resource Archives
Historically the game will only respect archives explicitly listed as comma separated values of BSA/BA2 file names.
Setting the string to null would allow loading of any archive associated with a loaded plugin.
This needs further testing with an author created archive.
```ini
[Archive]
sResourceDataDirsFinal=
```
