# Unit Parts

A section of pixels can be grouped together as a **part**. Parts have a single health pool and can only be destroyed as a whole.

## Config

- corePath
    - difference from core
- spritePath
- hp

### Placing
- size
- placements
- different sizes for same core

## Protecting Parts

Parts can remain invulnerable until certain other parts are destroyed. Usually the **core** can't be destroyed until the other parts are gone.

In the following example, the `core` part will be protected & invulnerable until the two `smallGun` parts and the two `largeGun` parts are destroyed.

```json hl_lines="10"
{
	"forms":[
		{
			"parts":{
                "core": {
                    "corePath": "misc/core/invasion/core0",
                    "size": 18,
                    "placements": [ 900 ],
                    "hp": 2000,
                    "requires": [ "smallGun", "largeGun", ],
                },
                "smallGun": {
                    "corePath": "misc/core/invasion/smallGun",
                    "size": 11,
                    "placements": [ 1616, 1737 ],
                    "hp": 1000,
                },
                "largeGun": {
                    "corePath": "misc/core/invasion/largeGun",
                    "size": 14,
                    "placements": [ 1224, 1420 ],
                    "hp": 1200,
                },
			}
		},
	],
}
```

### Ropes

Parts have a visual "rope" connecting them to any parts they're protecting.

<img src="https://files.facepunch.com/ryleigh/1b2211b1/Chippy_2019-08-22_16-37-08.png" />

The visuals can be adjusted with optional parameters:

```json
{
    "parts":[
        "core": {
            "corePath": "misc/core/octopus/core0",
            "size": 8,
            "placements": [ 0 ],
            "hp": 900,
            "requires": [ "mid", "side" ],
            "ropeColorStart":"color(1f,0f,0f)",
            "ropeColorEnd":"color(1f,0f,0.66f) * 1.25",
            "ropeWobbleOpacityMin":0,
            "ropeWobbleOpacityMax":1,
            "ropeWobbleGlow":3,
            "ropeWobbleWidthMin":0,
            "ropeWobbleWidthMax":1,
            "ropeTightness":3,
            "ropeWidthLerpFunc":"mapReturn(ropeSpringNum, 0f, ropeNumSprings, 20f, 1f, 'QuadOut')",
            "ropeOpacityLerpFunc":"mapReturn(ropeCurrLength, 0f, ropeTotalLength, 0f, 1f, 'QuadIn')",
        },
    ],
}
```

??? info "All rope parameters"
    Property &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | Type | Summary | Default Value
    :----------- |:------------- |:------------- |:-------------
    `ropeColorStart` | Color | color at protecting part | `color(0.66f, 0.66f, 1f)`
    `ropeColorEnd` | Color | color at protected part | `color(0f, 0f, 1f)`
    `ropeOpacityNormal` | float | opacity when rope is slack | `0.5`
    `ropeOpacityStretched` | float | opacity when rope is stretched | `0.25`
    `ropeWidthFactorNormal` | float | width factor when slack | `0.66`
    `ropeWidthFactorStretched` | float | width factor when stretched | `0.4`
    `ropeWobbleWidthMin` | float | width factor when spring is not wobbling  | `0.25`
    `ropeWobbleWidthMax` | float | width factor when spring is wobbling | `2.5`
    `ropeWobbleGlow` | float | glow factor when spring is wobbling | `1`
    `ropeWobbleEasingType` | EasingType | how the wobble effect eases through rope | `QuadIn`
    `ropeWobbleDelayPerNode` | float | makes the wobble effect look interesting | `0.075`
    `ropeWobbleOpacityMin` | float | opacity factor when spring is not wobbling  | `0.1`
    `ropeWobbleOpacityMax` | float | opacity factor when spring is wobbling | `1`
    `ropeLength` | float | slack length of rope | `8`
    `ropeLengthEasingType` | EasingType | how length distributed through springs | `SineInOut`
    `ropeNumNodes` | int | how many nodes (and therefore springs) in rope | `5`
    `ropeTightness` | float | how much force springs apply to stay slack | `15`
    `ropeNodeTopSpeed` | float | controls how much friction the node has | `30`
    `ropeNodeFrictionMin` | float | friction at no speed | `0.01`
    `ropeNodeFrictionMax` | float | friction at top speed | `0.05`
    `ropeNodeMass` | float | how heavy the nodes are | `0.25`
    `ropeBlockWidthFactor` | float | width factor when protected part is being attacked  | `1.33`
    `ropeBlockOpacityFactor` | float | opacity factor when protected part is being attacked | `2`
    `ropeBlockGlowFactor` | float | glow factor when protected part is being attacked | `4`
    `ropeBlockColor` | Color | rope color when protected part is being attacked | `color(1f, 1f, 1f)`
    `ropeAnimSpeedNormal` | float | normal wobble speed | `0.25`
    `ropeAnimSpeedBlock` | float | wobble speed when protected part is being attacked | `3`

    !!! info
        The `wobble` properties refer to the pulsing effect that moves along the rope toward the protected part. For example, `ropeWobbleWidthMax` is the multiplier applied to the spring width when the full wobble effect has reached that spring.

    <br>
    The following func properties can be used to adjust things along the length of a rope:

    Property &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | Type | Summary
    :----------- |:------------- |:-------------
    `ropeWidthLerpFunc` | float | width of the rope at a given point
    `ropeOpacityLerpFunc` | float | opacity of the rope at a given point
    `ropeTightnessLerpFunc` | float | tightness of the rope at a given point
    `ropeGlowAddLerpFunc` | float | amount to add to rope's glow at a given point

    These variables are made available for using in the funcs:

    Property &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;| Type | Summary
    :----------- |:------------- |:-------------
    `ropeSpringNum` | int | the current spring we're considering
    `ropeNumSprings` | int | total number of springs in the rope
    `ropeCurrLength` | float | the amount of length we've traversed, at the current spring
    `ropeTotalLength` | float | the total length of the rope



## Lasers

## Callbacks

You may want to call Actions from a unit part.

```json
{
    "onSpawn":[
        // called when status effect is started (gains its first level)
        { "action": "CallMethod", "target":"stage", "method": "ShakeCamera", "params": { "strength": 3, "time": 0.5, "easingType": "QuadOut" }},
    ],    

    "onUpdate":[ /* called each frame while part is active */ ],
	"onDestroy":[ /* called when part is destroyed */ ],
	"onHit":[ /* called when part hit by bullet or laser */ ],
	"onHitProtected":[ /* called when part hit by bullet or laser and has other part shielding it */ ],
},
```

## Params

## Core Controllers

### Config

## Sprites

### Config

## Non-Rectangle Parts