# Bullet Patterns

A bullet pattern is made up of **volleys**, each shooting a number of **bullets** from a certain position and angle.

## Data

## A Simple Pattern

```json
"simpleAttack": {
  "numVolleys": 15,
  "numBulletsInVolley":5,
  "shootDelay": 0.1,
  "rotationSpeed":-150,
  "sfxVolley": "OctopusSmallSpewShoot",
  "bullets": [".bullet"],
},
```

<video controls> <source src="https://files.facepunch.com/ryleigh/1b0711b1/2019-08-07_16-12-22.mp4" type="video/mp4"> </video>

This pattern shoots `15` times, with `5` bullets each.
By default, the bullets in each volley are spread evenly around a full 360° circle.

After the initial volley, there's a `0.1` second delay until the next.

The pattern rotates clockwise with a speed of `150` units (basically equivalent to 150° per second). Negative is clockwise, positive is counterclockwise.

`bullets` defines what this pattern shoots - since only one type is referenced, every bullet in the pattern will be the same. The path can be absolute, but usually it's easiest to reference definitions in the same json object - in this case, `.bullet` refers to the bullet defined at the same level as the `simpleAttack` pattern definition.

## More About Patterns

### Script Functions

Most of the properties in the pattern can be expressed as a string function that is continuously updated, instead of a static value. For example, we could increase the number of bullets in each subsequent volley by changing the `numBulletsInVolley` property:
```json
"numBulletsInVolley":"5 + volleyNum",
```
The `volleyNum` parameter is a value that all patterns can use in functions. The first volley will have 5 bullets, the second 6 bullets, and so on.

Instead of an unchanging rotation speed, we could make it oscillate between -150 and 150:

```json
"rotationSpeed":"sin(patternTime * 5f) * 150f",
```
`patternTime` simply tracks how long this pattern has been running for. 

!!! tip
	The 'f's after the numbers denote them as floating-point numbers instead of integers, since `rotationSpeed` is itself a float, but don't worry about it too much.

### Aiming

By default, patterns simply rotate according to their `rotationSpeed` property, but we can instead set a target angle:
```json hl_lines="7 8 9 10"
"simpleAttack": {
    "numVolleys": 15,
    "numBulletsInVolley":5,
    "shootDelay": 0.1,
    "bullets": [".bullet"],
    "sfxVolley": "ShootSoftWomp",
    "aimMode":"Target",
    "targetAimAngle":"vecToAngle(playerPos - patternPos)",
    "aimSpeed":0.1,
    "arcAngle":90,
  },
```
Setting `"aimMode":"Target"` means the pattern will ignore `rotationSpeed` and ease toward `targetAimAngle` instead. In this case the pattern wants to aim directly at the player's position. 

The `aimSpeed` is a value from 0-1. With a value of `0.1` it will ease 10% of the way to the target each frame, so it will lag behind a bit.

<video controls> <source src="https://files.facepunch.com/ryleigh/1b0711b1/2019-08-07_16-09-42.mp4" type="video/mp4"> </video>

With `"arcAngle":90` we changed the angle that all the bullets are distributed between from 360° to 90°.

<img src="https://files.facepunch.com/ryleigh/1b0611b1/Photo_2019-08-06_8_14_23_PM.jpg" width="300"/>

