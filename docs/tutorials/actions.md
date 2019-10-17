# Actions

**Actions** trigger game functionality from json scripts.

They can do useful things such as spawning objects, triggering visual effects, changing the size of the arena, and more.

They can be run from stages, units, bullets, patterns, status effects, and even guns.

## State Machine Control

These actions are used to handle logic and flow through a behaviour state machine.

### Wait

Wait for an amount of time before continuing.

```json
"state 0": [
	{ "action": "Wait", "time":0.5, },	
],
```

!!! tip
	To wait indefinitely, don't provide a value for `time`.

	```json
	"state_0": [
		{ "action": "Wait", },	
	],
	```

!!! warning
	For best practices, only use `Wait` actions in behaviour state machines, not in handlers like `onHitPixel`, `onPlayerHit`, etc.

### Condition

Use `Condition` actions like if-else statements. Based on whether the `condition` is `true` or `false`, call certain other actions.

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

!!! tip
	You can omit the `false` branch if it's not needed (or even omit the `true` branch).

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

!!! tip
		Conditions can be nested as much as you want.

		```json
		"state 0": [
			{ "action": "Condition", "condition": "rand.Float(0f, 1f) < 0.25f",
				"true": [
					{ "action": "Condition", "condition": "playerPos.y < 0f",
						"true": [{ "action": "Goto", "state": "state 1" },],
						"false":[{ "action": "Goto", "state": "state 2" },]},
				],
				"false":[
					{ "action": "Condition", "condition": "playerPos.x < 0f",
						"false": [{ "action": "Goto", "state": "state 3" },],},
				]},
		],
		```

### Switch

Use a `Switch` action when your branching logic has too many conditions.

