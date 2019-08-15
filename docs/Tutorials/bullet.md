# Bullets

## Data

Bullet definitions can be stored in their own json file, but it's usually easier to include them in the same file as the pattern that uses them.

??? example "Defined in its own file"
	This is the entire content of an example bullet file, lets say `MyCampaign/bullet/myBullet.json`.
    ```json
    {
    	"keyframes": [
    	    {
    	      // keyframe 0
    	    },
    	    {
    	      // keyframe 1
    	    },
	    ],
	    // non-keyframe bullet properties"
    }
    ```
    When referencing this bullet in a pattern, the `path` would be `MyCampaign/bullet/myBullet`.

??? example "Included with pattern"
	This is the entire content of an example bullet file, lets say `MyCampaign/pattern/myPattern.json`.
    ```json
    {
	  	"1": {
			"bullets": [".bullet"],
			// other pattern properties
	  	},

	  	"2": {
			"bullets": [".bullet"],
			// other pattern properties
	  	},

	  	"bullet": {
	        "keyframes": [
	    	    {
	    	      // keyframe 0
	    	    },
	    	    {
	    	      // keyframe 1
	    	    },
		    ],
		    // non-keyframe bullet properties"
	  	},
    }
    ```
    When referencing this bullet from a different file, the `path` would be `MyCampaign/pattern/myPattern.bullet`. As you can see above, when referencing it from within the same json object, you can just use `.bullet`.

    The `path` of the patterns would be `myCampaign/pattern/myPattern.1` and `myCampaign/pattern/myPattern.2`, when spawning them with Actions.

## Bullet Properties

Most properties of a bullet are part of its `keyframes` system, to simplify changing the state of a bullet between specific configurations. However some important properties can only be specified once for the bullet as a whole, instead of changing between its keyframes.

These are some of the most important non-keyframe properties for a bullet.

Property | Summary
:----------- |:-------------
`shapeType` | the shape of the bullet (`Circle`, `Diamond`, or `Rect`)     
`lifetime` | despawn after this many seconds
`startSpeed` | spawn with this velocity
`depthLevel` | the layer to draw the bullet on ([DepthLevel -->](../../SpaceUsurper/DepthLevel.md))

## Keyframes

Bullets have one or more keyframes, containing properties you can change over time.

???+ example "Diamond pattern example"
	```json
	{
	  "1": {
	    "numVolleys": 50,
	    "numBulletsInVolley":2,
	    "shootDelay": "volleyNum % 10 == 0 ? 0.33f : 0.05f", // this ternary operation sets shootDelay to 0.33s when the modulus operator (the % that returns the remainder) returns zero, or 0.05s otherwise
	    "bullets": [".bullet"],
	    "sfxVolley": "ShootSoftWomp",
	    "rotationSpeed":-100,
	  },

	  "bullet": {
	    "keyframes": [
	    {
	      // KEYFRAME 0
	      "duration":0.5,
	      "acceleration":66,
	      "frictionPercent":0.05,
	      "sprite":"sprites/diamond/simple",
	      "colorA1":{ "value": {"r":1,"g":0,"b":0,"a":0.6}},
	      "colorA2":{ "value": {"r":1,"g":0.1,"b":0,"a":0.7}},
	      "colorB1":{ "value": {"r":0.8,"g":0,"b":0,"a":0.6}},
	      "colorB2":{ "value": {"r":0.6,"g":0,"b":0,"a":0.7}},
	      "colorC1":{ "value": {"r":1,"g":0.1,"b":0.2,"a":0.4}},
	      "colorC2":{ "value": {"r":0.8,"g":0.2,"b":0.3,"a":0.5}},
	      "glowA": 0,
	      "glowB": 0.5,
	      "glowC": 2,
	      "colorBlinkTime":0.15,
	      "opacity":0,
	      "easingType":"QuadOut",
	    },
	    {
	   	  // KEYFRAME 1
	      "duration":1,
	      "opacity":1,
	      "length":8,
	      "crossWidth":2,
	      "crossDistance":0.3,
	      "easingType":"QuadIn",
	    },
	    {
	      // KEYFRAME 2
	      "duration":0,
	      "crossWidth":12,
	      "crossDistance":0.7,
	    },
	    ],
	    "startSpeed":33,
	    "lifetime":30,
	    "depthLevel": "Bullet",
	    "shapeType": "Diamond",
	  },
	}
	```
	<video controls> <source src="https://files.facepunch.com/ryleigh/1b1211b1/2019-08-12_21-46-12.mp4" type="video/mp4"> </video>

	This bullet spends `0.5` seconds in its first keyframe, eases the values to the 2nd keyframe with the easing type `QuadOut` (quickly approach target value, then slow down as you reach it), then spends `1` second easing in to the 3rd keyframe with an easing type of `QuadIn` (slowly begin changing to target value, then quickly reach it).

	You can see that the `width` of the bullet quickly reaches the value in keyframe 1 (the second keyframe), before slowly easing into the large `width` in keyframe 2. Since keyframe 2 does not specify a new `length`, `opacity`, etc, the bullet continues to use the last value that was set.