??? info "The entire json file for our example pattern, located at `octopus/pattern/simplePattern.json`"
	When the pattern refers to the bullet, it can simply use `.bullet` since it's in the same json object (the braces that enclose the whole file), though `octopus/pattern/simplePattern.bullet` would work as well. Any name can be used instead of "bullet".
	```json
	{
	  "simpleAttack": {
	    "numVolleys": 15,
	    "numBulletsInVolley":5,
	    "shootDelay": 0.1,
	    "bullets": [".bullet"],
	    "sfxVolley": "ShootSoftWomp",
	    "aimMode":"Target",
	    "targetAimAngle":"vecToAngle(playerPos - patternPos)",
	    "aimSpeed":0.1,
	    "arcAngle":90,
	  },

	  "bullet": {
	    "keyframes": [
	    {
	      "duration":0.5,
	      "acceleration":5,
	      "frictionPercent":0.25,
	      "radius":2,
	      "sprite":"sprites/circle/simple",
	      "colorA1":{ "value": {"r":1,"g":0,"b":0,"a":0.9}},
	      "colorA2":{ "value": {"r":1,"g":0.1,"b":0,"a":0.7}},
	      "colorB1":{ "value": {"r":0.8,"g":0,"b":0,"a":0.8}},
	      "colorB2":{ "value": {"r":0.6,"g":0,"b":0,"a":0.6}},
	      "colorC1":{ "value": {"r":1,"g":0.1,"b":0,"a":0.2}},
	      "colorC2":{ "value": {"r":0.8,"g":0.2,"b":0,"a":0.1}},
	      "glowA": 4,
	      "glowB": 0.5,
	      "glowC": 0,
	      "colorBlinkTime":0.15,
	      "opacity":0,
	      "easingType":"QuadOut",
	    },
	    {
	      "duration":1.5,
	      "acceleration":15,
	      "frictionPercent":0.05,
	      "glowA": 3.5,
	      "opacity":1,
	      "acceleration":66,
	    },
	    ],
	    "startSpeed":120,
	    "lifetime":30,
	    "depthLevel": "Bullet",
	    "shapeType": "Circle",
	    "despawnTime":0.15,
	  },
	}
	```

## Spawning a Pattern

Once you've created a bullet pattern definition, you'll need to spawn it in-game using an [Action](actions.md).

```json
{ "action": "CallMethod", "target":"stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/simplePattern.simpleAttack", "pos":"playerPos + vec2(0f, 10f)", "dir":"vec2(0f, 1f)", }},
```

Let's expand that line to make it more clear:

```json
{ "action": "CallMethod", // type of action
	"target":"stage", // call method on the stage object
	"method": "SpawnPattern", // name of the method to call
	"params": { // parameters to pass into this method
		"path": "octopus/pattern/simplePattern.simpleAttack", // the location of the pattern definition, inside our custom campaign folder
		"pos":"playerPos + vec2(0f, 10f)", // the position to spawn the pattern at (in this case, 10 units above the player, with 1 unit equaling the size of 1 boss pixel)
		"dir":"vec2(0f, 1f)", // the direction the pattern should begin facing (in this case, straight upward)
	}
},
```

??? abstract "Common methods for spawning patterns"
	These are the most common use-cases for making bullet patterns appear. There are more optional parameters than shown here, however.

	??? abstract "Spawning anywhere"
		This method, the same as seen above, can be called from anywhere actions are valid: from a unit, the player, the stage itself, etc.
		```json
		{ "action": "CallMethod", "target":"stage", "method": "SpawnPattern", "params": { "path": "octopus/pattern/simplePattern.simpleAttack", "pos":"playerPos + vec2(0f, 10f)", "dir":"vec2(0f, 1f)", }},
		```
	??? abstract "Charging from a unit part"
		This example doesn't specify the `target`, as it's not necessary when called from a unit itself.
		```json
		{ "action": "CallMethod", "method": "ChargePattern", "params": { "path": "octopus/pattern/simplePattern.simpleAttack", "partType": "core", "chargeTime":1, "dir":"(playerPos + playerVel * 1f) - partPos", }},
		```
		```json
		{ "action": "CallMethod",
			"method": "ChargePattern", 
			"params": { 
				"path": "octopus/pattern/simplePattern.simpleAttack", 
				"partType": "gun", // the name of the unit part to charge the pattern on
				"partSelect":"All" // if multiple parts of the same name exist, charge from all of them
				"chargeTime":1, // how long the pattern will charge up before shooting
				"dir":"(playerPos + playerVel * 1f) - partPos", // aim at the player, and lead them a bit
			}
		},
		```
	??? abstract "Anchoring a pattern to a bullet"
		The easiest way to make a pattern move around the way you want is to anchor it to a bullet. The bullet anchor can be invisible and non-colliding, and simply function as a vehicle to move the pattern around. When calling this from a bullet it's unnecessary to specify the `target`.
		```json
		{ "action": "CallMethod", "method": "AddPattern", "params": { "path": ".myChildPattern", "pos":"bulletPos", "angle":"vecToAngle(playerPos - bulletPos)" }},
		```
		```json
		{ "action": "CallMethod", 
			"method": "AddPattern", 
			"params": { 
				"path": ".myChildPattern",
				"pos":"bulletPos", // the position of the parent bullet
				"angle":"vecToAngle(playerPos - bulletPos)"
			}
		},
		```
