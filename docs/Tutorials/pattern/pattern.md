# Bullet Patterns

A bullet pattern contains a number of "volleys", each of which shoot a number of bullets from a certain position and angle.

## A Simple Pattern

```
"simpleAttack": {
  "numVolleys": 15,
  "numBulletsInVolley":5,
  "shootDelay": 0.1,
  "rotationSpeed":-150,
  "sfxVolley": "OctopusSmallSpewShoot",
  "bullets": [".bullet"],
},
```

This pattern will shoot `15` times, with `5` bullets each.
By default, the bullets in each volley will be spread evenly around a full 360° circle.

After the initial volley, there will be a `0.1` second delay until the next.

The pattern will rotate with a speed of `150` units, clockwise (negative is clockwise, positive is counterclockwise).

`bullets` defines what this pattern can shoot - since only one is referenced, every bullet in the pattern will be the same. The path can be absolute, but usually it's easiest to reference definitions in the same json object - in this case, `.bullet` refers to the bullet defined at the same level as the `simpleAttack` pattern definition.


## Creating a Pattern
