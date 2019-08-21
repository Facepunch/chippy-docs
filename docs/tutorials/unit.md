# Units

A **unit** is anything that has pixels. <br>
Bosses are units, minions are units, shield containers are units, etc.

## Config

## Movement

### Avoiding Other Units
 
### Level Boundary

## Forms

### Callbacks

You may want to call Actions at certain points while a unit form is active.

```json
{
    "onSpawn":[
        // called when status effect is started (gains its first level)
        { "action": "CallMethod", "target":"stage", "method": "ShakeCamera", "params": { "strength": 3, "time": 0.5, "easingType": "QuadOut" }},
    ],    

    "onFormRespawn":[ /* called when form has finished spawning pixels */ ],
    "onUpdate":[ /* called each frame this unit is active and not dormant or hidden, and on this form*/ ],
	"onDestroy":[ /* called when form is destroyed */ ],
	"onHidden":[ /* called when unit has becomes hidden */ ],
	"onPixelHit":[ /* called when a pixel of this form is hit by a bullet */ ],
	"onPixelHitByLaser":[ /* called pixel of this form is hit by a laser */ ],
	"onPixelDestroyed":[ /* called pixel of this form is destroyed */ ],
	"onPartHit":[ /* called when a part of this form is hit by a bullet */ ],
	"onPartHitByLaser":[ /* called when a part of this form is hit by a laser */ ],
	"onPartDestroyed":[ /* called when a part of this form is destroyed */ ],
	"onImplodeStart":[ /* called when this form starts imploding (core has taken lethal damage) */ ],
	"onImplodeUpdate":[ /* called while this form is imploding */ ],
	"onImplodeFinish":[ /* called when this form finishes imploding (and dies) */ ],
	"onPlayerHit":[ /* called when player takes damage but does not die */ ],
	"onPlayerDie":[ /* called when player takes lethal damage */ ],
	"onPlayerActivateStatus":[ /* called when player uses an item */ ],
	"onPlayerStatusLevelChanged":[ /* called when a status effect changes level */ ],
	"onDormantStart":[ /* called when unit becomes dormant (don't simulate) */ ],
	"onDormantEnd":[ /* called when unit is no longer dormant */ ],
	"onDormantUpdate":[ /* called while unit is dormant, according to "dormantUpdateInterval" */ ],
},
```

## Pixels

### PixelType

- normal
- invulnerable
- explosive


### Importing Pixels

### Texture

### Pixel Effects

- Splash Damage
- Transform Line
- Transform Ring
- Spark

### Pixel Chunks

## Animations

### Config

### Playback

## Behaviour

### Charging Patterns

## Callbacks

## Custom Variables

Custom variables can be defined in the `properties` structure.

```json
{
	"properties": {
	    "loopNum": { "type": "Int", },
	    "pixel": { "type": "PixelData", },
	    "revengeCounter": { "type": "Int", },
	    "shootTimer": { "type": "Float", "value":6, },
	    "hasShot": { "type": "Bool", },
	},
}
```

These values can be used in any script func by the unit.

To modify them, use the SetValue method:

```json
{ "action": "SetValue", "name": "revengeCounter", "value": "revengeCounter + 1" },
```

## Params

## Speech Bubbles

## Debugging