## Other Pattern Shapes

Instead of having patterns shoot outward from a central point, you may want to spawn bullets in precise or odd configurations. 

### Custom

Setting the `patternShape` to `Custom` lets you decide the position and orientation of each bullet.

```json hl_lines="2 5 8"
"1": {
  "patternShape":"Custom",

  // spawn the bullets in a circle arount the player
  "customBulletPos": "playerPos + angleToVec((volleyNum / float(numVolleys)) * 360f) * 40f",

  // spawn them aiming towards the player
  "customBulletAngle":"vecToAngle(playerPos - bulletPos)",

  "numVolleys": 40,
  "numBulletsInVolley":1,
  "shootDelay": 0.01,
  "bullets": [".bullet"],
  "sfxVolley": "ShootSoftWomp",
},
```

<video controls> <source src="https://s3-eu-west-1.amazonaws.com/files.facepunch.com/ryleigh/1b1611b1/2019-08-16_00-05-48.mp4" type="video/mp4"> </video>

### Manual

Setting the `patternType` to `Manual` means the pattern will wait for you to manually call Actions to shoot volleys or end the pattern.

<video controls> <source src="https://s3-eu-west-1.amazonaws.com/files.facepunch.com/ryleigh/1b1611b1/2019-08-16_00-11-35.mp4" type="video/mp4"> </video>

That type of pattern would have been challenging to express as a single `customBulletPos` function, so the actions were called manually.