### Shape

#### Circle

Keyframe Property | Summary
:----------- |:-------------
`radius` | the size of the circle bullet from center to edge

Non-Keyframe Property | Summary
:----------- |:-------------
`circleSkew` | the amount the circle bullet should stretch forward when moving fast (purely visual, doesn't affect the hitbox)
`circleSkewDist` | the distance required per frame to skew the max amount specified in `circleSkew`
`circleSkewEasingType` | how quickly to ease from no skew to full skew

```json
"circleBullet": {
    "keyframes": [
  	    {
  	      // ...
  	      "radius":2, // default is 0
  	    },
  	    {
  	      // ...
  	      "radius":4,
  	    },
    ],
    // ...
    "shapeType": "Circle",
    "circleSkew":0.2, // default is 0
    "circleSkewDist":1, // default is 0
    "circleSkewEasingType":"QuadIn", // default is Linear
},
```

<img src="https://files.facepunch.com/ryleigh/1b1311b1/Photo_2019-08-13_1_05_03_AM.jpg" width="400"/>

#### Diamond

Keyframe Property | Summary
:----------- |:-------------
`length` | length of diamond bullet
`crossWidth` | width of bullet at the widest point
`crossDistance` | how far forward the center of the bullet is

```json
"diamondBullet": {
    "keyframes": [
  	    {
  	      // ...
  	      "length":2, // default is 0
  	      "crossWidth":1, // default is 0
  	      "cross":0.33, // default is 0.5
  	    },
  	    {
  	      // ...
  	      "length":4,
  	      "crossWidth":1.5,
  	      "cross":0.66,
  	    },
    ],
    // ...
    "shapeType": "Diamond",
},
```

<img src="https://files.facepunch.com/ryleigh/1b1311b1/Photo_2019-08-13_1_18_22_AM.jpg" width="600"/>

#### Rect

Keyframe Property | Summary
:----------- |:-------------
`rectSize` | the width and length of the rectangle - `vec2(width, length)`
`rectWidthMods` | scaling applied to widths - `vec2(back width scale, front width scale)`

```json
"rectBullet": {
    "keyframes": [
  	    {
  	      // ...
  	      "rectSize":"vec2(4f, 2f)", // default is vec2(1f, 1f)
  	      "rectWidthMods":"vec2(0.5f, 1f)",  // default is vec2(1f, 1f)
  	    },
  	    {
  	      // ...
  	      "rectSize":"vec2(2f, 4f)",
  	      "rectWidthMods":"vec2(1f, 0f)", 
  	    },
    ],
    // ...
    "shapeType": "Rect",
},
```

<img src="https://files.facepunch.com/ryleigh/1b1311b1/Photo_2019-08-13_1_33_28_AM.jpg" width="600"/>

### Sprite

Bullets need to specify a sprite in their first keyframe. If a different sprite is specified in the next kefyrame, the bullet will blend into it over the current keyframe's duration. All the sprites used by a bullet need to have the same dimensions.

```json
"keyframes": [
    {
      // ...
      "sprite":"sprites/circle/simple",
    },
    {
      // ...
      "sprite":"sprites/circle/triangle2",
    },
]
```

### Color

Bullets don't reproduce their sprites exactly - instead they use color substitution to replace the red, blue, and green elements of the sprite with their own colors.

<img src="https://s3-eu-west-1.amazonaws.com/files.facepunch.com/ryleigh/1b1311b1/simple.png" width="150"/>

When using the above sprite, a bullet would choose what color they want to replace red with, green with, and blue with.

```json
"bullet": {
  "keyframes": [
    {
      // ...
      "sprite":"sprites/circle/simple",
      "colorA1":{ "value": {"r":1,"g":0,"b":0,"a":0.9}},
      "colorA2":{ "value": {"r":1,"g":0.2,"b":0,"a":0.7}},
      "colorB1":{ "value": {"r":1,"g":0,"b":0.1,"a":0.8}},
      "colorB2":{ "value": {"r":1,"g":0,"b":0.2,"a":0.6}},
      "colorC1":{ "value": {"r":1,"g":0.3,"b":0,"a":0.2}},
      "colorC2":{ "value": {"r":1,"g":0.4,"b":0,"a":0.1}},
      "glowA": 4,
      "glowB": 0.5,
      "glowC": 0,
      "colorBlinkTime":0.15,
    },
    // ...
  ],
},
```

In the above example, `colorA1` and `colorA2` will be used to replace the red portion of the sprite. `colorB1` and `colorB2` will be used to replace green, and `colorC1` and `colorC2` will replace blue.

So instead of appearing with red/green/blue rings, the bullet would be drawn like this:
<video controls> <source src="https://s3-eu-west-1.amazonaws.com/files.facepunch.com/ryleigh/1b1311b1/2019-08-13_23-26-46.mp4" type="video/mp4"> </video>

`glowA` is simply an additional factor that changes the strength of `colorA1` and `colorA2`. Alternatively, the colors themselves could be declared like this for the same effect:

```json
"colorA1":"color(1f, 0f, 0f, 0.9f) * 4f",
```

`colorBlinkTime` determines how rapidly the color pairs alternate - how quickly the red portion of the sprite blinks between `colorA1` and `colorA2`, etc.

### Movement 

A bullet's starting velocity is set with the non-keyframe property `startSpeed`. <br>
The keyframe property `acceleration` controls how fast they accelerate each frame <br>
The keyframe property `frictionPercent` is a value from `0-1` that controls how much of the bullet's speed is lost. A value of `0.1` means that the bullet will lose 10% of its velocity each frame.

#### Changing Direction

By default, bullets simply move forward in the direction their pattern spawns them in. Changing the keyframe property `moveAngle` will adjust the direction the bullet's `acceleration` moves them in.

The following bullet sets `"moveAngle":-90` on its third keyframe, which causes the bullet to turn 90° to the right, relative to its starting angle.

The blue line shows the bullet's current move direction, and the red line shows the bullet's current facing direction.

<video width="650" controls> <source src="https://s3-eu-west-1.amazonaws.com/files.facepunch.com/ryleigh/1b1411b1/2019-08-14_13-14-46.mp4" type="video/mp4" > </video>

??? info "Full json file"
    ```json
    {
      "1": {
        "numVolleys": 15,
        "numBulletsInVolley":3,
        "shootDelay": 0.5,
        "bullets": [".bullet"],
        "sfxVolley": "ShootSoftWomp",
        "rotationSpeed":-50,
      },

      "bullet": {
        "keyframes": [
        {
          "duration":0.5,
          "acceleration":5,
          "frictionPercent":0.25,
          "length":10,
          "crossWidth":4,
          "crossDistance":0.66,
          "sprite":"sprites/diamond/simple",
          "colorA1":{ "value": {"r":1,"g":0,"b":0,"a":0.9}},
          "colorA2":{ "value": {"r":1,"g":0.2,"b":0,"a":0.7}},
          "colorB1":{ "value": {"r":1,"g":0,"b":0.3,"a":0.8}},
          "colorB2":{ "value": {"r":1,"g":0,"b":0.6,"a":0.6}},
          "colorC1":{ "value": {"r":1,"g":0.3,"b":0.2,"a":0.5}},
          "colorC2":{ "value": {"r":1,"g":0.4,"b":0.2,"a":0.4}},
          "glowA": 2.5,
          "glowB": 0.5,
          "glowC": 1,
          "colorBlinkTime":0.25,
          "opacity":0,
          "easingType":"QuadOut",
          "facingSpeedPercent":0.1,
        },
        {
          "duration":1.5,
          "acceleration":66,
          "frictionPercent":0.05,
          "glowA": 3.5,
          "opacity":1,
          "easingType":"QuadIn",
        },
        {
          "duration":2.5,
          "moveAngle":-90,
        },
        ],
        "startSpeed":120,
        "lifetime":30,
        "depthLevel": "Bullet",
        "shapeType": "Diamond",
        "despawnTime":0.15,
        "onUpdate":[
          { "action": "CallMethod", "target":"stage", "method": "DrawDebugLine", "params": { "a": "bulletPos", "b":"bulletPos + facingDir * 12f", "color":"color(1f, 0f, 0f) * 2f"}},
          { "action": "CallMethod", "target":"stage", "method": "DrawDebugLine", "params": { "a": "bulletPos", "b":"bulletPos + angleToVec(moveAngle) * 7f", "color":"color(0.1f, 0.1f, 1f) * 3f"}},
        ],
      },
    }
    ```

#### Absolute Angles

If you want a bullet to interpret `"moveAngle":-90` as an absolute instead of relative angle, you can set the non-keyframe property `useAbsoluteAngles` to `true`.

```json
{
	"keyframes": [
	    // ...
	    {
	      // ...
	      "moveAngle":-90,
	    },
    ],
    // ...
    "useAbsoluteAngles":true,
}
```

<video controls> <source src="https://s3-eu-west-1.amazonaws.com/files.facepunch.com/ryleigh/1b1411b1/2019-08-14_15-10-35.mp4" type="video/mp4"> </video>

Now, the same bullets as before are all moving to the right on their third keyframe, instead of moving 90° to the right of their current angle.

For the record, this is the way angles are set up in Chippy:
<img src="https://s3-eu-west-1.amazonaws.com/files.facepunch.com/ryleigh/1b1411b1/Photo_2019-08-14_3_21_56_PM.jpg" width="450"/>

#### Direct Movement

It's possible to control a bullet's position directly, instead of relying on the physics of acceleration/velocity/deceleration.

```json
"keyframes": [
	// ...
	{
	  //...
	  "moveMode":"Target",
	  "targetPos":"playerPos",
	  "posLerpSpeed":0.01,
	},
],
```

When the bullet enters this keyframe, it will set its target position to the player's current location. From then on, its `posLerpSpeed` of `0.01` will move the bullet 1% of the remaining distance to the target per frame.

### Facing

By default, bullets don't rotate at all. By specifying a value from `0-1` for the keyframe property `facingSpeedPercent`, the bullet will ease toward a certain direction - normally the same direction as their velocity.

```json
"keyframes": [
	{
	  // ...
	  "facingSpeedPercent":0.1,
	},
],
```

For a bullet that rotates automatically instead of trying to face a certain direction, you can set the `facingMode` to `AutoRotate`, and setting the `rotationSpeed`.

```json
"keyframes": [
	{
	  // ...
	  "facingMode":"AutoRotate",
	  "rotationSpeed":"rand.Float(-100f, -500f)",
	},
],
```

<video controls> <source src="https://s3-eu-west-1.amazonaws.com/files.facepunch.com/ryleigh/1b1411b1/2019-08-14_15-59-56.mp4" type="video/mp4"> </video>

There are several other values for `facingMode`:

facingMode | Summary
:----------- |:-------------
`Velocity` | face toward velocity direction using `facingSpeedPercent`
`MoveAngle` | face toward current moveAngle using `facingSpeedPercent`
`Position` | face toward position delta using `facingSpeedPercent`
`Target` | face toward `targetFacingAngle` using `facingSpeedPercent`
`AutoRotate` | rotate using `rotationSpeed`

### Looping

Sometimes it's useful for a bullet to repeat keyframes multiple times. By setting the non-keyframe property `shouldLoop` to true, a bullet will continue looping through each keyframe unless told otherwise.

???+ info "Looping bullet definition"
	```json hl_lines="16 51"
	"bullet": {
	  "keyframes": [
		  {
		  	// KEYFRAME 0
		    "duration":0.5,
		    "acceleration":5,
		    "frictionPercent":0.25,
		    "crossDistance":0.66,
		    "sprite":"sprites/diamond/simple",
		    "glowA": 2.5,
		    "glowB": 0.5,
		    "glowC": 1,
		    "colorBlinkTime":0.25,
		    "opacity":0,
		    "easingType":"QuadOut",
		    "facingSpeedPercent":0.1,
		    "loopEnd":1, // keyframe ignored on loops greater or equal than 1
		  },
		  {
		  	// KEYFRAME 1
		    "duration":1,
		    "acceleration":150,
		    "frictionPercent":0.15,
		    "colorA1":{ "value": {"r":1,"g":0,"b":0.2,"a":0.9}},
		    "colorA2":{ "value": {"r":1,"g":0.05,"b":0.1,"a":0.7}},
		    "colorB1":{ "value": {"r":1,"g":0,"b":0.3,"a":0.8}},
		    "colorB2":{ "value": {"r":1,"g":0,"b":0.6,"a":0.6}},
		    "colorC1":{ "value": {"r":1,"g":0.1,"b":0.2,"a":0.5}},
		    "colorC2":{ "value": {"r":1,"g":0.25,"b":0.2,"a":0.4}},
		    "glowA": 5,
		    "opacity":1,
		    "easingType":"Linear",
		    "moveAngle":45,
		    "length":10,
		    "crossWidth":4,
		  },
		  {
		  	// KEYFRAME 2
		    "duration":1,
		    "colorA1":{ "value": {"r":0.5,"g":0.3,"b":0,"a":0.9}},
		    "colorA2":{ "value": {"r":0.5,"g":0.2,"b":0,"a":0.7}},
		    "colorB1":{ "value": {"r":0.5,"g":0.6,"b":0.3,"a":0.8}},
		    "colorB2":{ "value": {"r":0.5,"g":0.5,"b":0.6,"a":0.6}},
		    "colorC1":{ "value": {"r":0.5,"g":0.6,"b":0.2,"a":0.5}},
		    "colorC2":{ "value": {"r":0.5,"g":0.8,"b":0.2,"a":0.4}},
		    "glowA": 3,
		    "moveAngle":-45,
		    "length":8,
		    "crossWidth":5,
		  },
	  ],
	  "startSpeed":120,
	  "lifetime":30,
	  "shouldLoop":true, // loop keyframes
	  "depthLevel": "Bullet",
	  "shapeType": "Diamond",
	  "despawnTime":0.15,
	},
	```

<video width="650" controls> <source src="https://s3-eu-west-1.amazonaws.com/files.facepunch.com/ryleigh/1b1411b1/2019-08-14_23-42-12.mp4" type="video/mp4" > </video>

This bullet loops its second and third keyframe, but only plays its first keyframe once, thanks to `"loopEnd":1`. This means that the first keyframe (Keyframe 0) will be skipped when the number of times we've looped over this bullet's keyframes is >= 1, so it will be skipped the second time through.

The sequence of keyframes this bullet will follow is `0, 1, 2, 1, 2, 1, 2...`

The bullet wobbles back and forth, since its `moveAngle` constantly changes from `-45` to `45`. <br>
Its color and size changes too.

Some other properties that keyframes can use to change how bullet state flows:

Property | Summary
:----------- |:-------------
`loopStart` | Keyframe will be ignored until we are on loop number N or greater
`loopEnd` | Keyframe will be ignored if we are on or past loop number N (non-inclusive)
`loopModulus` | Keyframe active every N loops
`chance` | Chance of using keyframe (from 0 to 1)
`next` | Go to that frame number instead of the next one
	
## Script Functions

### PerUpdate Functions

## Pixel Collision

## Player Collision

## Visual Effect Bullets

## Callbacks

## Params

## Floating Text

## Debugging

- bubble example
