# Status Effects

Status Effects are used for both **active items** and **passive buffs/debuffs** applied to the player.

!!! info
	[Properties & Methods](../../SpaceUsurper/StatusEffect)

    [Full json config](../../SpaceUsurper/StatusEffectData)

## Levels

Set the max level of a status with `numLevels`:

```json
{
    "numLevels":3,
}
```

Levels can be used however you want. In the official Chippy levels, they represent the quantity of an item you have, but it could instead represent the strength of the item.

## Modifiers

## Items

### Selectable

The `isSelectable` property differentiates items from passive effects.

```json
{
    "isSelectable":true,
}
```

If `isSelectable` is true, an item will show up in the player's item bar and can be selected.

### Activation

For a status effect intended to be used as an active item, you should define the `onActivate` callback. This callback is triggered when the player presses the "use item" button while this status effect is selected.
```json
{
    "onActivate": [
        // your item's effect:
        { "action": "CallMethod", "target":"stage", "method": "ShakeCamera", "params": { "strength":0.5, "time":0.75, }},

        // typically, you want to remove one of the item stack when you use it
        { "action": "CallMethod", "method": "LevelDown" },
    ],
}
```

## Charge

The `charge` properties are a convenient way to do time-based effects, though more complicated functionality can be done with custom variables and the `onUpdate` callback.

The following is from an unused powerup that repelled nearby bullets after you closely graze a bullet long enough:

```json
{
    // this func is added to "charge" each frame (in this case, it's how closely a player is grazing bullets, from 0-1)
    "chargeIncrease":"playerGrazePercent",

    // when charge reaches this amount, "onExecute" is triggered,
    "chargeRequired":2.8,

    // apply this friction amount (0-1 value) to "charge" each frame (0.2 reduces charge by 20% each frame),
    "chargeDecay":0.2,

    "onExecute": [
        { "action": "CallMethod", "target":"stage", "method": "RepelBullets", "params": { "pos":"playerPos", "radius":100, "freezeTime":0.5, "color":"color(0.66f, 0.66f, 1f) * 1.15f", "strength":100, "effectBullet":"misc/bullet/effect/repel", "easingType":"QuadIn", }},

        { "action": "CallMethod", "method": "Disable" },
    ],
}
```

## Callbacks

You may want to call Actions at certain points during a status effect.

```json
{
    "onEnable":[
        // called when status effect is started (gains its first level)
        { "action": "CallMethod", "target":"stage", "method": "ShakeCamera", "params": { "strength": 3, "time": 0.5, "easingType": "QuadOut" }},
    ],    

    "onLevelUp":[ /* called when status effect gains a level */ ],
    "onMaxedOut":[ /* called when status effect gains a level but is already at max level */ ],
    "onLevelDown":[ /* called when status effect loses a level */ ],
    "onPreventDeath":[ /* called when status effect level is lost to prevent player death */ ],
    "onDisable":[ /* called when status effect is finished */ ],
    "onUpdate":[ /* called each frame the status effect is active */ ],
    "onActivate":[ /* called when player uses item when status effect is selected */ ],
    "onSelect":[ /* called when player selects status effect */ ],
    "onDeselect":[ /* called when player selects a different status effect, deselecting this one */ ],
    "onExecute":[ /* called when charge hits required amount */ ],
    "onPlayerHit":[ /* called when player is hit but does not die */ ],
},
```

## Icon

### Aux Text

### Category

## Name & Description

## Indicator Bullet

## Custom Variables

## Params

## Debugging

`debugVector`: draws a 2d vector from the player's position <br>
`debugText`: displays a string above the player's position (use `${NAME}` for properties)