??? info "Full json file"
	  ```json hl_lines="3 11 104"
	  {
	    "1":{
	      "patternShape": "Manual",
	      "properties": {
	        "size": { "type": "Float", },
	        "startPos": { "type": "Vector2", },
	        "pos": { "type": "Vector2", },
	        "count": { "type": "Int", },
	        "amount": { "type": "Int", },
	      },
	      "behaviour": ".fsm",
	      "bulletIndex": 0,
	      "arcAngle": "360f",
	      "dragBullets": false,
	      "chargeColor": "color(1f, 0f, 0f) * 10f",
	      "shootColor": "color(1f, 0f, 0f) * 8f",
	      "shootColorTime":0.25,
	      "shootColorEasingType": "QuadIn",
	      "vibrationStrength":"0.33f",
	      "maxVibrationDist":10,
	      "vibrationHorizThreshold":5,
	      "sfxVolley": "ShootPump",
	      "numVolleysPerShootSfx": 1,
	    },

	    // =============================================================================================================================================================================
	    "bullet": {
	      "keyframes": [
	      {
	        "duration":0.5,
	        "acceleration":0,
	        "frictionPercent":0,
	        "colorA1":{"r":0,"g":0,"b":1,"a":0.9},
	        "colorA2":{"r":0,"g":0,"b":1,"a":0.7},
	        "colorB1":{"r":0,"g":0,"b":1,"a":0.8},
	        "colorB2":{"r":0,"g":0,"b":1,"a":0.6},
	        "colorC1":{"r":0,"g":0,"b":1,"a":0.8},
	        "colorC2":{"r":0,"g":0,"b":1,"a":0.6},
	        "colorBlinkTime":0.5,
	        "easingType":"QuadOut",
	        "loopEnd": 1,
	        "glowA": 6,
	        "glowB": 6,
	        "glowC": 6,
	        "opacity":0,
	        "facingSpeedPercent": 0.5,
	        "sprite":"sprites/circle/thinEdge",
	        "ignorePlayerCollision":true,
	        "radius":4,
	      },
	      {
	        "duration":1.5,
	        "frictionPercent":0.035,
	        "radius": { "mode": "PerUpdate", "value": "1.66f + fastSin(bulletTime * 25f) * map(lifetimeProgress, 0f, 1f, 0f, 0.2f, 'ExpoOut')" },
	        "glowA": 0.66,
	        "glowB": 0.33,
	        "glowC": 0.5,
	        "loopEnd": 1,
	        "opacity":0.75,
	        "ignorePlayerCollision":false,
	        "colorA1":{"r":1,"g":0.5,"b":0.25,"a":0.9},
	        "colorA2":{"r":1,"g":0.25,"b":0.25,"a":0.7},
	        "colorB1":{"r":0.8,"g":0.4,"b":0.25,"a":0.8},
	        "colorB2":{"r":0.9,"g":0.2,"b":0.25,"a":0.6},
	        "colorC1":{"r":1,"g":0.25,"b":0.25,"a":0.8},
	        "colorC2":{"r":1,"g":0,"b":0.25,"a":0.6},
	      },
	      {
	        "duration":0.15,
	        "colorBlinkTime":0.05,
	        "glowA": 2.66,
	        "glowB": 0.33,
	        "glowC": 0.33,
	        "colorA1":{"r":1,"g":0.15,"b":0,"a":0.9},
	        "colorA2":{"r":1,"g":0.25,"b":0,"a":0.8},
	        "colorB1":{"r":0.8,"g":0.4,"b":0,"a":0.8},
	        "colorB2":{"r":0.9,"g":0.2,"b":0,"a":0.6},
	        "colorC1":{"r":1,"g":0.25,"b":0,"a":0.8},
	        "colorC2":{"r":1,"g":0,"b":0,"a":0.6},
	        "onKeyframe":[
	          { "action": "CallMethod", "target":"stage", "method": "PlaySfx", "params": { "sfxType":"InvasionXAttack", "pos":"bulletPos", }},
	        ],
	      },
	      {
	        "duration":0,
	        "acceleration":300,
	        "moveAngle":"vecToAngle(playerPos - bulletPos)",
	      },
	      ],
	      "startSpeed":0,
	      "lifetime":30,
	      "shouldLoop":false,
	      "despawnAfterKeyframes":false,
	      "depthLevel": "BulletBottom",
	      "shapeType": "Circle",
	      "impulseFrictionPercent":0.05,
	      "despawnTime":0.15,
	      "useAbsoluteAngles":true,
	      "circleSkew":0.5,
	      "circleSkewDist":1,
	    },

	    // =============================================================================================================================================================================
	    "fsm": {
	      "0": [
	        { "action": "SetValue", "name": "size", "value": 3 },
	        { "action": "SetValue", "name": "startPos", "value": "playerPos + (playerPos.y < 0f ? vec2(0f, 20f) : vec2(0f, -20f))" },
	        { "action": "SetValue", "name": "amount", "value": "roundToInt(map(patternNum, 0, 7, 6f, 12f, 'SineInOut'))" },

	        { "action": "SetValue", "name": "pos", "value": "startPos" },
	        { "action": "SetValue", "name": "count", "value": 0 },
	        { "action": "Repeat", "count": "amount", "delay": 0.02, "inner": [
	          { "action": "SetValue", "name": "pos", "value": "pos + rotateAround(vec2(0.7f, 0.7f), (map((nspc * patternNum) % 5, 0, 4, 0f, 45f) + rand.Float(0f, map(patternNum, 0, 6, 0f, 100f))) * (patternNum % 2 == 0 ? -1f : 1f)) * size" },
	          { "action": "CallMethod", "method": "AddBullet", "params": { "pos": "pos", "path": ".bullet", }}, 
	          { "action": "CallMethod", "target":"stage", "method": "PlaySfx", "params": { "sfxType":"InvasionXSpawn", "pos":"pos", "pitchModifier":"map(count, 0, float(amount), 0.8f, 1.5f, 'QuadIn')" }},
	          { "action": "SetValue", "name": "count", "value": "count + 1" },
	        ]},

	        { "action": "SetValue", "name": "pos", "value": "startPos" },
	        { "action": "SetValue", "name": "count", "value": 0 },
	        { "action": "Repeat", "count": "amount", "delay": 0.02, "inner": [
	          { "action": "SetValue", "name": "pos", "value": "pos + rotateAround(vec2(0.7f, -0.7f), (map((nspc * patternNum) % 5, 0, 4, 0f, 45f) + rand.Float(0f, map(patternNum, 0, 6, 0f, 100f))) * (patternNum % 2 == 0 ? -1f : 1f)) * size" },
	          { "action": "CallMethod", "method": "AddBullet", "params": { "pos": "pos", "path": ".bullet", }},
	          { "action": "CallMethod", "target":"stage", "method": "PlaySfx", "params": { "sfxType":"InvasionXSpawn", "pos":"pos", "pitchModifier":"map(count, 0, float(amount), 0.8f, 1.5f, 'QuadIn')" }},
	          { "action": "SetValue", "name": "count", "value": "count + 1" },
	        ]},

	        { "action": "SetValue", "name": "pos", "value": "startPos" },
	        { "action": "SetValue", "name": "count", "value": 0 },
	        { "action": "Repeat", "count": "amount", "delay": 0.02, "inner": [
	          { "action": "SetValue", "name": "pos", "value": "pos + rotateAround(vec2(-0.7f, 0.7f), (map((nspc * patternNum) % 5, 0, 4, 0f, 45f) + rand.Float(0f, map(patternNum, 0, 6, 0f, 100f))) * (patternNum % 2 == 0 ? -1f : 1f)) * size" },
	          { "action": "CallMethod", "method": "AddBullet", "params": { "pos": "pos", "path": ".bullet", }},
	          { "action": "CallMethod", "target":"stage", "method": "PlaySfx", "params": { "sfxType":"InvasionXSpawn", "pos":"pos", "pitchModifier":"map(count, 0, float(amount), 0.8f, 1.5f, 'QuadIn')" }},
	          { "action": "SetValue", "name": "count", "value": "count + 1" },
	        ]},

	        { "action": "SetValue", "name": "pos", "value": "startPos" },
	        { "action": "SetValue", "name": "count", "value": 0 },
	        { "action": "Repeat", "count": "amount", "delay": 0.02, "inner": [
	          { "action": "SetValue", "name": "pos", "value": "pos + rotateAround(vec2(-0.7f, -0.7f), (map((nspc * patternNum) % 5, 0, 4, 0f, 45f) + rand.Float(0f, map(patternNum, 0, 6, 0f, 100f))) * (patternNum % 2 == 0 ? -1f : 1f)) * size" },
	          { "action": "CallMethod", "method": "AddBullet", "params": { "pos": "pos", "path": ".bullet", }},
	          { "action": "CallMethod", "target":"stage", "method": "PlaySfx", "params": { "sfxType":"InvasionXSpawn", "pos":"pos", "pitchModifier":"map(count, 0, float(amount), 0.8f, 1.5f, 'QuadIn')" }},
	          { "action": "SetValue", "name": "count", "value": "count + 1" },
	        ]},

	        { "action": "CallMethod", "method": "Finish", },
	      ],
	    },
	  }
	  ```

