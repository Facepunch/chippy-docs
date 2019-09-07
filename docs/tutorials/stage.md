# Stages

!!! info
	[Properties & Methods](../../SpaceUsurper/GameStage)

	[Full json config](../../SpaceUsurper/StageData)

## Config

The Stage config file handles spawning units and the player, setting the bounds of the arena, and various other things.

### Basic Settings

```json
{
    "menuCore": "misc/core/octopus/core0", // the layered sprite eye to show on menu
    "title": "#octopus.title",
    "description": "#octopus.description",
    "behaviour": ".fsm", // the behaviour state machine
    "song": "019", // the song config file to use

	"arena": {
		// arena position and size
        "bounds": "rectCenter(vec2(0f, 0f), vec2(200f, 200f))",
    },
}
```

### Game Mode

#### Time Attack

This is the default mode. The goal is to destroy the boss(es) as quickly as possible.

```json
{
	// ...
	"gameMode": "TimeAttack",
}
```

#### Endless

In `Endless` mode, the goal is to survive as long as possible.

```json
{
	// ...
	"gameMode": "Endless",
}
```

!!! note
	When time is slowed down or sped up in `Endless` mode, the game timer is affected too!

### Medal Times

Choose the **time in seconds** that needs to be beat to earn each medal.

```json
{
	// ...
	"medals": {
        "bronze": 420,
        "silver": 300,
        "gold": 180,
    },
}
```

An `Endless` stage needs to specify the `victory` time as well - that is, the time you need to last to **beat the stage** without even earning a bronze medal.

```json
{
	// ...
	"medals": {
		"victory": 250,
        "bronze": 350,
        "silver": 500,
        "gold": 650,
    },
}
```

### Player

```json
{
	"player": {
		// the path to the player config file
        "path":"player/defaultPlayer",

		// spawn the player here at the start of level
        "spawnPos": "vec2(0f, -20f)",
    },
}
```

The `player.path` property is used when overriding the default player ship - you can safely omit it otherwise.

### Units

Units are preloaded to avoid stuttering during gameplay, and therefore the type and max count of each unit needs to be decided on in advance.

```json
{
	// ...
	"units": {
        "boss": { "config": "mech/unit/boss", "requiredForVictory": true },
        "turret": { "config": "mech/unit/turret", "count":5, },
        "egg": { "config": "misc/unit/eggShield", "count":1, },
        "trap": { "config": "mech/unit/trapLaser", "count":1, },
    },
}
```

To beat the level on `Time Attack` stages, the player needs to destroy all `requiredForVictory` units.

#### Cross-Unit Requirements

Unit parts can be protected from parts of other units.

```json
{
	// ...
	"units": {
        "boss": { "config": "octopus/unit/boss", "requiredForVictory": true, "requirements": { "form2:core": [{ "unit": "turret", "form": 0, "parts": [ "core" ] }] }},
        "turret": { "config": "octopus/unit/turret", "count": "turretCount", "progressWeight": 0.25 },
        "egg": { "config": "misc/unit/eggShield", "count":1, },
    },
}
```

Expanded for clarity:
```json
"boss": {
	// ...
	"requirements": { 
		// the 3rd form core of the boss requires the turret unit's 1st form core
		"form2:core": [
			{ 
				"unit": "turret", 
				"form": 0, 
				"parts": [ "core" ],
			},
		], 
	},
},
```

#### Spawning

```json
{ "action": "CallMethod", "method": "SpawnUnit", "params": { "name": "boss", "pos": "vec2(0f, 10f)", }},
```

There are a couple optional parameters:

```json
{ "action": "CallMethod", "method": "SpawnUnit", 
	"params": { 
		"name": "boss", // the name refers to what you chose in the "units" json property
		"pos": "vec2(0f, 10f)", 
		"force": "vec2(0f, -50f)", // force applied to unit upon spawn
		"facingDir": "UpLeft", // initial direction of unit
	}
},
```

If you try to spawn a unit with too many active already, it will be ignored. The `count` of a unit determines the max amount that can be active.

### Arena

You'll probably want to choose your level size by setting `bounds`, but the other `arena` properties can be ignored if you're fine with the defaults for now.

```json
{
	"arena": {
		// a rect specifying the size and position of the level
	    "bounds": "rectCenter(vec2(0f, 0f), vec2(220f, 200f))",

	    // level background color
	    "bgColor":"color(0.06f, 0.06f, 0.08f)",

	    // what color hides the out-of-bounds areas? (setting opacity <1 is useful for debugging bullet behaviour)
	    "letterboxColor":"color(0f, 0.025f, 0f, 1f)",

	    // color of background grid
	    "gridColor":"color(1f, 1f, 1f, 0.015f)",

	    // how thick are the lines on the grid
	    "gridThickness":2.2,

	    // what dimensions are the grid diamonds
        "gridSpacing":"vec2(20f, 20f)",

        // how large are the edges of the grid
        "gridEdgeWidth":12,

        // how much to warp grid in the edges
        "gridEdgeWarp":1.25,

        // scale the grid lines in the edges
        "gridEdgeScale":3.5,
	},
}
```

<img src="https://s3-eu-west-1.amazonaws.com/files.facepunch.com/ryleigh/1b1611b1/Chippy_2019-08-16_17-38-15.png" width="100%"/>

## Behaviour

The stage has its own state machine like units do, where actions can be called in sequence.

