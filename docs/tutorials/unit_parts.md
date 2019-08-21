# Unit Parts

A section of pixels can be grouped together as a "part" or "pixelgroup". Parts have a single health pool and can only be destroyed as a whole.

## Config

- corePath
- spritePath
- hp

## Placing
- size
- placements
- different sizes for same core



## Requirements

### Ropes

## Lasers

## Callbacks

You may want to call Actions at from a unit part.

```json
{
    "onSpawn":[
        // called when status effect is started (gains its first level)
        { "action": "CallMethod", "target":"stage", "method": "ShakeCamera", "params": { "strength": 3, "time": 0.5, "easingType": "QuadOut" }},
    ],    

    "onUpdate":[ /* called each frame while part is active */ ],
	"onDestroy":[ /* called when part is destroyed */ ],
	"onHit":[ /* called when part hit by bullet or laser */ ],
	"onHitProtected":[ /* called when part hit by bullet or laser and has other part shielding it */ ],
},
```

## Params

## Cores

### Config

## Sprites

### Config

## Non-Rectangle Parts