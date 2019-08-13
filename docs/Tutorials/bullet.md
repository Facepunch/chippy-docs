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

### Color

### Sprite

### Movement

### Looping

<!-- ## Script Functions -->

### PerUpdate Functions

## Pixel Collision

## Player Collision

## Visual Effect Bullets

## Callbacks

## Params

## Floating Text

## Debugging

- bubble example
