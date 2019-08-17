# Units

A **unit** is anything that has pixels. <br>
Bosses are units, minions are units, shield containers are units, etc.

## Config

## Movement

### Avoiding Other Units
 
### Level Boundary

## Forms

## Pixels

### PixelType

- normal
- invulnerable
- explosive


### Importing Pixels

### Texture

### Pixel Effects

- Splash Damage
- Transform Line
- Transform Ring
- Spark

### Pixel Chunks

## Animations

### Config

### Playback

## Behaviour

### Charging Patterns

## Callbacks

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

To modify them, use the SetValue method:

```json
{ "action": "SetValue", "name": "revengeCounter", "value": "revengeCounter + 1" },
```

## Params

## Speech Bubbles

## Debugging