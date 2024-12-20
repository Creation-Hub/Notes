# Text Replacement
This page covers text replacement syntax used with `Quest`, `Book`, `Message`, `Terminal`, and some other places that text appears.


### Automatic
```
<Alias=Player>
```

The use of `PlayerShip` without an explicit quest alias is unconfirmed.
```
<Alias=PlayerShip>
```


### Form
Displays the original full name of the object.
```
<BaseName>
```


### Global Variable
Where `MyGlobalVariable` is the editor ID of a `GLOB` record.
```
<Global=MyGlobalVariable>
```

A `Quest` record is required for for text replacement values.
To use the `<Global>` tag on `Message` text, set the *Owner Quest* to a Quest intended to support text replacement.
On the `Quest` record under the *Quest Data* tab, add `GLOB` records to the *Test Display Globals* list.

Use Papyrus script to update the text replacement globals associated with the `Quest` and `Message` records.
```papyrus
MyGlobalVariable.SetValue(32)
MyQuest.UpdateCurrentInstanceGlobal(MyGlobalVariable)
MyMessage.Show()

MyGlobalVariable.SetValue(64)
MyQuest.UpdateCurrentInstanceGlobal(MyGlobalVariable)
MyMessage.Show()
```


### Quest Alias
Where `MyQuestAlias` is the *Alias Name* of an `Alias` type belonging to a `Quest` record.

Displays the *base* name of an object.
```
<Alias=MyQuestAlias>
```

Displays the *current* name of a reference.
```
<Alias.CurrentName=MyQuestAlias>
```

Displays the *short* name of a reference.
```
<Alias.ShortName=MyQuestAlias>
```

Displays the *plural* name of a reference.
```
<Alias.PluralName=MyQuestAlias>
```


### Pronouns
The pronoun for the alias.
```
<Alias.Pronoun=Player>
```

The pronoun object for the alias.
```
<Alias.PronounObj=Player>
```

The pronoun possessive object for the alias.
```
<Alias.PronounPosObj=Player>
```

See `OE_AustinF_DyingWish`.
```
<Alias.Obj=NPC>
```

### Magic Effect

The magnitude of the magic effect.
```
<mag>
```

The duration of the magic effect.
```
<dur>
```



### Capitalization
Any subtag suffixed with `Cap` will be capitalized.
```
<Alias.CurrentNameCap=MyQuestAlias>
<Alias.PronounCap=MyQuestAlias>
```


### Quest Reference Collection Alias
Where `MyQuestAliasCollection` is the *Alias Name* of a `RefCollectionAlias` type belonging to a `Quest` record.
```
<Alias.CurrentName=MyQuestAliasCollection[0]>
<Alias.CurrentName=MyQuestAliasCollection[1]>
<Alias.CurrentName=MyQuestAliasCollection[2]>
```



### Numeric Formatting
See `Message.Show(float, float, float, float, float, float, float, float, float)`
```
%.0f/%.0f
```



## Text Replacement with Papyrus Tokens
Text replacement tokens are defined with Papyrus functions.


### Token
```
<Token=MyTokenNameString>
```


### Token Value
See `ObjectReference.AddTextReplacementValue(string, float)`
```
<Token.Value=MyTokenNameString>
```


### Token Name
See `ObjectReference.AddTextReplacementData(string, Form)`
```
<Token.Name=MyTokenNameString>:
```


### Token Title
```
<Token.Title=MyTokenNameString>
```


### Token Index
```
<0.Name>
<1.Title>
<2.Value>
```



### Input & Controls
These are text replacement tokens for player controls.
Each control represents a binding between a game action and a device input such as Keyboard vs Gamepad.

### Control
- `[Activate]`
- `[Confirm]`
- `[StartWait]`
- `[Steady]`
- `[Sneak]`
- `[Sprint]`
- `[Crew]`
- `[CargoHold]`
- `[Repair]`
- `[RepairShip]`
- `[ShipTransaction]`
- `[ExecuteJump]`
- `[FastTravelShip]`
- `[SelectTarget]`
- `[Monocle]`
- `[PlaceBeacon]`
- `[ChangeMode]`
- `[ToggleView]`
- `[WeaponGroup1] `
- `[WeaponGroup2] `
- `[WeaponGroup3]`
- `[VATS]`
- `[Boosters]`
- `[SHMonocle]`
- `[TakeOff]`
- `[PlaceMarker]`
- `[ShipBuilder]`
- `[Edit]`
- `[FlightCheck]`
- `[Exit]`
- `[Add]`


Movement and Interaction
- `[Forward]`
- `[Back]`
- `[StrafeLeft]`
- `[StrafeRight]`
- `[Jump]`
- `[TogglePOV]`
- `[Move]`
- `[Look]`

Combat and Weapons
- `[PrimaryAttack]`
- `[SecondaryAttack]`
- `[Melee]`
- `[AltAttack]`
- `[WeaponReadyReload]`

Menus and Navigation
- `[DataMenu]`
- `[Accept]`
- `[Cancel]`
- `[Up]`
- `[Down]`
- `[Left]`
- `[Right]`


#### Device PC
- `[Click]`
- `[Space]`

#### Device Gamepad
- `[XButton]`
- `[RTrigger]`
- `[LShoulder]`
- `[RShoulder]`
- `[LeftStick]`
