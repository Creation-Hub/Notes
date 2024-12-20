# Quests
This section describes how to debug quest related content while the game is running.


## Commands
This section describes the most commonly used developer console commands.
Console commands are not case sensitive.


### `ShowQuestVars` (`sqv`)
> Show quest variables. You can optionally specified a papyrus variable or script to filter with [svq QuestID]
```
sqv <form-id>
```
This developer console command will print the values of all quest related variables which include the variables and properties of attached scripts.


### Other Commands
- ShowQuestVars: Show quest variables. You can optionally specified a papyrus variable or script to filter with [svq QuestID]
- ShowQuests: List quests.
- ShowQuestAliases: Show quest aliases. [ShowQuestAliases QuestID]
- SetPapyrusQuestVar: Set a Papyrus property on the specified quest.
- SetQuestAliases: Set quest aliases. [SetQuestAliases QuestID]
- ClearQuestAliases: Clears quest aliases. [ClearQuestAliases QuestID]
- SetQuestLocationAliasDebug: Sets a debug location for a quest alias before it starts.
- SetQuestRefAliasDebug: Sets a debug ref for a quest alias before it starts.
- ShowQuestLog: Show Quest Log
- ShowFullQuestLog: Show all log entries for a single quest
- ShowQuestTargets: Show current quest targets
- MoveToQuestTarget: Move player to current quest target.
- StartAllQuests: Starts all quests
- CompleteAllQuestStages (caqs): Sets all quest stages
- SetConsoleScopeQuest: Sets the scope quest for all console functions. No param clears current scope quest.
- Quest: Toggle Quest Event Info
- SetDebugQuest: Sets the quest to be the only one startable for its event type.
- SetQuestAliasLogging: Turns alias logging on/off for a quest.
- PrintQuestSceneInfo: Prints to the Quest Inf file the current state of scenes.
- PrintQuestSceneInfo: Prints to the Quest Inf file the current state of scenes.
- CallQuestFunction (cqf): Calls a papyrus function on a quest. Second parameter is the function, the rest are parameters
- StartRobotQuestTester (srqt): Starts the quest testing robot on the player
- PauseRobotQuestTester: Pauses or resumes the quest testing robot on the player
- FailAllObjectives: Fail all of a quest's objectives
- StartQuest: Tries to start the given quest (optionally can specify 1 after the quest to indicate a force-start).
- StopQuest: Stops the given quest.
- GetQuestRunning (GetQR): Is the given quest running?
- SetStage: Sets a quest stage using the Papyrus mechanisms to ensure fragments and stages don't fire off early if the quest isn't started.
- GetStage: What stage is the given quest in?
- GetStageDone: Is the given quest past the given stage?
- CompleteQuest: Sets the specified quest to the "completed" state.
- StartScene: Starts the Scene in a quest with the given ID.
- StopScene: Stops the Scene in the Quest with a given id.
- IsScenePlaying: Tells if a scene on a quest is active.
- ForceRefIntoAlias: Force the calling ref into the specified alias on the scope quest.
- EmptyRefAlias: Clear the ref currently in the specified alias on the scope quest.
- ShowQuestObjectives (SQO): Shows the list of current quest objectives
- GetIsCurrentLocationAlias: Is the ref currently in the given location of our owner quest?
- CompleteAllObjectives: Complete all of a quest's objectives
- ResetQuest: Resets the specified quest.
- SetQuestDelay: Adds a specified script processing delay for the given quest.
- GetQuestCompleted (GetQC): Has the given quest been completed?
- ShowQuestStages (SQS): Prints quest stages for the specified quest into the console.
- KillQuestUpdates (KQU): Removes all quest updates from the UI.
- GetIsAliasRef: Is the ref the given alias ref in our owner quest?
- GetIsEditorLocationAlias: Is the ref's editor loc in the given alias location of our owner quest?
- GetAliasedRef: Gets the ref currently in the given alias on our owner quest.
- GetVMQuestVariable: Gets a value out of a Papyrus script (called on a specific reference or quest).
- UpdateQuestInstanceGlobal: Updates the value for the given global in the given quests current instance data.
- ForceLocationIntoAlias: Force the given location into the specified alias on the scope quest.
- HasValidRumorTopic: See if a Ref has a valid Rumor topic to say for a particular quest or for any quest.
- GetQuetStarting (GetQS): Is the given quest starting?
