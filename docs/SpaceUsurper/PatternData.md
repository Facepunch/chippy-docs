# PatternData Resource

<small>**Namespace**: SpaceUsurper</small>

<small>**Inheritance**: [Object](https://docs.microsoft.com/en-us/dotnet/api/system.object?view=netframework-4.5) → [HotloadedData](HotloadedData.md) → PatternData</small>

!!! note
    This resource type supports `#includes`, so it can inherit properties
    from other resources of the same type.
## Properties

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [`#include`](HotloadedData-1/Include.md) | <small>(Inherited from [HotloadedData](HotloadedData-1.md)&lt;[PatternData](PatternData.md)&gt;)</small> | 
| [`advanceImmediately`](PatternData/advanceImmediately.md) | If true, update the bullet pattern immediately (shoot first volley, so subsequent actions can affect its bullets). | 
| [`aimMode`](PatternData/aimMode.md) |  | 
| [`aimSpeed`](PatternData/aimSpeed.md) |  | 
| [`angleOffset`](PatternData/angleOffset.md) | Amount of degrees to offset current bullet's angle. | 
| [`arcAngle`](PatternData/arcAngle.md) | What angle to spread spokes over (when 0 or 360, use the whole circle). | 
| [`arcEasingType`](PatternData/arcEasingType.md) | How the bullets in an arc are laid out. | 
| [`behaviour`](PatternData/Behaviour.md) |  | 
| [`bulletIndex`](PatternData/bulletIndex.md) | Decides which bullet is used for a given shot. | 
| [`bullets`](PatternData/bullets.md) | The paths of the different bullets used in the pattern. | 
| [`bulletSizeMultiplier`](PatternData/bulletSizeMultiplier.md) | Amount to scale each bullet's size by. | 
| [`chargeColor`](PatternData/chargeColor.md) |  | 
| [`chargeColorEasingType`](PatternData/chargeColorEasingType.md) |  | 
| [`chargeLookLerpPercent`](PatternData/chargeLookLerpPercent.md) | How quickly the pattern's anchor core looks in the aim direction while charging. | 
| [`chargeLookPercent`](PatternData/chargeLookPercent.md) | How far the pattern's anchor core looks in the aim direction while charging. | 
| [`constantRotation`](PatternData/constantRotation.md) | If true, handle rotation every update, instead of only when firing a volley. | 
| [`customBulletAngle`](PatternData/customBulletAngle.md) | The angle of a given bullet in an custom pattern. | 
| [`customBulletPos`](PatternData/customBulletPos.md) | The position of a given bullet in an custom pattern. | 
| [`customPatternPos`](PatternData/customPatternPos.md) | The position of the pattern for the current volley, for a custom pattern. | 
| [`debugText`](PatternData/debugText.md) |  | 
| [`debugVector`](PatternData/debugVector.md) |  | 
| [`despawnChildBulletsWhenFinished`](PatternData/despawnChildBulletsWhenFinished.md) | If true, remove all bullets we've fired when we finish for any reason. | 
| [`despawnWhenAnchorInactive`](PatternData/despawnWhenAnchorInactive.md) | If true, remove pattern if the anchor doesn't exist any longer (defaults to true). | 
| [`dragBullets`](PatternData/dragBullets.md) | Whether bullets of this pattern move with the pattern itself in addition to their own movement. | 
| [`fanAngle`](PatternData/fanAngle.md) | Degrees between each bullet, only used for fan pattern shape. | 
| [`fanSubdivide`](PatternData/fanSubdivide.md) | Number of fan bullets each 'spoke' should have. | 
| [`hitSelfPixels`](PatternData/hitSelfPixels.md) | If true, bullets in this pattern can collide with the same pxc that spawned it. | 
| [`ignoreCollision`](PatternData/ignoreCollision.md) | Units that this pattern should ignore collision with. | 
| [`impulseVelocity`](PatternData/impulseVelocity.md) | Amount to add to bullet's starting impulse velocity. | 
| [`inheritAnchorAngle`](PatternData/inheritAnchorAngle.md) | Whether this pattern's angle is set to anchor angle, when attached. | 
| [`kickbackLerpPercent`](PatternData/kickbackLerpPercent.md) | How fast the kickback lerps. | 
| [`kickbackPercent`](PatternData/kickbackPercent.md) | How far in the reverse direction the shootLookPercent is adjusted each volley. | 
| [`kickbackTime`](PatternData/kickbackTime.md) | How long the kickback lasts for. | 
| [`linkVolleyBullets`](PatternData/linkVolleyBullets.md) | If true, all bullets in a volley will despawn if any of them despawn. | 
| [`maxVibrationDist`](PatternData/maxVibrationDist.md) |  | 
| [`name`](PatternData/name.md) |  | 
| [`numBulletsInVolley`](PatternData/numBulletsInVolley.md) |  | 
| [`numVolleys`](PatternData/numVolleys.md) | The number of volleys to shoot before finishing. If 0, don't stop until the parent tells it to. | 
| [`numVolleysPerShootSfx`](PatternData/numVolleysPerShootSfx.md) | How many volleys have to happen before playing each shoot sfx. | 
| [`parallelForce`](PatternData/parallelForce.md) | Sideways force to spread out bullets that head in the same direction, only used for parallel pattern shape. | 
| [`parallelSubdivide`](PatternData/parallelSubdivide.md) | Number of parallel bullets each 'spoke' should have. | 
| [`patternShape`](PatternData/patternShape.md) | Spokes: spread bullets out along the arc angle (default = full circle), Custom: specify the position and angle of each bullet. | 
| [`positionOffset`](PatternData/positionOffset.md) | Amount to offset current bullet's position. | 
| [`properties`](PatternData/Properties.md) |  | 
| [`recoil`](PatternData/recoil.md) | Force that's applied to the player/unit for each volley. Only applies when Player.AddPattern is called, not for patterns fired from player guns. "shoot_force" physics element must be defined. | 
| [`rotateBulletAngles`](PatternData/rotateBulletAngles.md) | If false, only rotates the position of anchored bullets, not their orientation. | 
| [`rotateBullets`](PatternData/rotateBullets.md) | Whether the rotation of this pattern modifies the position of child bullets. | 
| [`rotateWithAnchor`](PatternData/rotateWithAnchor.md) | Whether rotation applied to the anchor affects this pattern's rotation. | 
| [`rotationSpeed`](PatternData/rotationSpeed.md) |  | 
| [`sfxCharge`](PatternData/sfxCharge.md) |  | 
| [`sfxFinish`](PatternData/sfxFinish.md) |  | 
| [`sfxStart`](PatternData/sfxStart.md) |  | 
| [`sfxVolley`](PatternData/sfxVolley.md) |  | 
| [`sfxVolleyPitchFactor`](PatternData/sfxVolleyPitchFactor.md) |  | 
| [`sfxVolleyVoiceLimit`](PatternData/sfxVolleyVoiceLimit.md) |  | 
| [`sfxVolleyVolumeFactor`](PatternData/sfxVolleyVolumeFactor.md) |  | 
| [`shootColor`](PatternData/shootColor.md) |  | 
| [`shootColorEasingType`](PatternData/shootColorEasingType.md) |  | 
| [`shootColorPercent`](PatternData/shootColorPercent.md) |  | 
| [`shootColorTime`](PatternData/shootColorTime.md) |  | 
| [`shootDelay`](PatternData/shootDelay.md) | The amount of time each volley (after the first) will be delayed from the previous volley. | 
| [`shootEffectPattern`](PatternData/shootEffectPattern.md) | The bulletpattern that is fired whenever a volley is shot. | 
| [`shootFinishLookTime`](PatternData/shootFinishLookTime.md) | How long to stay looking in the aim direction after shooting all volleys. | 
| [`shootLookLerpPercent`](PatternData/shootLookLerpPercent.md) | How quickly the pattern's anchor core looks in the aim direction each volley. | 
| [`shootLookPercent`](PatternData/shootLookPercent.md) | How far the pattern's anchor core looks in the aim direction each volley. | 
| [`shootTime`](PatternData/shootTime.md) | How long each shot volley affects the core. | 
| [`shouldOverrideStatusEffect`](PatternData/shouldOverrideStatusEffect.md) | Decides if the current bullet should be overridden with a status effect. | 
| [`shouldShoot`](PatternData/shouldShoot.md) | Whether the current bullet that will be shot, should actually be shot or not (defaults to true). | 
| [`startAngle`](PatternData/startAngle.md) | If set, overrides default or target starting angle. | 
| [`startDelay`](PatternData/startDelay.md) | The amount of time the first volley will be delayed. | 
| [`statusPaths`](PatternData/statusPaths.md) | The status effects that can be used to override. | 
| [`targetAimAngle`](PatternData/targetAimAngle.md) |  | 
| [`torque`](PatternData/torque.md) | Rotation force applied to units. | 
| [`useRawDeltaTime`](PatternData/useRawDeltaTime.md) | Ignore time-scaling. | 
| [`velocity`](PatternData/velocity.md) | Amount to add to bullet's starting velocity. | 
| [`vibrationEasingType`](PatternData/vibrationEasingType.md) |  | 
| [`vibrationHorizThreshold`](PatternData/vibrationHorizThreshold.md) |  | 
| [`vibrationStrength`](PatternData/vibrationStrength.md) | Amount to vibrate at position of pattern, each volley. | 
| [`vibrationTime`](PatternData/vibrationTime.md) |  | 
| [`waitForBulletsToDespawn`](PatternData/waitForBulletsToDespawn.md) | If true, wait for all fired bullets to despawn before removing pattern, else only wait until all have been fired. | 

</div>

## Handlers

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [`onBullet`](PatternData/OnBullet.md) |  | 
| [`onFinish`](PatternData/OnFinish.md) |  | 
| [`onStart`](PatternData/OnStart.md) |  | 
| [`onUpdate`](PatternData/OnUpdate.md) |  | 
| [`onVolley`](PatternData/OnVolley.md) |  | 

</div>

