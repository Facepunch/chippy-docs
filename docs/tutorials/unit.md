# Units

A **unit** is anything that has pixels. <br>
Bosses are units, minions are units, shield containers are units, etc.

!!! info
	[Properties & Methods](../../SpaceUsurper/Unit)

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

??? abstract "Example json file of a simple 2-form boss"
	```json
	{
		// custom variables for this boss
		"properties": {
			"loopNum": { "type": "Int", "value": 0 }, // the starting value is already 0 by default, but it's specified here for clarity
		},

		"behaviour": ".fsm", // specify where to find the behaviour state machine definition (the leading "." indicates its inside the same json object)

		// properties defined in baseForm will be used for all forms unless overridden
		"baseForm": {
			"baseHp":18, // default hp for each pixel

			// when player is hit by a bullet, this handler is called
			"onPlayerHit":[
				{ "action": "CallSubroutine", "target":"unit", "path": ".speech.sub", "params": { "message": "#octopus.boss.player_hit_bullet", "chance":0.1, }},
			],
		},

		"forms": [
			{   
				// FORM 0 CONFIG

				"pxcSource": "octopus/pxc/boss/form0/source", // the location of the pixel source file for this form
				"pxcAnimDir": "octopus/pxc/boss/form0", // the directory where the anim files associated with the source file are located
				
				// list anim files to use (from the directory specified for pxcAnimDir)
				"anims": {
					"idle": { 
						"time": 1.25, // how long each playthrough of the anim is
						"easingType": "Linear", // how to ease through the anim frames
					},
				},

				// pixel properties
				"pixels": [
					{   
						"range": "all", // apply these properties to all pixels
						"sfxHit": "FleshHit",
						"sfxDestroy": "FleshDestroy",
						"sfxDisconnect": "FleshDisconnect",
						"hitGlow":1.4,
						"hitFlashTime":1,
					},
				],

				// define parts
				"parts": {
					"core": {
						"corePath": "misc/core/octopus/core0",
						"size": 8, // a size of 8 means this part is an 8x8 square
						"placements": [ 0 ],
						"hp": 900,
						"requires": [ "mid", "side" ], // this part cant be damaged until the required parts are destroyed
						"onHit": [
							{ "action": "CallMethod", "target": "stage", "method": "ShakeCamera", "params": { "strength": 0.25, "time": 0.33, "easingType": "QuadOut" }},
						],
					},
					"mid": {
						"corePath": "misc/core/octopus/smallGun",
						"size": 4,
						"placements": [ 73, 89 ],
						"hp": 500,
						"onDestroy": [
							// spawn a powerup
							{ "action": "CallMethod", "target":"stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/powerup0Mid", "pos": "partPos", "angle":"vecToAngle((playerPos + playerVel * 0.5f) - partPos)",  }},
						],
					},
					"side": {
						"corePath": "misc/core/octopus/smallGun",
						"size": 3,
						"placements": [ 64, 105 ], 
						"hp": 500,
						"onDestroy": [
							{ "action": "CallMethod", "target":"stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/powerup0Side", "pos": "partPos", "angle":"vecToAngle((playerPos + playerVel * 0.5f) - partPos)",  }},
						],
					}
				},

				// this handler is called each frame
				"onUpdate": [
					// continually re-align the rotation of the boss
					{ "action": "CallMethod", "method": "AimTowards", "params": { "facingAngle":0, "rotPercent":0.125, }},
				],

				// this handler is called when the form is destroyed
				"onDestroy": [
					{ "action": "CallMethod", "target":"stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/powerup0Core", "pos": "corePos", "angle":"vecToAngle((playerPos + playerVel * 0.5f) - corePos)",  }},

					// controller rumble
					{ "action": "CallMethod", "target": "player", "method": "Vibrate", "params": { "pos":"unitPos", "strength": 1, "time": 0.25, "maxDist": 150, "horizThreshold": 40 }},

					// camera shake
					{ "action": "CallMethod", "target": "stage", "method": "ShakeCamera", "params": { "strength": 5, "time": 0.5, "easingType": "QuadOut" }},

					// slow time for a moment
					{ "action": "CallMethod", "target": "stage", "method": "AddTimeScale", "params": { "scale": 0.5, "time": 0.5, "easingType": "CubicIn" }},
				],

				// this handler is called when the player dies while this form is active
				"onPlayerDie":[
					// a chance to show a speech bubble
					{ "action": "CallSubroutine", "target":"unit", "path": ".speech.sub", "params": { "message": "#octopus.boss.player_die_0", "chance":0.2, }},
				],
			},
			{ 
				// FORM 1 CONFIG

				"pxcSource": "octopus/pxc/boss/form1/source",
				"pxcAnimDir": "octopus/pxc/boss/form1",
				"spawnDelay":2.2, // time to wait before spawning this form
				"coreSpawnTime":1.75, // time to spawn the core
				"moveMode":"Target", // unit moves toward target position, instead of using velocity
				"targetPos":"unitSpawnPos + vec2(sin(stageTime * 0.5f), cos(stageTime * 0.5f)) * 2f", // unit will bob around a central point
				"posLerpSpeed":0.01, // how fast the unit lerps toward the target position

				"anims": {
					"spawn": { "time": 1, "easingType": "QuadIn", "next": "idle" },
					"idle": { "time": 1.25, "easingType": "Linear" },
				},
				"pixels": [
					{   
						"range": "all", 
						"sfxHit": "FleshHit",
						"sfxDestroy": "FleshDestroy",
						"sfxDisconnect": "FleshDisconnect",
						"hitGlow":1.4,
						"hitFlashTime":1,
					},
					{ 
						"range": "part('core')", 
						"color": "color(1f, 0f, 0f)", // this property applies to pixels defined in the "core" part below
					},
					{  
						"range": "part('mid')",  
						"color": "color(1f, 0f, 0f)", // this property applies to pixels defined in "mid" parts below
					},
					{  "range": "part('side')", "color": "color(1f, 0f, 0f)", },
					{  "range": "part('bot')", "color": "color(1f, 0f, 0f)", },
					{
						"range": "range(146,389)",
						"sfxHit": "Thump",
						"sfxDestroy": "MetalDestroy",
						"sfxDisconnect": "MetalDisconnect",
						"damagedColor": "color(0.175f, 1f, 0.35f) * 1.15f", // as the pixel loses hp, it changes toward this color
						"hp": 40, // override the baseHp for these pixels
						"hitGlow":1.2,
						"hitFlashTime":0.5,
					}
				],
				"parts": {
					"core": {
						"corePath": "misc/core/octopus/core1",
						"size": 8,
						"placements": [ 0 ],
						"hp": 1000,
						"requires": [ "mid", "side", "bot" ],
						"onHit": [
							{ "action": "CallMethod", "target": "stage", "method": "ShakeCamera", "params": { "strength": 0.25, "time": 0.33, "easingType": "QuadOut" }},
						],
					},
					"side": {
						"corePath": "misc/core/octopus/smallGun",
						"placements": [ 
							{ "size": 3, "start": 128 }, 
							{ "area": 9, "start": 137 }, // you can specify "area" instead of "size", for irregularly shaped parts
						],
						"hp": 600,
						"onDestroy": [ 
							{ "action": "CallMethod", "target":"stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/powerup1Side", "pos": "partPos", "angle":"vecToAngle((playerPos + playerVel * 0.5f) - partPos)",  }},
						],
					},
					"bot": {
						"corePath": "misc/core/octopus/largeGun",
						"size": 4,
						"placements": [ 80, 112 ],
						"hp": 600,
						"onDestroy": [{ "action": "CallMethod", "target":"stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/powerup1Bot", "pos": "partPos", "angle":"vecToAngle((playerPos + playerVel * 0.5f) - partPos)",  }},],
					},
					"mid": {
						"corePath": "misc/core/octopus/largeGun",
						"size": 4,
						"placements": [ 64, 96 ],
						"hp": 600,
						"onDestroy": [{ "action": "CallMethod", "target":"stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/powerup1Mid", "pos": "partPos", "angle":"vecToAngle((playerPos + playerVel * 0.5f) - partPos)",  }},],
					}
				},

				// this handler is called immediately when the unit is spawned
				"onSpawn": [
					{ "action": "CallMethod", "target": "stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/effect/bgClouds.fgStart", }},
					{ "action": "CallMethod", "target": "stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/effect/bgClouds.fgOngoing", }},
					{ "action": "CallMethod", "target":"stage", "method": "SetGridColor", "params": { "color": "color(0f, 1f, 1f, 0.033f)", "time":1, "easingType":"QuadOut" }},
				],

				// this handler is called when the pixels finish respawning
				"onFormRespawn": [
					{ "action": "CallSubroutine", "target":"unit", "path": ".speech.sub", "params": { "message": "#octopus.boss.form_1", "chance":0.25, }},
				],

				"onUpdate": [
					{ "action": "CallMethod", "method": "Shake", "params": { "strength":"map(core.HpPercent, 1f, 0f, 0f, 0.175f, 'QuadIn')", "time":0, }},
					{ "action": "CallMethod", "method": "SetScale", "params": { "scale": "vec2(1f + sin(stageTime * 1.8f) * 0.03f, 1f + sin(stageTime * 1.8f) * 0.03f)" }},
					{ "action": "CallMethod", "method": "AimTowards", "params": { "facingAngle":0, "rotPercent":0.125, }},
				],

				// this handler is called when the unit's pixel is hit by a bullet
				"onPixelHit": [
					{ "action": "CallMethod", "target": "unit", "method": "Nudge", "params": { "vector":"bullet.FacingDirection * 0.15f", "time":0.25, "easingType":"QuadOut", }},
				],
				
				"onPlayerDie":[
					{ "action": "CallSubroutine", "target":"unit", "path": ".speech.sub", "params": { "message": "#octopus.boss.player_die_1", "chance":0.33, }},
				],
			},
		],

		// the state machine that handles the boss behaviour
		"fsm": {
			"inactive": [
				{ "action": "Wait", } // wait indefinitely
			],
			"form0": { // the name "form0" is important, when the first form of the unit finishes respawning, its behaviour state will be set to this
				// FORM 0
				"initial delay": [
					{ "action": "Wait", "time":2, },
				],
				"0": [
					{ "action": "CallMethod", "method": "ChargePattern", "params": { "paths": [ "octopus/pattern/lazyBullets.1", "octopus/pattern/lazyBullets.2", "octopus/pattern/lazyBullets.3", "octopus/pattern/lazyBullets.4" ], "pathIndex":"loopNum % 4", "partType": "mid", "chargeTime": 0.75, "dir":"playerPos - partPos", }},
					{ "action": "Wait", "time": 4, },
				],
				"1": [
					{ "action": "SetValue", "name": "loopNum", "value": "loopNum + 1" },
					{ "action": "Goto", "state": "0" },
				],
			},
			"form1": { // when the 2nd unit form finishes respawning, its behaviour state will be set to "form1"
				// FORM 1
				"initial delay 2": [
					{ "action": "SetValue", "name": "loopNum", "value": 0 },
	
					{ "action": "Wait", "time": 1 },
					{ "action": "CallMethod", "method": "ChargePattern", "params": { "path": "octopus/pattern/curseMineOrb", "partType": "core", "chargeTime": 1, "loopNum":"loopNum", "dir": "(playerPos + playerVel * 0.75f) - partPos", }},
					{ "action": "Wait", "time": 1 },
				],
				"0": [
					{ "action": "Condition", "condition": "loopNum > 0 && numShotPatterns % 2 == 0",
						"true": [ 
							{ "action": "CallMethod", "method": "ChargePattern", "params": { "paths": [ "octopus/pattern/spread.spokes1", "octopus/pattern/spread.spokes2", "octopus/pattern/spread.spokes3" ], "pathIndex":"numShotPatterns % 3", "partType": "side", "chargeTime": 1, "dir":"(playerPos + playerVel * 0.25f) - partPos", }},
							{ "action": "Wait", "time": 3, },
						],
						"false": [ 
							{ "action": "Repeat", "count": 2, "delay": 1.5, "inner": [
								{ "action": "CallMethod", "method": "ChargePattern", "params": { "path": "octopus/pattern/spread.1", "partType": "side", "chargeTime": 1, "dir":"(playerPos + playerVel * 0.25f) - partPos", }},
							]},
							{ "action": "Wait", "time": 2, },
						],},
				],
				"1": [
					{ "action": "SetValue", "name": "loopNum", "value": "loopNum + 1" },
					{ "action": "Goto", "state": "0" },
				],
			},
		},

		// subroutine to show a speech bubble and play a sound
		"speech.sub": {
			// the parameters we can pass in to the subroutine
			"parameters": {
				"this": { "type": "Unit" }, // this subroutine is intended to be run by Unit objects
				"message": { "type": "String" },
				"chance": { "type": "Float" },
			},

			"actions": [
				{ "action": "Condition", "condition": "rand.Float(0f, 1f) < 0.5f",
					"true": [ 
						{ "action": "CallMethod", "target":"unit.GetPart('core')", "method": "SpawnBubble", "ignoreNullRef": true, "params": { "text": "${message}", "partType":"core", "lifetime": 4, }},
						{ "action": "CallMethod", "target":"stage", "method": "PlaySfx", "params": { "sfxType": "OctopusBossSpeech", "pos":"unitPos", }},
					],},
			]
		},
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

!!! info "Unit form info"
    [Unit form json config](../../SpaceUsurper/UnitFormData)

### Base Form

Any properties defined for the `baseForm` of a unit apply to all of its forms, unless overridden (they're essentially the same thing as the `#include` functionality, which can be used instead).

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

