# Tags
```
SelfOnly
Private
Protected
```


# Guards

```papyrus
Guard MyGuard
int MyValue = 0 RequiresGuard(MyGuard)

Function Update()
	LockGuard(MyGuard)
		MyValue += 1
	EndLockGuard
EndFunction
```


## ProtectsFunctionLogic
The `ProtectsFunctionLogic` flag is optional on `Guard` declaration.
```papyrus
Guard MyGuardName ProtectsFunctionLogic

Function Update1()
    LockGuard MyGuardName
        ; do work
    EndLockGuard
EndFunction

Function Update2()
    LockGuard MyGuardName
        ; do work
    EndLockGuard
EndFunction
```


## RequiresGuard
The `RequiresGuard` guards a variable by requiring use within a `LockGuard`.
Multiple `Guard` elements can be specified at once for a single `LockGuard`.
Can be applied to properties and variables.

```papyrus
Guard MyGuard1
int MyValue1 RequiresGuard(MyGuard1)

Guard MyGuard2
int MyValue2 RequiresGuard(MyGuard2)

Function CalculateReward()
  	LockGuard MyGuard1, MyGuard2
		MyValue1 += 1
		MyValue2 += 1
	EndLockGuard
EndFunction
```
