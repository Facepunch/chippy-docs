# Units

A **unit** is anything that has pixels. <br>
Bosses are units, minions are units, shield containers are units, etc.

## Config

The config type for units is of the type `UnitData`.

The basic structure looks like this:

```json
{
	"properties": {
		// custom variables defined here
	},

	"behaviour":".fsm", // references a finite-state-machine in the same config file

	"baseForm":{
		// properties common to each form
	},

	"forms": [
		{
			// - each form specifies where its pixel source & anim files are located
			// - defines pixel types
			// - defines parts
		},
	],

	"fsm":[
		"form0": {
			// the actions in the behaviour state machine
		},
	],
}
```

## Forms

Most of the properties for a unit can be defined for each form.<br>
When one form is destroyed, the unit will respawn in their next form.

The config type for unit forms is of the type `FormData`.
Each unit config should contain a list of forms:

```json
{
	"forms": [
		{
			// form 0
		},
		{
			// form 1
		},
	],
}
```

### Base Form

Any properties defined for the `base form` of a unit apply to all of its forms, unless overridden (they're essentially the same thing as the `#include` functionality, which can be used instead).

```json
{
	"baseForm": {
        "baseHp":18,
		"onUpdate":[
			// actions
		],
	},

	"forms": [
		{
			// form 0
			"baseHp":25,
		},
		{
			// form 1
			"onUpdate":[
				// different actions
			],
		},
	],
}
```

`form 0` overrides the base pixel health of the base form while keeping its `onUpdate` actions, while the next form keeps the base form's `baseHp` but overrides its `onUpdate` actions.

## Pixels

Each form needs to specify the location of the pixel `source` file and the directory where its `anim` files are located.<br>

Each unit form should have **one** source file, and **one or more** anim files.<br>

```json
{
	"forms":[
		"pxcSource":"octopus/pxc/boss/form0/source",
		"pxcAnimDir":"octopus/pxc/boss/form0",
		// ...
	],
}
```

Each form should also set some properties for its pixels.

```json
{
	"forms":[
		// ...

		"pixels": [
			{
				"range": "all", // these properties will apply to all pixels
				"hp":20,
				"sfxHit": "PixelHit",
				"sfxDestroy": "PixelDestroy",
				"sfxDisconnect": "PixelDisconnect",
			},
			{
				"range": "part('core')", // these properties will apply to pixels in the "core" part, and override previous properties
				"color": "#668855"
			},
			{
				"range": "range(616, 771)", // these pixels apply to a range of assigned numbers (generally a certain color), and override previous properties
				"hp":40,
				"sfxHit": "Thud3",
			},
			{
                "range": "range(72, 317)",
                "pixelType":"Invulnerable",
                "sfxHit": "MetalHit",
            },
		],

		// ... 
	],
}
```

To find the `range` of a certain type of pixel:
> 1) Load your animation file in the [PxcEditor](pxc_editor.md).

> 2) Decide which pixel type you want to get the range of - in this case, the purple colored pixels are going to be invulnerable.

<img src="https://files.facepunch.com/ryleigh/1b2211b1/PxcEditor_2019-08-22_20-39-47.png" />

> 3) Hold the ++c++ key and right click one of the pixels to select all other pixels of the same color.

<img src="https://files.facepunch.com/ryleigh/1b2211b1/PxcEditor_2019-08-22_20-38-32.png" />

> 4) Hold the ++shift+c++ keys and right click one of the **other** purple pixels to add all pixels of that shade to the selection.

<img src="https://files.facepunch.com/ryleigh/1b2211b1/PxcEditor_2019-08-22_20-39-01.png" />

> 5) Press ++"Middle Mouse Button"++ or the `=` button on the far right of the toolbar to toggle showing pixel assignments.

<img src="https://files.facepunch.com/ryleigh/1b2211b1/PxcEditor_2019-08-22_20-46-28.png" />

> 6) The range (in this case `244, 1923`) should now be copied to your clipboard. Paste it into the pixel config. If your range isn't a neat sequence, you probably didn't assign your pixels on a color-by-color basis.

### Pixel Types

When specifying properties for pixels, you can choose between a few fundamental types.

Pixel Type | Summary
:----------- |:-------------
`Normal` | pixel has a certain amount of hp until it is destroyed
`Explosive` | a small amount of damage will trigger this pixel to explode and destroy adjacent pixels
`Invulnerable` | normal damage won't affect this pixel (though Explosive pixels will)

## Parts

Each kind of part used in your enemy needs to be defined in the form's config.

```json
{
	"forms":[
		{
			"parts":{
				"core": {
                    "corePath": "misc/core/octopus/core0",
                    "size": 12,
                    "placements": [ 0 ],
                    "hp": 900,
                    "requires": [ "gun", ],
                },
                "gun": {
                    "corePath": "misc/core/octopus/smallGun",
                    "size": 7,
                    "placements": [ 73, 89 ],
                    "hp": 500,
                },
			}
		},
	],
}
```