!!! warning
	Some properties won't show your changes until you completely reload the level - restarting isn't enough.

	Press the ++g++ key to reload the level.

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
				// attack
			],
		},
		"form1": {
			"state 0": [
				{ "action": "Wait", "time": 1.5 },
			],
			"state 1": [
				// attack
			],
		},
		
	},
}
```

!!! tip
	Holding the ++h++ key will show the current state of a unit.

When finishing the last action in a state, the state machine will automatically move to the next state in the group.

When finishing the last state in a group of states, it will loop around to the first state in the group. 

For example, when ==form1.state&nbsp;1== finishes all its actions, playback will move back to ==form1.state&nbsp;0==.

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

!!! info
	The movement mode and the functions can be set with Actions such as `SetMovementModeFunc`, `SetAccelVectorFunc`, `ClearAccelVectorFunc`, etc.

### Avoiding Other Units

Generally you want to prevent units from overlapping eachother. You can define circular hitboxes that repel other units.

<img src="https://files.facepunch.com/ryleigh/1b2111b1/Unity_2019-08-21_21-16-28.png" />

```json
{
	"forms": [
		{
			"repulsionCircles": [
                {  "offset":"vec2(0, 7f)", "radius":18, // strength is 1 by default},
                {  "offset":"vec2(-14.5f, -7f)", "radius":12, "strength":1.5, },
                {  "offset":"vec2(14.5f, -7f)", "radius":12, "strength":1.5, },
            ],

			// how strongly the unit's circles are repelled by other units
			"avoidUnitStrength":1,

			// how strongly the unit's circles repel other units' circles
        	"repelUnitStrength":10,
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

## Handlers

You may want to call Actions at certain points while a unit form is active.

```json
{
    "onSpawn":[
        // called immediately when unit is spawned
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

## Unit Destruction

### Anchors

Individual pixels can set the `isAnchor` property to `true`. When non-anchor pixels or parts are disconnected from all anchor pixels, they will be destroyed.

### Cores

Generally, units should declare a part with the name =="core"==, though this isn't absolutely required.

The **core** part of a unit will automatically set all its pixels as anchors.

!!! note
	If a unit has no core (and no anchor pixels), it will handle destruction differently: whenever pixels become separated, the smaller of the separate pieces will be destroyed.

### Imploding

"Imploding" refers to the animation when a unit has received lethal damage to its core, but before it is destroyed.

<video controls width="100%"> <source src="https://files.facepunch.com/ryleigh/1b1111b1/2019-10-11_13-10-33.mp4" type="video/mp4" > </video>

In order for your unit to display this behaviour, it must define a few handlers in its form config:

```json
"baseForm": {
	// the time the imploding effect lasts
	"implodeTime":1.5,

	// called once, when the unit core takes lethal damage
	"onImplodeStart": [
		// play sounds, show speech bubbles, initialize variables
	],

	// called each frame between onImplodeStart and onImplodeFinish
	"onImplodeUpdate": [
		// make the unit wiggle around, destroy random pixels, etc
	],

	// called once, after implodeTime has elapsed, and right before the unit is destroyed
	"onImplodeFinish": [
		// play sounds, spawn explosion effects, destroy nearby bullets, etc
	],
}
```

!!! tip
	You can manually call the **Implode** action on a unit to destroy it at any time, without it needing to take lethal damage to the core.

	```json
	{ "action": "CallMethod", "target":"unit", "method": "Implode", },
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

!!! warning
	When specifying the starting value of custom properties, you **can't** use a scriptfunc.
	
	For instance:
	```json
	"revengeCounter": { "type": "Int", "value":"rand.Int(0, 99)"},
	```
	Is **not** allowed, but using a simple value of `6` is:
	```json
	"revengeCounter": { "type": "Int", "value":6},
	```
	

## Texture

Unit forms have a `texture` property, which itself has a single `shader` property.

It draws a scrolling wavy texture on the pixels.

```json
{
	"baseForm":{
		"texture": {
            "shader": {
				// the texture to draw (path relative to your campaign folder)
				"texturePath":"pxc_textures/blurredClouds",

				// how strong the effect is
				"intensity": "rand.Float(0.9, 1.1)",

				// i can't remember what all this stuff does, you just gotta play with it
                "speedX": "rand.Float(0.8, 1.2)",
                "speedY": "rand.Float(0.15, 0.25)",
                "timeFactor": "rand.Float(0.08, 0.12)",
                "timeFactor2": "rand.Float(0.45, 0.55)",    
                "timeFactor3": "rand.Float(0.65, 0.75)",
                "freqX": "rand.Float(9, 11)",
                "freqY": "rand.Float(7, 9)",
                "depthX": "rand.Float(0.075, 0.125)",
                "depthY": "rand.Float(0.125, 0.175)",
            }
        },
	},
}
```

<i>The unit on the left has no shader, while the unit on the right has a subtle cloudy coloring.</i>
<img src="https://files.facepunch.com/ryleigh/1b1111b1/shader.png" />

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

!!! tip
	In order to print the value of a property or function in text (instead of just displaying the name), format the string with `${    }` surrounding whatever should be evaluated.
	```json
	"text": "I'm thinking of a number!! It's ${rand.Int(1, 100)}!!!", 
	```

	<img src="https://files.facepunch.com/ryleigh/1b1011b1/Unity_2019-09-10_02-16-20.png" />

!!! example "Fonts"
	[Here is an image](https://files.facepunch.com/ryleigh/1b1511b1/fonts-for-floating-text.png) showing the different fonts available.

### String Files

Instead of including speech lines directly in the unit configs, you can list them in a separate string file. This allows for more variety and opens up the possibility of localizing into other languages.

Here is `text.json`, the strings file for the **example** custom campaign:
```json
{
    "en": { // english
        "example": {
            "title": "Example Stage",
            "description": "This is an example stage",

            "boss":{
                "welcome": [
					"Let's fight", 
					{ "value": "I'm just an example boss!", "weight": 0.8 }, 
					{ "value": "I will kill you", "weight": 0.3 },
                ],

                "death": [
					{ "value": "You killed me!", "weight": 1.5 }, 
					{ "value": "Aghhhh....", "weight": 0.66 },
                ],
            },
        },
    }
}
```

Your `plugin.json` file needs to list this file under the `strings` property, and it's possible to include more than one.

```json hl_lines="6"
{
	"title": "Example Plugin",
    "description": "Custom campaign example",

	// ...
	"strings": [ "text" ],
}
``` 

Now we can use those strings in any of our scripts. 

The text `#example.boss.welcome` will be replaced with a random selection defined for that string, with <font color=#888888>*Let's fight*</font> having the greatest chance with a default weight of `1.0`, <font color=#aaaaaa>*I'm just an example boss!*</font> happening slightly less often, and <font color=#dddddd>*I will kill you*</font> being even more rare.




## Script Parameters

These parameters can be used inside any scriptfunc by a Unit.

!!! info
    [Script Params](../../SpaceUsurper/UnitData/#script-parameters)

## Debugging

`debugVector`: draws a 2d vector from the unit's position <br>
`debugText`: displays a string below the unit's position (use `${NAME}` for properties)