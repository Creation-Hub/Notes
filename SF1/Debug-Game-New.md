## New Game Testing
From the main menu, open the console run: `SET 000a7d31 TO 8`
- Now click *New Game* button on the main menu.
- After a short loading screen you will now be in *New Atlantis*.
- To customize the player character run: `SLM 14`

The form `000a7d31` is a `GLOB` type called `MQ101Debug`.

#### MQ101Debug Values
- `MQ101Debug=0` : Full game start
- `MQ101Debug=1` : Move player to ship
- `MQ101Debug=3` : Barrett Scene
- `MQ101Debug=4` : Orbit around Lodge
- `MQ101Debug=5` : Start of the Mine Post Elevator
- `MQ101Debug=6` : FaceGen
- `MQ101Debug=7` : Kreet
- `MQ101Debug=8` : New Atlantis
- `MQ101Debug=9` : Artifact Pick up
- `MQ101Debug=10`: Pirate Attack


## Start Location
These game ini settings need more research.
```ini
[General]
sStartingWorld=
sStartingCell=
sStartingCellX=
sStartingCellY=
```


### Command: `StartNewGame`
> Command to trigger new game on main menu without UI
```
StartNewGame
```
This command does not appear to do anything from the main menu.