## Affecting Child Bullets

Patterns have their own position and angle, and their movement can be applied to bullets they've fired.

```json
"childPattern": {
	// ...
	"dragBullets": true, // affect bullet position as pattern position changes
	"rotateBullets": true, // affect bullet position as pattern rotation changes
	"rotateBulletAngles":true, // affect bullet rotation as pattern rotation changes
	"waitForBulletsToDespawn":true, // dont despawn until all bullets have despawned
},
```

<video controls> <source src="https://files.facepunch.com/ryleigh/1b2011b1/2019-08-20_16-12-32.mp4" type="video/mp4"> </video>

On the left, `dragBullets` is true.<br>
In the center, `dragBullets` and `rotateBullets` are true.<br>
On the right,  `dragBullets` and `rotateBullets` and `rotateBulletAngles` are true.<br>

<img src="https://files.facepunch.com/ryleigh/1b2011b1/Chippy_2019-08-20_18-49-15.png"/><br>
To produce the attack in the image above:
> 1) A very simple pattern shoots the faded blue bullet, then the pattern despawns

> 2) On its first keyframe, the blue bullet shoots a second pattern and anchors it to itself

> 3) The second pattern fires the red diamond bullets, and drags them along as the blue bullet drags *it*

??? info "Full json file"
	```json
	{
		"1":{
			"patternShape": "Spokes",
			"numVolleys": 1,
			"numBulletsInVolley": "1",
			"shootDelay": "0f",
			"rotationSpeed": "-80f - ((patternNum % 3) * 20f)",
			"arcAngle": "360f",
			"bullets": [".parentBullet1"],
			"dragBullets": false,
			"chargeColor":"color(1f, 0f, 0f) * 8f",
			"shootColor":"color(1f, 0f, 0f) * 10f",
			"shootColorTime":0.25,
			"shootColorEasingType": "QuadIn",
			"vibrationStrength":"0.33f",
			"maxVibrationDist":10,
			"vibrationHorizThreshold":5,
			"sfxCharge":"OctopusF1OrbCharge",
			"sfxVolley": "OctopusF1OrbShoot",
			"numVolleysPerShootSfx": 1,
		},

		"2":{
			"#include":".1",
			"bullets": [".parentBullet2"],
		},

		"3":{
			"#include":".1",
			"bullets": [".parentBullet3"],
		},
		
		"parentBullet1": {
			"keyframes": [
			{
			"duration":0,
			"acceleration":6,
			"frictionPercent":0.025,
			"opacity":0.2,
			"radius":5,
			"sprite":"sprites/circle/simple",
			"colorA1":{"r":1,"g":0,"b":1,"a":0.9},
			"colorA2":{"r":1,"g":0,"b":1,"a":0.8},
			"colorB1":{"r":0,"g":0,"b":1,"a":0.33},
			"colorB2":{"r":0,"g":0,"b":1,"a":0.5},
			"colorC1":{"r":1,"g":0.33,"b":1,"a":0.5},
			"colorC2":{"r":1,"g":0.22,"b":1,"a":0.66},
			"onKeyframe":[{ "action": "CallMethod", "method": "AddPattern", "params": { "path": ".childPattern1", }},],
			},
			],
			"startSpeed":0,
			"lifetime":200,
			"shouldLoop":false,
			"despawnAfterKeyframes":false,
			"depthLevel": "Bullet",
			"shapeType": "Circle",
			"despawnTime":0.05,
			"outOfBoundsRadiusFactor":5,
			"mass":2,
			"ignorePlayerCollision":true,
		},

		"parentBullet2":{
			"#include":".parentBullet1",
			"keyframes": [
				{
				"#include": ".parentBullet1.keyframes[0]",
				"onKeyframe":[{ "action": "CallMethod", "method": "AddPattern", "params": { "path": ".childPattern2", }},],
				},
			],
		},

		"parentBullet3":{
			"#include":".parentBullet1",
			"keyframes": [
				{
				"#include": ".parentBullet1.keyframes[0]",
				"onKeyframe":[{ "action": "CallMethod", "method": "AddPattern", "params": { "path": ".childPattern3", }},],
				},
			],
		},

		"childPattern1": {
			"patternShape": "Custom",
			"numVolleys": 1,
			"numBulletsInVolley": "5",
			"customBulletPos": "patternPos + vec2(0f, 1f) * bulletNum * 5f",
			"customBulletAngle": 0,
			"shootDelay": "0f",
			"bulletIndex": 0,
			"rotationSpeed": "-50f",
			"arcAngle": "360f",
			"bullets": [".childBullet"],
			"dragBullets": true,  
			"rotateBullets": false,
			"rotateBulletAngles":false,
			"waitForBulletsToDespawn":true,
			"constantRotation":true,
			"chargeColor":"color(1f, 0f, 0f) * 8f",
			"shootColor":"color(1f, 0f, 0f) * 10f",
			"shootColorTime":0.25,
			"shootColorEasingType": "QuadIn",
			"vibrationStrength":"0.33f",
			"maxVibrationDist":10,
			"vibrationHorizThreshold":5,
			"sfxVolley": "ShipShoot",
			"numVolleysPerShootSfx": 1,
			"debugVector":"patternDir * 5f",
		},

		"childPattern2":{
			"#include":".childPattern1",
			"dragBullets": true,  
			"rotateBullets": true,
			"rotateBulletAngles":false,
		},

		"childPattern3":{
			"#include":".childPattern1",
			"dragBullets": true,  
			"rotateBullets": true,
			"rotateBulletAngles":true,
		},

		"childBullet": {
			"keyframes": [
			{
			"duration":0.5,
			"frictionPercent":0.05,
			"colorA1":{"r":1,"g":0,"b":0.1,"a":0.9},
			"colorA2":{"r":1,"g":0,"b":0.05,"a":0.8},
			"colorB1":{"r":0,"g":0,"b":0.075,"a":0.33},
			"colorB2":{"r":0,"g":0,"b":0.1,"a":0.5},
			"colorC1":{"r":1,"g":0.33,"b":0,"a":0.5},
			"colorC2":{"r":1,"g":0.22,"b":0,"a":0.66},
			"colorBlinkTime":0.5,
			"easingType":"ExpoOut",
			"loopEnd": 1,
			"glowA": 8,
			"glowB": 8,
			"glowC": 8,
			"opacity":0,
			"sprite":"sprites/diamond/simple",
			},
			{
			"duration":2,
			"length":5,
			"crossWidth":4,
			"crossDistance":0.66,
			"easingType":"ExpoInOut",
			"glowA": 3.75,
			"glowB": 0.33,
			"glowC": 0.33,
			"opacity":1,
			},
			],
			"startSpeed":0,
			"lifetime":200,
			"shouldLoop":false,
			"despawnAfterKeyframes":false,
			"depthLevel": "Bullet",
			"shapeType": "Diamond",
			"despawnTime":1,
			"mass":99,
			"anchored":true,
		},
	}
	```

