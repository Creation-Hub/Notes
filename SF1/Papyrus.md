### Base Scripts
Papyrus has 101 native base scripts.

- Action
- Activator
- ActiveMagicEffect
- Actor
- ActorBase
- ActorValue
- AffinityEvent
- Alias
- Ammo
- Armor
- AssociationType
- Book
- CameraShot
- Cell
- Challenge
- Class
- CombatStyle
- ConditionForm
- ConstructibleObject
- Container
- Curve
- Debug
- Door
- EffectShader
- Enchantment
- Explosion
- Faction
- Flora
- Form
- FormList
- Furniture
- Game
- GameplayOption
- GlobalVariable
- Hazard
- HeadPart
- Idle
- IdleMarker
- ImageSpaceModifier
- ImpactDataSet
- Ingredient
- InputEnableLayer
- InstanceNamingRules
- Key
- Keyword
- LegendaryItem
- LeveledActor
- LeveledItem
- LeveledSpaceshipBase
- LeveledSpell
- Light
- Location
- LocationAlias
- LocationRefType
- MagicEffect
- Math
- Message
- MiscObject
- MovableStatic
- MusicType
- Note
- ObjectMod
- ObjectReference
- Outfit
- Package
- PackIn
- Perk
- Planet
- Potion
- Projectile
- Quest
- Race
- RefCollectionAlias
- ReferenceAlias
- ResearchProject
- Resource
- Scene
- ScriptObject
- Scroll
- ShaderParticleGeometry
- Shout
- SoulGem
- SpaceshipBase
- SpaceshipReference
- SpeechChallengeObject
- Spell
- Static
- TalkingActivator
- Terminal
- TerminalMenu
- TextureSet
- Topic
- TopicInfo
- Utility
- VisualEffect
- VoiceType
- Weapon
- Weather
- WordOfPower
- WorldSpace
- WwiseEvent

#### SortBaseScripts.ps1
This is a PowerShell script to sort the above files into their own folder.
I find it easier to browse when they are separated from the game scripts.
Fill in the correct paths on the first two variables for your system, then execute the script.

```ps1
# Define the source directory where the scripts are currently located.
$sourceDirectory = "C:\Program Files (x86)\Steam\steamapps\common\Starfield\Data\Scripts\Source"

# Define the destination directory to store the base scripts.
$destinationDirectory = "C:\Program Files (x86)\Steam\steamapps\common\Starfield\Data\Scripts\Source\Base"

# Create the destination directory if it does not exist.
if (-not (Test-Path -Path $destinationDirectory))
{
	New-Item -Path $destinationDirectory -ItemType Directory
}

# List of native base scripts to move.
$baseScripts = @(
	"Action.psc", "Activator.psc", "ActiveMagicEffect.psc", "Actor.psc", "ActorBase.psc",
	"ActorValue.psc", "AffinityEvent.psc", "Alias.psc", "Ammo.psc", "Armor.psc",
	"AssociationType.psc", "Book.psc", "CameraShot.psc", "Cell.psc", "Challenge.psc",
	"Class.psc", "CombatStyle.psc", "ConditionForm.psc", "ConstructibleObject.psc", "Container.psc",
	"Curve.psc", "Debug.psc", "Door.psc", "EffectShader.psc", "Enchantment.psc",
	"Explosion.psc", "Faction.psc", "Flora.psc", "Form.psc", "FormList.psc",
	"Furniture.psc", "Game.psc", "GameplayOption.psc", "GlobalVariable.psc", "Hazard.psc",
	"HeadPart.psc", "Idle.psc", "IdleMarker.psc", "ImageSpaceModifier.psc", "ImpactDataSet.psc",
	"Ingredient.psc", "InputEnableLayer.psc", "InstanceNamingRules.psc", "Key.psc", "Keyword.psc",
	"LegendaryItem.psc", "LeveledActor.psc", "LeveledItem.psc", "LeveledSpaceshipBase.psc", "LeveledSpell.psc",
	"Light.psc", "Location.psc", "LocationAlias.psc", "LocationRefType.psc", "MagicEffect.psc",
	"Math.psc", "Message.psc", "MiscObject.psc", "MovableStatic.psc", "MusicType.psc",
	"Note.psc", "ObjectMod.psc", "ObjectReference.psc", "Outfit.psc", "Package.psc",
	"PackIn.psc", "Perk.psc", "Planet.psc", "Potion.psc", "Projectile.psc",
	"Quest.psc", "Race.psc", "RefCollectionAlias.psc", "ReferenceAlias.psc", "ResearchProject.psc",
	"Resource.psc", "Scene.psc", "ScriptObject.psc", "Scroll.psc", "ShaderParticleGeometry.psc",
	"Shout.psc", "SoulGem.psc", "SpaceshipBase.psc", "SpaceshipReference.psc", "SpeechChallengeObject.psc",
	"Spell.psc", "Static.psc", "TalkingActivator.psc", "Terminal.psc", "TerminalMenu.psc", "TextureSet.psc",
	"Topic.psc", "TopicInfo.psc", "Utility.psc", "VisualEffect.psc", "VoiceType.psc",
	"Weapon.psc", "Weather.psc", "WordOfPower.psc", "WorldSpace.psc", "WwiseEvent.psc"
)

# Move the scripts to the new "Base" directory.
foreach ($script in $baseScripts)
{
	$scriptPath = Join-Path -Path $sourceDirectory -ChildPath $script
	if (Test-Path -Path $scriptPath)
	{
		Move-Item -Path $scriptPath -Destination $destinationDirectory
	}
	else
	{
		Write-Warning "File not found: $scriptPath"
	}
}
```



## Papyrus Logging
```ini
[Papyrus]
bEnableLogging=1
bEnableTrace=1
bLoadDebugInformation=1
bAssertOnOverflow=1
bEnableRemoteDebugging=1
bRemoteDebuggingLogVerbose=1
```


## Papyrus Profiling
```ini
[Papyrus]
bEnableProfiling=1
```

Use `startpsp <scriptname>` and `stoppsp <scriptname>` to start and stop script profiling.
A log is created `My Games\Starfield\Logs\Profiling\Script_<scriptname>.0.log`.