```json
{
	"behaviour": ".fsm",

	// ...

	"fsm":{
		"inactive": [
			
		],
		"start":[
			// spawn clouds, boss, etc

			// without an indefinite Wait, the state machine will keep looping
			{ "action": "Wait", },
		],
	},

}
```

!!! warning
	While most names can be safely changed in Chippy scripts, the `start` state in a stage fsm will specifically be set at the beginning of a run, so make sure it exists.

## Handlers

You can call Actions are certain points during a stage, besides the state machine.

```json
{
    "onUpdate":[
        // called each frame
        { "action": "CallMethod", "target":"player", "method": "AddForce", "params": { "force": "vec2(0f, 1f)", }},
    ],    

    "onPlayerHit":[ /* called when player is hit but does not die */ ],
	"onPlayerDie":[ /* called when player takes lethal damage */ ],
},
```

## Custom Variables

Custom variables can be defined in the `properties` structure of the stage config.

```json
{
	"properties": {
	    "numBubblesPopped": { "type": "Int" },
		"egg": { "type": "Unit" },

		// player specific
		"attempts": { "type": "Int", "userData": true, "value": "progression.GetAttempts(stageId)" },
		"victories": { "type": "Int", "userData": true, "value": "progression.GetVictories(stageId)" },
	},
}
```

These values can be used in any script func by the stage **or any object** (unit, player, bullets, etc) that exists on the stage.

To modify them, use the SetValue method:

```json
{ "action": "SetValue", "target":"stage", "name": "numBubblesPopped", "type": "Int", "value": "numBubblesPopped + 1" },
```

When using the `target` param so you can set the property of a different object (for example, a bullet setting the value of a stage property) you must also declare the **type** of the value.

### Player Specific Properties

The **player specific** properties check the player's individual progression file for their `attempts` (number of times playing the level) and `victories` (number of times beating the level).

Typically these are only used to adjust which speech lines the bosses say, but there's no rule that they can't have gameplay implications.

### Return Values

Some methods have a **return** value that you may want to save to a custom variable to access later.

```json hl_lines="15"
{
	"properties": {
		// when the level starts, the value of the bossUnit property is null
		"bossUnit": { "type": "Unit" },
	},

	"fsm": {
		"inactive": [
            { "action": "Wait" },
        ],
        "start": [
			// spawn the boss unit and save the return value (of type Unit) to the custom bossUnit property
			{ "action": "CallMethod", "method": "SpawnUnit", 
			 	"params": { "name": "boss", "pos": "vec2(0f, 20f)" }, 
				"return":"bossUnit", 
			},

			// now we can call actions directly on the bossUnit
			{ "action": "CallMethod", "target":"bossUnit", "method": "Shake", "params": { "strength":5, "time":2, "easingType":"QuadIn", }},
		],
	},
}
```

## Screen Effects

Some visual effects can be applied to the screen.

```json
"onUpdate":[
	{ "action": "CallMethod", "method": "SetHueShift", "params": { "amount": "mapReturn(stageTime, 0f, 9f, 0f, 100f, 'QuadInOut')", }},
	{ "action": "CallMethod", "method": "SetContrast", "params": { "amount": "mapReturn(stageTime, 0f, 2f, 0f, -60f, 'QuadInOut')", }},
	{ "action": "CallMethod", "method": "SetSaturation", "params": { "amount": "mapReturn(stageTime, 0f, 8f, 0f, 200f, 'QuadInOut')", }},
	{ "action": "CallMethod", "method": "SetColorFilter", "params": { "color": "lerp(color(1f, 1f, 1f), color(1f, 1f, 0f) * 2f, mapReturn(stageTime, 0f, 4f, 0f, 1f, 'QuadInOut'))", }},
	{ "action": "CallMethod", "method": "SetTemperature", "params": { "amount": "mapReturn(stageTime, 0f, 5f, 0f, -100f, 'Linear')", }},
	{ "action": "CallMethod", "method": "SetChromaticAberration", "params": { "amount": "mapReturn(stageTime, 0f, 10f, 0f, 4f, 'ExpoInOut')", }},
],
```

<video controls width="100%"> <source src="https://files.facepunch.com/ryleigh/1b2611b1/2019-08-26_00-18-50.mp4" type="video/mp4" > </video>

## Script Parameters

These parameters can be used inside any scriptfunc by the stage or any object in it (player, units, patterns, bullets, etc).

!!! info
    [Script Params](../../SpaceUsurper/StageData/#script-parameters)

## Debugging

Any entity can call the Stage debug methods to draw lines or text.

```json
"onUpdate": [
	{ "action": "CallMethod", "target":"stage", "method": "DrawDebugLine", 
		"params": { 
			"a":"playerPos", 
			"b":"playerPos + playerVel", 
			"time":0.02, 
			"color":"color(0f, 0f, 1f) * 2f", 
			"width":0.2, 
			"opacity":0.6, 
		}
	},

	{ "action": "CallMethod", "target":"stage", "method": "DrawDebugText", 
		"params": {
			"pos": "playerPos + vec2(0f, 3f)",
			"text": "${playerVel}",
			"fontSize":"2.5f + fastSin(stageTime * 4f) * 0.5f",
			"time": 0.02,
			"color":{"r":1,"g":1,"b":0,"a":0.25},
		}
	},
],

```

<video controls width="100%"> <source src="https://files.facepunch.com/ryleigh/1b2411b1/2019-08-24_22-55-58.mp4" type="video/mp4" > </video>

### Camera Zoom

Hold ++v++ to temporarily zoom out, or use ++plus++ and ++minus++ for finer control.