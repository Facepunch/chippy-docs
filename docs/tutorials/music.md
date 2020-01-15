# Music

Chippy has a dynamic, layer-based music system. A song can be randomized so it's different each time, and can change certain elements based on the gameplay.

## Built-in Songs

To simply re-use one of the Chippy songs for your stage, use one of these song names for the `song` property in your level config json.

```json hl_lines="4"
{
  "title": "#intro.title",
  "description": "#intro.description",
  "song": "017",
  // ...
}
```

??? example "Stage song names"
    Stage | Resource Folder Name | Song Name
    :----------- |:-------------|:-------------
    Neophyte | `intro` | `017`
    Kraken | `octopus` | `019`
    Guardian | `mech` | `023`
    Execution | `fuse` | `025`
    Overgrowth | `trench` | `015`
    Anomaly | `onion` | `022`
    Phobia | `hunter` | `012`
    Medusa | `tentacle` | `020`
    Goliath | `claw` | `002`
    Hermit | `orb` | `021`
    Monarch | `frame` | `013`
    Prospector | `laser` | `024`
    Storm | `storm` | `010`
    Xulgon | `invasion` | `011`

!!! abstract "Download campaign songs"
    These are the song files used in the campaigns, for you to learn from or remix: [**campaign_songs.zip**](https://files.facepunch.com/ryleigh/200115-tgZam9/campaign_songs.zip)

## Custom Songs

### Example

Here's an example song:
[**music.zip**](https://files.facepunch.com/ryleigh/200115-tn3Hqc/music.zip)

To test it in your stage, unzip the `music` folder and place it somewhere in your plugin folder.<br />
In the stage config json file, enter the path to the song config file.

```json
"song": "myStageName/music/bouncy_song",
```

These are three different files included:

???+ info "bouncy_samples.mp3"
    This is an audio file with all our loops crammed into it. We could have used a separate audio file for each loop if we wanted, but then we'd need to create a sample config file for each.

    <img src="https://files.facepunch.com/ryleigh/200115-pY2ZNh/audacity_2020-01-15_00-19-22.png" />

    <audio controls>
      <source src="https://files.facepunch.com/ryleigh/200115-bPN3x2/bouncy_samples_2.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
    </audio>

??? abstract "bouncy_sample_config.json"
    This is the sample config file. It defines which parts of an audio file can be used as sampled loops in the song config.

    ```json
    {
      "filename": "bouncy_samples",
      "beatsPerMinute": 128,
      "beatsPerBar": 4,

      "samples": {
        "drum0": { "startBar": 0, "lengthBars": 2 },
        "drum1": { "startBar": 2, "lengthBars": 2 },
        "drum_fill": { "startBar": 4, "lengthBars": 2 },
        "bass0": { "startBar": 5, "lengthBars": 2 },
        "bass1": { "startBar": 7, "lengthBars": 2 },
        "synth0": { "startBar": 9, "lengthBars": 2 },
        "synth1": { "startBar": 11, "lengthBars": 2 },
        "piano0": { "startBar": 13, "lengthBars": 8 },
        "piano1": { "startBar": 21, "lengthBars": 4 },
        "vox": { "startBar": 25, "lengthBars": 2 },
      }
    }
    ```

??? abstract "bouncy_song.json"
    This is song config file. It uses samples defined in the sample config file and arranges them into layers, each layer playing up to one sample at a time.

    ```json
    {
      "beatsPerMinute": 128,
      "beatsPerBar": 4,

      "properties": {
        "drumsVolume": {
          "type": "Func<Float>",
          "value": "0.66f + sin(stageTime * 0.25) * 0.33f"
        },
        "drumsHighpass": {
          "type": "Func<Float>",
          "value": "sin(stageTime * 0.1) * 0.2f"
        },
        "bassVolume": {
          "type": "Func<Float>",
          "value": "0.7f + sin(stageTime * 0.33) * 0.3f"
        },
        "synthVolume": {
          "type": "Func<Float>",
          "value": "0.6f + sin(stageTime * 0.2) * 0.2f"
        },
        "voxVolume": {
          "type": "Func<Float>",
          "value": "0.9f + sin(stageTime * 0.66) * 0.1f"
        },
        "voxLowpass": {
          "type": "Func<Float>",
          "value": "fastSin(stageTime * 0.275) * 0.2f"
        },
        "voxHighpass": {
          "type": "Func<Float>",
          "value": "fastSin(stageTime * 0.325) * 0.2f"
        },
      },
      "layers": {
        "drums": {
          "volume": "drumsVolume",
          "segments": [
            { "name": "seg0", "lengthBars": "rand.Int(1, 16) * 2", "sample": "bouncy_sample_config.drum0", "next":"seg${rand.Int(0, 2)}", "volume":1, },
            { "name": "seg1", "lengthBars": "rand.Int(1, 3) * 1", "sample": "bouncy_sample_config.drum_fill", "next":"seg2", "volume":1, },
            { "name": "seg2", "lengthBars": "rand.Int(1, 16) * 2", "sample": "bouncy_sample_config.drum1", "next":"seg${rand.Int(2, 4)}", "volume":1, },
            { "name": "seg3", "lengthBars": "rand.Int(1, 3) * 1", "sample": "bouncy_sample_config.drum_fill", "next":"seg0", "volume":1, },
          ]
        },
        "bass": {
          "volume": "bassVolume",
          "segments": [
            { "name": "seg0", "lengthBars": "rand.Int(3, 6) * 2", "next":"seg1", },
            { "name": "seg1", "lengthBars": "rand.Int(1, 16) * 2", "sample": "bouncy_sample_config.bass0", "next":"seg${rand.Int(0, 3)}", "volume":1, },
            { "name": "seg2", "lengthBars": "rand.Int(1, 8) * 2", "sample": "bouncy_sample_config.bass1", "next":"seg0", "volume":1, },
          ]
        },
        "synth": {
          "volume": "synthVolume",
          "segments": [
            { "name": "part0", "lengthBars": "rand.Int(8, 12) * 2", }, // by not specifying "next", it will automatically go to the next segment
            { "name": "part1", "lengthBars": "rand.Int(1, 16) * 2", "sample": "bouncy_sample_config.synth0", "next":"part2", "volume":1, },
            { "name": "part2", "lengthBars": "rand.Int(1, 16) * 2", "sample": "bouncy_sample_config.synth1", "next":"part0", "volume":1, },
          ]
        },
        "piano": {
          "volume": "0.8f",
          "segments": [
            { "name": "seg0", "lengthBars": "rand.Int(14, 16) * 2", "next":"seg1", },
            { "name": "seg1", "lengthBars": "rand.Int(1, 6) * 8", "sample": "bouncy_sample_config.piano0", "next":"seg2", "volume":1, },
            { "name": "seg2", "lengthBars": "rand.Int(1, 4) * 4", "sample": "bouncy_sample_config.piano1", "next":"seg0", "volume":1, },
          ]
        },
        "vox": {
          "volume": "voxVolume",
          "highpass":"voxHighpass", // filter out low frequency sounds
          "lowpass":"voxLowpass", // filter out high frequency sounds
          "segments": [
            { "name": "seg0", "lengthBars": "rand.Int(4, 14) * 2", "next":"seg${rand.Int(0, 2)}", },
            { "name": "seg1", "lengthBars": "rand.Int(1, 16) * 2", "sample": "bouncy_sample_config.vox", "next":"seg${rand.Int(0, 2)}", "volume":1, },
          ]
        },
      }
    }
    ```    

    !!! tip
        This example only uses one sample config file, but you can create as many as you want. 

<br />
Here's the same song playing twice, and progressing slightly differently each time:
<br /> <br />
<audio controls>
  <source src="https://files.facepunch.com/ryleigh/200114-D7XCN8/song_0.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>

<audio controls>
  <source src="https://files.facepunch.com/ryleigh/200114-SQieHh/song_1.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>

### Workflow

#### Audio

Find some music loops that sound good together. They should probably all be the same bpm.

I used Ableton Live, but any DAW should work.

<img src="https://files.facepunch.com/ryleigh/200114-8sCRQY/Ableton_Live_10_Suite_2020-01-14_23-51-13.png" />

Lay out the clips so they play one after another, and export it to mp3.

<img src="https://files.facepunch.com/ryleigh/200115-eGWbAC/Ableton_Live_10_Suite_2020-01-15_01-05-08.png" />

#### Sample Config

Now that we have our audio file, it's time to specify which sections of it to use as samples.

```json
{
  // specify the name of the audio file. since it is in the same folder, no need to specify the full path
  "filename": "bouncy_samples",

  "beatsPerMinute": 128,
  "beatsPerBar": 4, 

  "samples": {
    "drum0": { "startBar": 0, "lengthBars": 2 }, // the first bar is 0, not 1
    "drum1": { "startBar": 2, "lengthBars": 2 },
    "drum_fill": { "startBar": 4, "lengthBars": 2 },
    "bass0": { "startBar": 5, "lengthBars": 2 },
    "bass1": { "startBar": 7, "lengthBars": 2 },
    "synth0": { "startBar": 9, "lengthBars": 2 },
    "synth1": { "startBar": 11, "lengthBars": 2 },
    "piano0": { "startBar": 13, "lengthBars": 8 },
    "piano1": { "startBar": 21, "lengthBars": 4 },
    "vox": { "startBar": 25, "lengthBars": 2 },
  }
}
```

To find the `lengthBars` value, count the number of bars each sample is comprised of:

<img src="https://files.facepunch.com/ryleigh/200115-DFcbHr/bars.png" />

Simply increment `startBar` by the `lengthBars` of each sample, but be sure to start with bar `0`, not `1`.

#### Song Config

We have our samples defined now, and can use them to create a song.

```json
{
  // pick whatever bpm your samples are in (this value can be dynamically changed in SOME ways, but it's pretty janky, and can't use custom song properties)
  "beatsPerMinute": 128,

  "beatsPerBar": 4,

  // define custom properties that the layers can refer to 
  "properties": {
    "bassVolume": {
      "type": "Func<Float>",
      "value": "0.7f + sin(stageTime * 0.33) * 0.3f"
    },
    // ...
  },

  // when the song starts, each layer will begin playing on its first segment
  "layers": {
    "bass": {
      "volume": "bassVolume", // using a custom property to control volume of this layer
      "segments": [
        // if there is no sample defined, this section will be silent
        { "name": "seg0", "lengthBars": "rand.Int(3, 6) * 2", "next":"seg1", },

        // after seg1, the next segment will randomly be selected from seg0, seg1, seg2
        { "name": "seg1", "lengthBars": "rand.Int(1, 16) * 2", "sample": "bouncy_sample_config.bass0", "next":"seg${rand.Int(0, 3)}", "volume":1, },

        { "name": "seg2", "lengthBars": "rand.Int(1, 8) * 2", "sample": "bouncy_sample_config.bass1", "next":"seg0", "volume":1, },
      ]
    },
    // ...
  }
}
```  

## Custom Property Examples

Here are some examples of ways to influence the song with the current gameplay state.

```json
{
  "properties": {
    // true if the boss form number is 0 (BossFormNumber is shorthand for stage.GetUnit('boss').CurrFormNum)
    "firstForm": {
      "type": "Func<Bool>",
      "value": "stage.BossFormNumber == 0"
    },
    "secondForm": {
      "type": "Func<Bool>",
      "value": "stage.GetUnit('boss').CurrFormNum == 1"
    },
    // the volume of the hats is based on whether the player is shooting or not (we must check if we're on the menu, because no player exists on the menu stage)
    "hatsVolume": {
      "type": "Func<Float>",
      "value": "isMenuStage ? 0f : player.Input.ShootInputPercent * 0.25f"
    },
  },
}
```

## Segment Actions

Each segment of a layer can define actions to trigger when it starts. In the campaign songs, this is used to control which sections are playing.

```json
{
  "properties": {
    // this property will be changed with an action
    "shouldPlayMelody": {
      "type": "Bool",
      "value": true
    },
  },
  "layers": {
    "section-control": {
      "volume": 0,
      "segments": [
        { "name": "intro", "next": "melody", "lengthBars": 8, 
          "actions": [
            { "action": "SetValue", "name": "shouldPlayMelody", "value": false },
          ] 
        },
        { "name": "melody", "next": "intro", "lengthBars": 8, 
          "actions": [
            { "action": "SetValue", "name": "shouldPlayMelody", "value": true },
          ] 
        },
      ],
    },
    "melody": {
      // the volume of this layer depends on the bool value modified by the action
      "volume": "shouldPlayMelody ? 1 : 0",
      "segments":[
        // ...
      ],
    },
  },
}
```