### Linking Volley Bullets

A pattern can choose to **link** all bullets in a volley.

```json
"linkedPattern": {
	"linkVolleyBullets":true,
},
```

If one linked bullet despawns, all other bullets in the linked volley will despawn - this is useful for powerup patterns, among other things.

## Visual Effects

Patterns can declare another pattern to be spawned as their "shoot effect":

```json
"attack":{
	// ...
	"shootEffectPattern": "misc/pattern/shoot/fanRedRound",
},
```

This will spawn the effect at the position of the shooting pattern, and pointed in the same direction.

## Callbacks

You may want to call Actions at certain points during a pattern.

```json
"pattern":{
	// ...
	"onStart":[
		// called when the pattern begins
		{ "action": "CallMethod", "target":"stage", "method": "ShakeCamera", "params": { "strength": 2, "time": 0.75, "easingType": "QuadOut" }},
	],    

	"onVolley":[ /* called when the pattern starts a volley */ ],
	"onBullet":[ /* called when the pattern fires a bullet */ ],
	"onUpdate":[ /* called each frame the pattern is active */ ],
	"onFinish":[ /* called when the pattern despawns */ ],
},
```

## Behaviour

## Params

## Custom Variables

## Workflow

??? tip "Extending other patterns"
	Patterns can **include** other patterns and change only specifed properties, keeping the rest the same as the original.
	```json
	"simpleAttack_rng_bs": {
	  "#include":".simpleAttack",
	  "numBulletsInVolley":"rand.Int(1, 30)",
	  "arcAngle":"rand.Float(10f, 360f)",
	},
	```
	<video controls> <source src="https://files.facepunch.com/ryleigh/1b0811b1/2019-08-08_23-33-03.mp4" type="video/mp4"> </video>

## Debugging

`debugVector`: draws a 2d vector from the pattern position <br>
`debugText`: displays a string above the pattern position (use `${NAME}` for properties)
```json
"simpleAttack": {
  ...
  "debugVector":"patternDir * 30f",
  "debugText":"volleyNum: ${volleyNum}, angle: ${patternAngle}",
  "waitForBulletsToDespawn":true, // pattern persists until all its bullets have despawned (normally, patterns end when all have been fired)
},
```
<video controls> <source src="https://files.facepunch.com/ryleigh/1b0911b1/2019-08-09_00-57-28.mp4" type="video/mp4"> </video>
