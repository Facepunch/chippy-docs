# Player

!!! info
	[Properties & Methods](../../SpaceUsurper/Player)
    
    [Full json config](../../SpaceUsurper/PlayerData)

## Overriding Default Player

To create a custom player that only changes certain things, you can `#include` the default player and override specific properties.

```json
{
    "#include":"player/defaultPlayer",
    "gun":"player/gun/double", // override the default gun
}
```

Then, in your stage config, reference your new player config:

```json
{
    "player": {
        "path":"player/customPlayer",
        "spawnPos": "vec2(0f, -50f)",
    },
}
```

### Physics Elements

You may want different types of forces that can be applied to players.

For each type of you create, you can define `frictionPercentMin` (the minimum friction) and `frictionPercentMax` (the max friction). You also choose the `topSpeed` - as the player's velocity increases to `topSpeed`, the friction applied to them increases from the min friction to the max.

```json
{
    "physicsElements": {
        "impulse": { "frictionPercentMin": 0.05, "frictionPercentMax": 0.3, "topSpeed": 100, },
        "shoot_force": { "frictionPercentMin": 0.2, "frictionPercentMax": 0.5, "topSpeed": 50, },
        "boost": { "frictionPercentMin": 0.04, "frictionPercentMax": 0.15, "topSpeed": 100, },
    },

    "onHit": [
        { "action": "CallMethod", "target": "player.Movement", "method": "AddPhysicsForce", "params": { "name": "impulse", "force":"damageDir * 50f" }},
    ],
}
```

## Guns

!!! info "Player gun info"
	[Properties & Methods](../../SpaceUsurper/PlayerGun)
    
    [Full json config](../../SpaceUsurper/PlayerGunData)

    [Script Params](../../SpaceUsurper/PlayerGunData/#script-parameters)


## Script Parameters

These parameters can be used inside any scriptfunc in the Player (including any of the [Stage script params](../../SpaceUsurper/StageData/#script-parameters))

!!! info
    [Script Params](../../SpaceUsurper/PlayerData/#script-parameters)

## Debugging

`debugVector`: draws a 2d vector from the player's position <br>
`debugText`: displays a string below the player's position (use `${NAME}` for properties)
