# SFX

Sound effects are played with the Stage's `PlaySfx` action.

```json
{ "action": "CallMethod", "target":"stage", "method": "PlaySfx", "params": { "sfxType": "ShootForce", "pos":"vec2(0f, 10f)" }},
```

Some modifier parameters can be specified:

```json
{ "action": "CallMethod", "target":"stage", "method": "PlaySfx", 
    "params": { 
        "sfxType": "ShootForce", 
        "pos":"playerPos + vec2(0f, 10f)",
        "volumeModifier": 0.75,
        "pitchModifier": 1.2,
        "maxDistanceModifier": 0.5 // this sound will half 50% of the max distance (if the sound is farther away than max distance from the player, it will not be played)
    }
},
```

If the `pos` parameter is not specified, sounds will play at the player's position.

## Built-in SFX



## Custom SFX

You can also create a new json file to define custom sounds.

This is `sfx.json` from the **example** plugin.
```json
{
    "ExampleStage":  { 
        "volume": 1, 
        "pitchMin": 0.9, 
        "pitchMax": 1.2, 
        "maxDistance": 200, 
        "priority": 200, 
        "fileName": "sfx/example_stage", 
    },

    "Victory":  { "volume": 1, "pitchMin": 0.85, "pitchMax": 1.3, "maxDistance": 300, "priority": 200, "fileName": "sfx/victory", },
}
```

The **filename** property specifies that `example_stage.wav` is located in a folder called `sfx` located in the plugin folder.<br/>
The **maxDistance** property can make unimportant sounds not play if they are too far from the player.<br/>
The **priority** property isn't very important, but setting a lower priority means that those sounds will be skipped in the event that the audio engine is overloaded with sounds in a short period of time.

Trigger your custom sfx in the same way as the built-in sounds:
```json
{ "action": "CallMethod", "target":"stage", "method": "PlaySfx", "params": { "sfxType": "ExampleStage", }},
```

Don't forget to include the path to you sfx file(s) in your `plugin.json` file.
```json
{
  // load files from sfx.json, in the same folder as plugin.json
  "sounds": [ "sfx" ],
}
```


## Looping SFX

Looping sounds can be useful for lasers and other things that persist for a certain amount of time.

1. Call the stage's `StartLoopingSfx` action, storing the return value in an integer property. This value identifies the particular looping sound being created.
2. Change the properties of the sound over time using `SetLoopingSfxPosition`, `SetLoopingSfxVolume`, `SetLoopingSfxPitch`, and `SetLoopingSfxMaxDistance`. These actions require you to pass in the ID of the looping sound you want to modify.
3. Call `StopLoopingSfx` to end the looping sound.

```json
{
    // pattern stuff ...

    "properties": { "sfxId": { "type": "Int" }, },
    "onStart":[
      { "action": "CallMethod", "target": "stage", "method": "StartLoopingSfx", "params": { "sfxType":"LaserLoop", "pos":"vec2(0f, 0f)", }, "return":"sfxId" },
      { "action": "CallMethod", "target": "stage", "method": "SetLoopingSfxVolume", "params": { "id":"sfxId", "volume":0, }, },
    ],
    "onUpdate":[
      { "action": "CallMethod", "target": "stage", "method": "SetLoopingSfxVolume", "params": { "id":"sfxId", "volume":"patternTime < 4.75f ? map(patternTime, 1.5f, 1.75f, 0f, 1f, 'QuadOut') : map(patternTime, 4.75f, 5f, 1f, 0f)", }, },
      { "action": "CallMethod", "target": "stage", "method": "SetLoopingSfxPosition", "params": { "id":"sfxId", "pos":"projectPointOntoLine(playerPos, patternPos + patternDir * 10f, patternPos + patternDir * 500f)", }, },
    ],
    "onFinish":[
      { "action": "CallMethod", "target": "stage", "method": "StopLoopingSfx", "params": { "id":"sfxId", }, },
    ],
}
```

In this example, the ID of the looping sound is stored in a custom integer property of a pattern. You could also store it in the built-in `intVar` of bullets, for example.