# Log Action

<small>**Namespace**: SpaceUsurper</small>

Write a message to the game's log file. Can be useful for debugging.

<small>**Inheritance**: [Object](https://docs.microsoft.com/en-us/dotnet/api/system.object?view=netframework-4.5) → [FsmAction](FsmAction.md) → Log</small>

## Examples

!!! example
    The following example prints a greeting, then the current player position.
    ``` json...
    { "action": "Log", "message": "Hello world!" },
    { "action": "Log", "message": "The player is at: ${playerPos}" },
    ...```

## Examples

!!! example
    The following example prints a greeting, then the current player position.
    ``` json...
    { "action": "Log", "message": "Hello world!" },
    { "action": "Log", "message": "The player is at: ${playerPos}" },
    ...```

## Properties

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [`message`](Log/message.md) | Message to write. | 

</div>