For more info check the [Unit Parts](unit_parts.md) page.

## Animations

### Importing

Animations should be declared in the unit form's `anims` property.

These `anim` json files should be located in the `pxcAnimDir` you specified for the unit form.

```json
{
	"forms": [
		{
			// ...
			"anims": {
				"spawn": { "time": 0.5, "easingType": "QuadIn", "next": "idle" },
				"idle": { "time": 1.25, "easingType": "Linear" },
				"idle_2": { "time": 1.5, "easingType": "SineInOut" },
			},
		},
	],
}
```

### Playback

Unit anims can be played with an Action.<br>

Played anims will be added to the end of a queue, and played when earlier animations have been finished.

```json
{ "action": "CallMethod", "target": "unit", "method": "PlayAnim", "params": { "name": "spawn", }},
```

There are a number of optional parameters as well:

```csharp
public void PlayAnim(string name, bool reverse = false, bool forceChange = false, LoopMode loopMode = LoopMode.None, EasingType easingType = EasingType.None, bool playNext = false)
```

Parameter | Summary
:----------- |:-------------
`reverse` | whether anim should start from the end and play backwards     
`forceChange` | if true, end current animation immediately to play new one (may cause issues?!)
`loopMode` | override the loop mode saved with the anim file
`easingType` | override the anim's easing mode specified in the import settings
`playNext` | if true, play new anim next instead of after all queued anims

## Behaviour

The behaviour state machine should be specified in the `behaviour` unit property.

```json
"behaviour": ".fsm",
```

The unit will begin in the first state, `inactive`.

When the first form of the unit finishes spawning, it will try to switch to a state called `form0`. In this case, `form0` isn't itself a state, but a collection of states, and the first one will be chosen.

When the unit's second form finishes spawning, it will switch to the first state in `form1`.


```json
{
	"fsm": {
		"inactive": [
			{ "action": "Wait"}
		],
		"form0": {
			"state 0": [
				{ "action": "Wait", "time": 1 },
			],
			"state 1": [
				{ "action": "Goto", "state": "state 0" },
			],
		},
		"form1": {
			"state 0": [
				{ "action": "Wait", "time": 1 },
			],
			"state 1": [
				{ "action": "Goto", "state": "state 0" },
			],
		},
		
	},
}
```

!!! tip
	Holding the ++h++ key will show the current state of a unit.

### Charging Patterns

When you want a unit to shoot a pattern, usually you'll **charge** it from their core or another part. This will cause the part to glow and look in the pattern direction as it leads up to firing.

```json
{ "action": "CallMethod", "method": "ChargePattern", "params": { "path": "octopus/pattern/lazyBullets.1", "partType": "side", "chargeTime": 1, "dir":"playerPos - partPos", }},
```

Let's spread that out for clarity:

```json
{ 
	"action": "CallMethod", 
	"method": "ChargePattern", 
	"params": { 
		"path": "octopus/pattern/lazyBullets.1", 
		"partType": "side", 
		"chargeTime": 1, 
		"dir":"playerPos - partPos", 
	}
},
```

It can be convenient to choose between multiple patterns in the same `ChargePattern` action.<br>
Instead of using the `path` parameter, use the `paths` parameter to list the options, and `pathIndex` to choose which to use.

```json
{ "action": "CallMethod", "method": "ChargePattern", "params": { "paths": [ "octopus/pattern/lazyBullets.1", "octopus/pattern/lazyBullets.2", "octopus/pattern/lazyBullets.3", "octopus/pattern/lazyBullets.4" ], "pathIndex":"numShotPatterns % 4", "partType": "side", "chargeTime": 1, "dir":"playerPos - partPos", }},
```

There are some optional `ChargePattern` parameters available:

Parameter | Type | Summary
:----------- |:------------- |:-------------
`path` | PatternData | the path of the pattern to shoot
`paths` | List of PatternData | the path of the pattern to shoot
`pathIndex` | int | which index in `paths` to use
`partType` | string | which unit part(s) to fire from
`partSelect` | PartSelectMode | how to choose next part of `partType`
`randomDegrees` | float | change pattern angle by up to this much
`mirrorMode` | MirrorMode | used to create extra mirrored patterns
`flip` | FlipPatternMode | used to make patterns symmetrical across an axis
`chargeTime` | float | how long to charge before shooting
`dir` | Vector2 func | starting pattern direction
`sizeMultiplier` | float | scaling applied to every bullet in pattern
`numVolleysAddition` | int | adjust amount of volleys
`numBulletsAddition` | int | adjust amount of bullets in each volley
`shootDelayModifier` | float | scaling applied to shoot delay time
`maxDist` | float | don't shoot pattern if part is too far from player

## Movement

Similar to how bullets work, units can choose to be moved by velocity or moved toward a target position.

### Velocity

