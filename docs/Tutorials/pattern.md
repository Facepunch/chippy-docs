# Bullet Patterns

A bullet pattern contains a number of "volleys", each of which shoot a number of bullets from a certain position and angle.

## A Simple Pattern

```json hl_lines="3"
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
`patternTime` simply tracks how long this pattern has been running for. The 'f's after the numbers denote them as floating-point numbers instead of integers, since `rotationSpeed` is itself a float, but don't worry about it too much.

### Aiming

By default, patterns simply rotate according to their `rotationSpeed` property, but we can instead set a target angle:
```json
{
	...
	"aimMode":"Target",
	"targetAimAngle":"vecToAngle(playerPos - patternPos)",
	"aimSpeed":0.1,
	"arcAngle":90,
	...
}
```
Setting `"aimMode":"Target"` means the pattern will ignore `rotationSpeed` and ease toward `targetAimAngle` instead. In this case the pattern wants to aim directly at the player's position. 

The `aimSpeed` is a value from 0-1. With a value of `0.1` it will ease 10% of the way to the target each frame, so it will lag behind a bit.

<video controls> <source src="https://files.facepunch.com/ryleigh/1b0711b1/2019-08-07_16-09-42.mp4" type="video/mp4"> </video>

With `"arcAngle":90` we changed the angle that all the bullets are distributed between from 360° to 90°.

<img src="https://files.facepunch.com/ryleigh/1b0611b1/Photo_2019-08-06_8_14_23_PM.jpg" width="300"/>

## Spawning a Pattern

## Visual Effects

## Debugging Patterns

