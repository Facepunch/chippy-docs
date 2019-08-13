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

## Affecting Child Bullets

## Visual Effects

## Callbacks

## Params

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