```json
{
	"forms":[
		{
			"moveMode":"Velocity", // not necessary to specify since it's the default
			"accelVector":"normalize(playerPos - unitPos) * 0.5f", // move toward player
		}
	],
}
```

### Target 

```json
{
	"forms":[
		{
			"moveMode":"Target",
			"targetPos":"playerPos", // move toward player
			"posLerpSpeed":0.05, // unit moves 5% of the current distance to player each frame
		}
	],
}
```

### All 

Setting `moveMode` to `All` will apply both acceleration and easing toward the target position. Not sure if this mode is useful for anything.

```json
{
	"forms":[
		{
			"moveMode":"All",
			"accelVector":"vec2(0f, 2f)", // move upwards
			"targetPos":"playerPos", // move toward player
			"posLerpSpeed":0.05, // unit moves 5% of the current distance to player each frame
		}
	],
}
```

The movement mode and the functions can be set with Actions such as `SetMovementModeFunc`, `SetAccelVectorFunc`, `ClearAccelVectorFunc`, etc.

### Avoiding Other Units

Generally you want to prevent units from overlapping eachother. You can define circular hitboxes that repel other units.

<img src="https://files.facepunch.com/ryleigh/1b2111b1/Unity_2019-08-21_21-16-28.png" />

```json
{
	"forms": [
		{
			// how strongly the unit's circles are repelled by other units
			"avoidUnitStrength":1,

			// how strongly the unit's circles repel other units' circles
        	"repelUnitStrength":10,

			"repulsionCircles": [
                {  "offset":"vec2(0, 7f)", "radius":18, // strength is 1 by default},
                {  "offset":"vec2(-14.5f, -7f)", "radius":12, "strength":1.5, },
                {  "offset":"vec2(14.5f, -7f)", "radius":12, "strength":1.5, },
            ],
		},
	],
}
```

!!! tip
	Hold the `H` key to see the repulsion circles of units.

### Level Boundary

By default, a unit does not try to stay in the level bounds, and is removed when it completely leaves the bounds.

```json
{
	"disableOutOfBounds":false, // this unit does not disable when it goes out of bounds (default is true)

	"forms": [
		{
			// define new bounds for this unit
			"bounds":"rect(-stageWidth * 0.5f, -stageHeight * 0.5f, stageWidth, stageHeight * 0.75f)",

			// how strongly the unit adds force to stay within its bounds
			"stayInBoundsStrength":10,
		},
		{
			// this form only stays in bounds on the left and right sides
			"stayInBoundsStrengthLeft":10,
			"stayInBoundsStrengthRight":10,
			"stayInBoundsStrengthUp":0,
        	"stayInBoundsStrengthDown":0,
		},
	],
}
```

<img src="https://files.facepunch.com/ryleigh/1b2111b1/Unity_2019-08-21_23-11-36.png" />

!!! tip
	Hold the `H` key to see the bounds of units.

## Facing

### Target

```json
{
	"forms":[
		{
			"facingMode":"Target",
            "targetFacingAngle":"vecToAngle(playerPos - unitPos)", // look at player
            "facingLerpSpeed":0.05, // rotate 5% of the way to target angle per frame
		}
	],
}
```

### AutoRotate

```json
{
	"forms":[
		{
			"facingMode":"AutoRotate",
            "rotationSpeed":-100,
		}
	],
}
```

## Texture

## Pixel Effects

- Splash Damage
- Transform Line
- Transform Ring
- Spark

## Pixel Chunks

## Callbacks

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

```json
{ "action": "Repeat", "count": "revengeCounter", "inner": [
	// ...
]},
```

To modify them, use the SetValue method:

```json
{ "action": "SetValue", "name": "revengeCounter", "value": "revengeCounter + 1" },
```

## Params

## Speech Bubbles

Unit's `SpawnBubble` creates a speech bubble coming out of a part.

```json
{ "action": "CallMethod", "method": "SpawnBubble", 
	"params": { 
		"text": "Hihihi", 
		"partType":"core", 
		"lifetime": 1,
		"fillColor": "color(0.2f, 0.1f, fastSin(stageTime * PI * 2f) * 0.2f + 0.5f, 0.8f)", 
		"borderColor": "color(0.75f, 0.75f, fastSin((stageTime + 0.5f) * PI * 2f) * 0.05f + 0.95f, 0.66f)", 
		"borderWidth": "fastSin(stageTime * PI * 3f) * 2f + 4f",
		"textColor":"lerp(color(1f, 1f, 1f), color(0.75f, 0.75f, 1f), 0.5f + fastSin(stageTime * PI * 12f) * 0.5f)",
		"font":"Quantico",
		"fontSize":33,
	}
},
```

<img src="https://files.facepunch.com/ryleigh/1b2311b1/Chippy_2019-08-23_20-50-13.png" />

## Debugging

`debugVector`: draws a 2d vector from the unit's position <br>
`debugText`: displays a string below the unit's position (use `${NAME}` for properties)