The `value` parameter should be an integer variable.

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
],
```

Expanded for clarity:
```json
"state_6":[
	{ "action": "Repeat", 
		"count": "6 + min(loopNum, 4)", 
		"delay": "map(loopNum, 0, 6, 1.5f, 1.25f, 'QuadIn')", 
		"inner": [
	    	{ "action": "CallMethod", "method": "ChargePattern", 
				"params": { 
					"path": "claw/pattern/orbiter.1", 
					"partType": "core", 
					"chargeTime":1, 
					"dir":"(playerPos + playerVel * 2f) - partPos", 
	    		}
			},
		]},
],
```

### Goto

The `Goto` action lets you change states.

In the following example, normally the state would loop from "1" back to the beginning state "initial delay". Instead it's told to go back to state "0".

```json hl_lines="10"
"fsm": {
	"form0": {
		"initial delay":[
			// do this only one time
		],
		"0":[
			// do this every time
		],
		"1":[
			{ "action": "Goto", "state":"0" },
		],
	}
},
```

!!! tip
	You can also be more specific and pass in a state of "form0.0" (or even "form1.0", if that exists).

## SetValue

Set the value of a custom variable.

```json hl_lines="4 15"
{
	"properties":[
		// ...
		"lastTauntTime": { "type": "Float", "value":-60, },
	],

	// when the player takes damage, boss should consider taunting them if it's been long enough since last taunt
	"baseForm": [
		"onHitPlayer":[
            { "action": "Condition", "condition": "(stageTime - lastTauntTime) > 5f",
                "true": [
                    // display a speech bubble taunt here

					// set value of lastTauntTime to current time
                    { "action": "SetValue", "name": "lastTauntTime", "value": "stageTime" },
                ],},
        ],
	],
}
```

When setting the value of **another object's** property, you must specify the `target` object and the `type` of the property.

```json
{ "action": "SetValue", "target":"stage", "name": "cloudFlashGlowPercent", "type": "Float", "value": "clamp01(cloudFlashGlowPercent + 0.75f)" },
```

Expanded for clarity:
```json hl_lines="4 6"
[
	{ 
		"action": "SetValue", 
		"target":"stage", 
		"name": "cloudFlashGlowPercent", 
		"type": "Float", 
		"value": "clamp01(cloudFlashGlowPercent + 0.75f)" 
	},
],
```

## CallMethod

The `CallMethod` action is used to run whitelisted C# methods.

Specifying the `target` is only necessary if you are calling a method on a different json object.

```json
{ "action": "CallMethod", "target":"stage", "method": "AddTimeScale", "params": { "scale": 0.33, "time": 0.25, "easingType": "CubicIn" }},
```

<br>
Here are **some** of the most useful methods:

??? example "[Stage](../../SpaceUsurper/Stage) Methods"
	[AddTimeScale](../../SpaceUsurper/Stage/AddTimeScale)<br>
	[LerpBounds](../../SpaceUsurper/GameStage/LerpBounds)<br>
	[ShakeCamera](../../SpaceUsurper/Stage/ShakeCamera)<br>
	[SpawnPattern](../../SpaceUsurper/Stage/SpawnPattern)<br>
	[AffectBulletsInRadius](../../SpaceUsurper/Stage/AffectBulletsInRadius)<br>
	[AffectTouchingBullets](../../SpaceUsurper/Stage/AffectTouchingBullets)<br>
	[AffectUnitsInRadius](../../SpaceUsurper/Stage/AffectUnitsInRadius)<br>
	[AffectTouchingUnits](../../SpaceUsurper/Stage/AffectTouchingUnits)<br>
	[AddPattern](../../SpaceUsurper/Stage/AddPattern)<br>
	[DespawnAddedPatterns](../../SpaceUsurper/Stage/DespawnAddedPatterns)<br>

??? example "[Player](../../SpaceUsurper/Player) Methods"
	[AddForce](../../SpaceUsurper/Player/AddForce)<br>
	[AddPhysicsForce](../../SpaceUsurper/Player/AddPhysicsForce)<br>
	[Vibrate](../../SpaceUsurper/Player/Vibrate)<br>
	[ReplaceMainGun](../../SpaceUsurper/Player/ReplaceMainGun)<br>
	[RestoreDefaultMainGun](../../SpaceUsurper/Player/RestoreDefaultMainGun)<br>
	[AddStatus](../../SpaceUsurper/Player/AddStatus)<br>
	[GetStatusLevel](../../SpaceUsurper/Player/GetStatusLevel)<br>

??? example "[Pattern](../../SpaceUsurper/BulletPattern) Methods"
	[AddBullet](../../SpaceUsurper/BulletPattern/AddBullet)<br>
	[AffectBullets](../../SpaceUsurper/BulletPattern/AffectBullets)<br>

??? example "[Bullet](../../SpaceUsurper/Bullet) Methods"
	[AddPattern](../../SpaceUsurper/Bullet/AddPattern)<br>
	[Flash](../../SpaceUsurper/Bullet/Flash)<br>
	[Redirect](../../SpaceUsurper/Bullet/Redirect)<br>
	[Reflect](../../SpaceUsurper/Bullet/Reflect)<br>
	[AffectTouchingBullets](../../SpaceUsurper/Bullet/AffectTouchingBullets)<br>
	[AffectTouchingUnits](../../SpaceUsurper/Bullet/AffectTouchingUnits)<br>
	[SetFloatVar](../../SpaceUsurper/Bullet/SetFloatVar)<br>
	[SetVectorVar](../../SpaceUsurper/Bullet/SetVectorVar)<br>
	[SetIntVar](../../SpaceUsurper/Bullet/SetIntVar)<br>
	[Transform](../../SpaceUsurper/Bullet/Transform)<br>

??? example "[Unit](../../SpaceUsurper/Unit) Methods"
	[AddForce](../../SpaceUsurper/Unit/AddForce)<br>
	[Respawn](../../SpaceUsurper/Unit/Respawn)<br>
	[Flash](../../SpaceUsurper/Unit/Flash)<br>
	[DoesPartExist](../../SpaceUsurper/Unit/DoesPartExist)<br>
	[Shake](../../SpaceUsurper/Unit/Shake)<br>
	[SetHidden](../../SpaceUsurper/Unit/SetHidden)<br>
	[AimTowards](../../SpaceUsurper/Unit/AimTowards)<br>

??? example "[Unit Part](../../SpaceUsurper/PixelGroup) Methods"
	[ChargePattern](../../SpaceUsurper/PixelGroup/ChargePattern)<br>
	[AddPattern](../../SpaceUsurper/PixelGroup/AddPattern)<br>
	[Flash](../../SpaceUsurper/PixelGroup/Flash)<br>
	[Look](../../SpaceUsurper/PixelGroup/Look)<br>
	[SpawnBubble](../../SpaceUsurper/PixelGroup/SpawnBubble)<br>
	[StopChargingPatterns](../../SpaceUsurper/PixelGroup/StopChargingPatterns)<br>
	[StopPatterns](../../SpaceUsurper/PixelGroup/StopPatterns)<br>
	[SetCore](../../SpaceUsurper/PixelGroup/SetCore)<br>

??? example "[Pixel](../../SpaceUsurper/PixelData) Methods"
	[SplashDamage](../../SpaceUsurper/PixelData/SplashDamage)<br>
	[TransformPixelLine](../../SpaceUsurper/PixelData/TransformPixelLine)<br>
	[TransformPixelCircle](../../SpaceUsurper/PixelData/TransformPixelCircle)<br>
	[Spark](../../SpaceUsurper/PixelData/Spark)<br>
	[ApplyDamage](../../SpaceUsurper/PixelData/ApplyDamage)<br>

??? example "[Status Effect](../../SpaceUsurper/StatusEffect) Methods"
	[AddBullet](../../SpaceUsurper/StatusEffect/AddBullet)<br>
	[DespawnAddedBullets](../../SpaceUsurper/StatusEffect/DespawnAddedBullets)<br>
	[AddGun](../../SpaceUsurper/StatusEffect/AddGun)<br>
	[DespawnGuns](../../SpaceUsurper/StatusEffect/DespawnGuns)<br>
	[SetCharge](../../SpaceUsurper/StatusEffect/SetCharge)<br>
	[Execute](../../SpaceUsurper/StatusEffect/Execute)<br>
	[LevelUp](../../SpaceUsurper/StatusEffect/LevelUp)<br>
	[LevelDown](../../SpaceUsurper/StatusEffect/LevelDown)<br>
	[Disable](../../SpaceUsurper/StatusEffect/Disable)<br>

## Return Values

.....
	
## Subroutines

Subroutines allow you to create your own functions (essentially, a sequence of actions).

The following example calls the `speech.sub` subroutine when the player gets hit.

```json
{
	"onHitPlayer":[
		{ "action": "Condition", "condition": "(stageTime - lastTauntTime) > 5f",
			"true": [
				{ "action": "CallSubroutine", "target":"unit", "path": ".speech.sub", "params": { "message": "#octopus.boss.player_hit_pixel", "chance":"map(stageTime - lastTauntTime, 0f, 60f, 0f, 0.45f, 'QuadIn') * map(stageTime - lastSpeechTime, 0f, 4f, 0f, 1f, 'ExpoIn')", }},
				{ "action": "SetValue", "name": "lastTauntTime", "value": "stageTime" },
			],},
	],

	"speech.sub": {
        "parameters": {
            "this": { "type": "Unit" },
            "message": { "type": "String" },
            "chance": { "type": "Float" },
        },

        "actions": [
            { "action": "Condition", "condition": "rand.Float(0f, 1f) < chance * map(stageTime - lastSpeechTime, 0f, 4f, 0f, 1f, 'ExpoIn') && !isImploding",
                "true": [ 
                    { "action": "CallMethod", "target":"unit.GetPart('core')", "method": "SpawnBubble", "ignoreNullRef": true, "params": { "text": "${message}", "partType":"core", "lifetime": 4,
                        "fillColor": "color(0.2f, 0.1f, fastSin(stageTime * PI * 2f) * 0.2f + 0.5f, 0.8f)", 
                        "borderColor": "color(0.75f, 0.75f, fastSin((stageTime + 0.5f) * PI * 2f) * 0.05f + 0.95f, 0.66f)", 
                        "borderWidth": "fastSin(stageTime * PI * 3f) * 2f + 4f",
                        "textColor":"lerp(color(1f, 1f, 1f), color(0.75f, 0.75f, 1f), 0.5f + fastSin(stageTime * PI * 12f) * 0.5f)",
                        "fontSize":33,
                    }},
                    { "action": "CallMethod", "target":"stage", "method": "PlaySfx", "params": { "sfxType": "OctopusBossSpeech", "pos":"unitPos", }},
                    { "action": "SetValue", "name": "lastSpeechTime", "value": "stageTime" },
                ],},
        ]
    },
},
```

When calling the subroutine, you should specify the `target`, even if you're calling the subroutine from an object on itself.

```json hl_lines="3"
{ 	
	"action": "CallSubroutine", 
	"target":"unit", 
	"path": ".speech.sub", 
	"params": { 
		"message": "#octopus.boss.player_hit_pixel", 
		"chance":"map(stageTime - lastTauntTime, 0f, 60f, 0f, 0.45f, 'QuadIn') * map(stageTime - lastSpeechTime, 0f, 4f, 0f, 1f, 'ExpoIn')", 
	},
},
```

The subroutine definition should include a `this` parameter, set to the type of object the subroutine will be run on.

```json hl_lines="4"
{
	"tauntSpeech.sub": {
        "parameters": {
            "this": { "type": "Unit" },
        },

        "actions": [
            { "action": "Condition", "condition": "(stageTime - lastTauntTime) > 10f && rand.Float(0f, 1f) < map(stageTime - lastTauntTime, 0f, 60f, 0f, 0.35f, 'QuadIn') * map(stageTime - lastSpeechTime, 0f, 4f, 0f, 1f, 'ExpoIn')",
                "true": [
                    { "action": "Condition", "condition": "player.GetStatusLevel('status/passive/shield') < 1",
                        "true": [{ "action": "CallSubroutine", "target":"unit", "path": ".speech.sub", "params": { "message": "#octopus.boss.player_hit_bullet_no_shield", "chance":1, }},],
                        "false":[{ "action": "CallSubroutine", "target":"unit", "path": ".speech.sub", "params": { "message": "#octopus.boss.player_hit_bullet", "chance":1, }},  ]},

                    { "action": "SetValue", "name": "lastTauntTime", "value": "stageTime" },
                ],},
        ]
    },
}
```

!!! tip
	The name of subroutines don't **need** to include `.sub`, we just do it for clarity.