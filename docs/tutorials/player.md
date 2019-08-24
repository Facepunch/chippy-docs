# Player

!!! info
	[Properties & Methods](../../SpaceUsurper/Player)
    
    [Full json config](../../SpaceUsurper/PlayerData)

## Config

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

### Body

## Behaviour

## Custom Variables

## Params

## Guns

!!! info "Player gun info"
	[Properties & Methods](../../SpaceUsurper/PlayerGun)
    
    [Full json config](../../SpaceUsurper/PlayerGunData)

### Gun Params

## Debugging