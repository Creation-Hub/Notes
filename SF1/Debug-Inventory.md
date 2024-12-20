### Command: `ShowInventory`
> Shows reference inventory [1 = Show Armor Addons]
```
ShowInventory [int]
```
Shows the selected console reference's inventory.
When provided with the integer parameter value of `1`, will shows the target inventory with Armor Addons included.


### Command: `ShowInventoryVars` (`siv`)
> Shows reference inventory script data
```
ShowInventoryVars (siv)
```
Shows the selected console reference's inventory variable script data.


### Command: `reference.AddItem`
> Adds the specified item to the inventory/container of the selected reference.
```
<reference>.AddItem <form-id-item> [int-quantity]
```
The `int-quantity` is optional and defaults to 1.


### Command: `reference.RemoveItem`
> Remove item from ref object.
```
<reference>.RemoveItem <form-id-item>
```


### Command: `reference.RemoveAllItems`
> Removes all items from this reference's inventory.
> Optionally places them into the specified container (can also specify 1 after the container to change ownership of the items, and another 1 after that to ignore container weight limits).
```
<reference>.RemoveAllItems
```


### Command: `reference.RemoveMe`
> Removes the item from a container or character's inventory and optionally places it into the given container.
```
<reference>.RemoveMe
```


### Command: `reference.Drop`
> Forces the reference to drop the specified item.
```
<reference>.Drop
```


### Command: `reference.DropMe`
> Drops the item from a container or character's inventory.
```
<reference>.DropMe
```


### Command: `reference.DuplicateAllItems`
> Duplicates and copies all items from the current reference's inventory/container into the given target inventory/container.
```
<reference>.DuplicateAllItems
```


### Command: `reference.SetShowQuestItems`
> Shows (1) or hides (0) quest items in the inventory.
```
<reference>.SetShowQuestItems
```


### Command: `reference.OpenActorContainer`
> Open the container of a teammate so you can take things or add them.
```
<reference>.OpenActorContainer
```


### Command: `reference.GetInContainer`
> Is this ref currently in the param ref?
```
<reference>.GetInContainer
```


### Command: `reference.GetUsedWeightCapacityConditionFunction`
> Get the used weight capacity for actors, ships, containers. 1.0f is 100%
```
<reference>.GetUsedWeightCapacityConditionFunction
```


### Command: `reference.AddToContainer`
> Add the reference called on to the given container reference.
```
<reference>.AddToContainer
```


### Command: `reference.GetContainer`
> Gets the ref ID for the current reference's container.
```
<reference>.GetContainer
```


### Command: `reference.ResetContainer`
> Resets the currently selected container, or if you specify "1", then it'll reset all containers.
```
<reference>.ResetContainer
```


### Command: `reference.ResetInventory`
> Resets the inventory of the current actor.
```
<reference>.ResetInventory
```


### Command: `reference.MoveContainerContentToUnfilledContainers`
> Transfer container's content down the line to unfilled containers.
```
<reference>.MoveContainerContentToUnfilledContainers
```


### Command: `reference.IsCarryable`
> Returns true if the ref can be picked up and added to a container.
```
<reference>.IsCarryable
```


### Command: `reference.GetInventoryValue`
> Gets the total value of the inventory of the given ref.
```
<reference>.GetInventoryValue
```


### Command: `reference.GetItemCount`
> How many of the specified item does the reference have?
```
<reference>.GetItemCount
```


### Command: `reference.GetGold`
> How much gold/currency does the specified reference have?
```
<reference>.GetGold
```
