# Actions

**Actions** are special whitelisted C# methods that can be run from json. 

They can do useful things such as spawning objects, triggering visual effects, changing the size of the arena, and more.

They can be run from stages, units, bullets, patterns, status effects, and even guns.

## Stage Methods

- TimeScale
- Shake Camera

## Player Methods

- Vibrate

## State Machine Control

These actions can be used to change the flow through a behaviour state machine.

### Wait

Wait for an amount of time before continuing the state machine.

```json
"state 0": [
	{ "action": "Wait", "time":0.5, },	
],

```

To wait indefinitely, don't provide a value for `time`.

```json
"state_0": [
	{ "action": "Wait", },	
],
```

!!! warning
	Only use `Wait` actions in behaviour state machines, not in callbacks like `onHitPixel`, `onPlayerHit`, etc.

### Condition

Use `Condition` actions like if-else statements, to run certain actions based on the result of a condition function.

```json
"state_1":[
	{ "action": "Condition", "condition": "playerPos.y > 0f",
	    "true": [
	    	{ "action": "CallMethod", "target": "player", "method": "Vibrate", "params": { "strength": 1.5, "time": 0.25, }},
	        { "action": "Goto", "state": "state_2" },
	    ],
		"false":[
			{ "action": "Goto", "state": "state_3" },
		]},
],
```

You can omit the `false` branch if it's not needed.

```json
"5b":[
	{ "action": "Condition", "condition": "player.GetStatusLevel('status/passive/shield') > 0",
	    "true": [
	        { "action": "CallMethod", "target": "stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/bubbleGrid.1", }},
	        { "action": "CallMethod", "target":"player", "method": "Vibrate", "params": { "strength":0.1, "time":1, }},
	        { "action": "CallMethod", "target":"stage", "method": "ShakeCamera", "params": { "strength":0.25, "time":0.1, }},
	    ],},
],
```

### Repeat

Use the `Repeat` action to loop actions multiple times.

The `count` parameter controls the number of times to loop the actions.<br>
The `delay` parameter is the time to wait after each loop.<br>
The `inner` parameter is the list of actions to loop.<br>

```json
"state_6":[
	{ "action": "Repeat", "count": "6 + min(loopNum, 4)", "delay": "map(loopNum, 0, 6, 1.5f, 1.25f, 'QuadIn')", "inner": [
	    { "action": "CallMethod", "method": "ChargePattern", "params": { "path": "claw/pattern/orbiter.1", "partType": "core", "chargeTime":1, "dir":"(playerPos + playerVel * 2f) - partPos", }},
	]},

	// or, spread out for clarity:
	{ "action": "Repeat", 
		"count": "6 + min(loopNum, 4)", 
		"delay": "map(loopNum, 0, 6, 1.5f, 1.25f, 'QuadIn')", 
		"inner": [
	    	{ "action": "CallMethod", "method": "ChargePattern", "params": { 
	    		"path": "claw/pattern/orbiter.1", 
	    		"partType": "core", "chargeTime":1, 
	    		"dir":"(playerPos + playerVel * 2f) - partPos", 
	    	}},
		]},
],
```

### Switch

Use a `Switch` action when your branching logic has too many conditions.

The `value` parameter should be an Int variable.

```json
{
	"properties": {
		"attack_num": { "type": "Int", "value":1 },
	},

	// ...

	"fsm": {
		"form0": {
			"choose_next_attack":[
				{ "action": "Switch", "value": "attack_num", "cases": {
				    "0": [{ "action": "Log", "message": "Shoot small attack!", },],
				    "1": [{ "action": "Log", "message": "Shoot medium attack!!", },],
				    "2": [
				    	{ "action": "Log", "message": "Shoot big attack!!!", },
				    	{ "action": "CallMethod", "target":"stage", "method": "PlaySfx", "params": { "sfxType":"BombExplode", "pos":"unitPos", }},                
				    ],
				}},
			],
		}
	},
}
```
### Goto

### Yield

## SetValue

## Subroutines

- Log
