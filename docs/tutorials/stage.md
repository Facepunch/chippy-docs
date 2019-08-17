# Stages

## Config

The Stage config file handles spawning units and the player, setting the bounds of the arena, and various other things.

### Game Mode

#### Time Attack

This is the default mode. The goal is to win as fast as possible.

```json
{
	"gameMode": "TimeAttack",
}
```

#### Endless

The goal is to survive as long as possible. When time is slowed down or sped up in this mode, the game timer is affected too.

```json
{
	"gameMode": "Endless",
}
```

### Medal Times

### Player

### Units

- count
- requiredForVictory

#### Cross-Unit Requirements

## Behaviour

## Stage Patterns

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


## Adjusting Stage Size

## Behaviour

## Callbacks

## Params

## Custom Variables

## Camera Effects

## Background

## Debugging