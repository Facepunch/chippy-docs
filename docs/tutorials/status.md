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

## Player Modifiers

[Player modifiers](../../SpaceUsurper/StatusEffectPlayerModifierData) are easy ways to change certain properties of the player while a status is active.

The modifiers can be expressed as a simple value or as a script func that is constantly updated.

```json
{
    "modifiers": {
        // multiplier to player's movement speed
        "moveSpeedMultiplier": 1.5,

        // multiplier to player's movement friction
        "frictionMultiplier":0.5,

        // amount added to `playerDamageBonus` property, which bullets can add to their damage
        "damageAmount": "level * 0.38f",

        // multiplier to player's opacity
        "opacityMultiplier":"map(playerGrazePercent, 0f, 1f, 0.5f, 1f, 'SineOut')",

        // while true, player can safely move through bullets, pixels, and lasers
        "intangible": "dist(playerVel) < 0.1f",

        // amount to add to player's bullet avoidance strength
        "avoidBulletsAmount":0.6,

        // how much to reverse player's move/aim input (0-1)
        "reverseInputPercent":"0.5f + sin(stageTime * 2f) * 0.5f",
    },
}
```

## Items

### Selectable

The `isSelectable` property differentiates **items** from passive effects.

```json
{
    "isSelectable":true,
}
```

If `isSelectable` is true, an item will show up in the player's item bar and can be selected.

### Activation

For a status effect intended to be used as an active item, you should define the `onActivate` handler. This handler is triggered when the player presses the "use item" button while this status effect is selected.
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

The `charge` properties are a convenient way to do time-based effects, though more complicated functionality can be done with custom variables and the `onUpdate` handler.

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

## Handlers

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

The `auxText` is the little number on the upper right corner of a status icon. 

<img src="https://files.facepunch.com/ryleigh/1b2611b1/Chippy_2019-08-26_21-17-19.png" />

Generally it indicates the level (quantity) of an item, but it could potentially be used as a countdown timer, show the number of enemies around you, things like that.

```json
{
    "auxText": "${level > 1 ? level.ToString() : ''}",
    "auxTextColor": "#707c7f",
}
```

### Category

The `category` of a status effect just affects the colors of its icon background.

```json
{
    "category": "categories.offensive",
}
```

You can define a new category wherever you want.

```json
"category": ".red",

"red": {
    "color1":"color(1f, 0f, 0f) * 1.5f",
    "color2":"color(1f, 0f, 0f) * 0.1f",
},
```

<img src="https://files.facepunch.com/ryleigh/1b2611b1/Chippy_2019-08-26_21-33-52.png" />

!!! tip
    If you want to replace a powerup with your own tweaked version, you can simply copy it to the same relative path and edit it, and your edited version will be loaded instead of the original.

    For example, `status/repel` is the path of the original. Placing your edited version at `your_campaign_folder/status/repel` will cause your version of the powerup to override the original.

## Name & Description

```json
{
    "displayName":"Shield",
    "description":"Prevent death ${level} ${level > 1 ? 'times' : 'time'}",
}
```

<img src="https://files.facepunch.com/ryleigh/1b2611b1/Chippy_2019-08-26_21-56-39.png" />

## Indicator Bullet

The items in chippy each show a different visual indicator on your ship while you have them selected.

<video controls> <source src="https://files.facepunch.com/ryleigh/1b2611b1/2019-08-26_22-01-33.mp4" type="video/mp4" > </video>

The `onSelect` and `onDeselect` handlers are used to accomplish this.

```json
{
    "onSelect": [
        { "action": "CallMethod", "method": "DespawnAddedBullets", },
        { "action": "CallMethod", "method": "AddBullet", "params": { "path": ".effectBullet", "pos":"playerPos", "level":"level", }},

        { "action": "CallMethod", "target": "stage", "method": "PlaySfx", "params": { "sfxType":"PowerupSlowmoSelect", "pos":"playerPos", }},
    ],

    "onDeselect": [
        { "action": "CallMethod", "method": "DespawnAddedBullets", },
    ],
}
```

## Custom Variables

Much like other json object types, status effects can declare custom properties.

```json
{
    "properties": {
        "aimer": { "type": "Bullet" },
        "aimer2": { "type": "Bullet" },
    },

    "onSelect": [
        { "action": "CallMethod", "method": "DespawnAddedBullets", },
        { "action": "CallMethod", "method": "AddBullet", "params": { "path": ".aimer", "pos": "stage.IsRaycastHit(playerGunPos, playerGunPos + playerGunDir * 60f) ? stage.Raycast(playerGunPos, playerGunPos + playerGunDir * 60f) : playerGunPos + playerGunDir * 8f", "level":"level", }, "return": "aimer" },
        { "action": "CallMethod", "method": "AddBullet", "params": { "path": ".aimer2", "pos": "playerPos", "level":"level", }, "return": "aimer2" },

        { "action": "CallMethod", "target": "stage", "method": "PlaySfx", "params": { "sfxType":"PowerupCannonSelect", "pos":"playerPos", }},
    ],

    "onDeselect": [
        { "action": "CallMethod", "method": "DespawnAddedBullets", },
    ],

    "onUpdate": [
        { "action": "Condition", "condition": "isSelected && aimer2 != null && aimer != null",
          "true": [ 
            { "action": "CallMethod", "target": "aimer2", "method": "SetVectorVar", "params": { "var":"aimer.Position - playerPos", }},
          ],},
    ],
}
```

## Debugging

`debugVector`: draws a 2d vector from the player's position <br>
`debugText`: displays a string above the player's position (use `${NAME}` for properties)