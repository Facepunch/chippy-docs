# Player

## Spawning

In the stage config, you can declare a `player` structure with the data path and position of the player ship.

```json
"player": {
    "path":"player/defaultPlayer",
    "spawnPos": "vec2(0f, -40f)",
},
```

## Config

## Overriding Default Player

To create a custom player that only changes certain things, you can `#include` the default player and override specific properties.

```json
{
    "#include":"player/defaultPlayer",
    "gun":"player/gun/double", // override the default gun
}
```

### Body

## Behaviour

## Custom Variables

## Params

## Guns

### Gun Params

## Debugging