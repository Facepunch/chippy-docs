# Condition Action

<small>**Namespace**: SpaceUsurper</small>

Evaluates a condition before deciding which set of actions to perform next.

<small>**Inheritance**: [Object](https://docs.microsoft.com/en-us/dotnet/api/system.object?view=netframework-4.5) → [FsmAction](FsmAction.md) → Condition</small>

## Examples

!!! example
    The following example prints `"You got lucky!"` with a 20% chance, and
    otherwise prints `"Better luck next time!"`.
    ``` json
    ...
    { "action": "Condition", "condition": "rand.Chance(0.2)",
        "true": [
            { "action": "Log", "message": "You got lucky!" }
        ],
        "false": [
            { "action": "Log", "message": "Better luck next time!" }
        ]
    },
    ...
    ```

## Properties

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [`condition`](Condition/condition.md) | Condition to evaluate, the result of which will decide which set of actions to perform. | 
| [`false`](Condition/false.md) | Optional actions to run if the `condition` evaluated to `false`. | 
| [`true`](Condition/true.md) | Optional actions to run if the `condition` evaluated to `true`. | 

</div>

