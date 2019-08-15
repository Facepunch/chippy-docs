# BulletKeyframeData Resource

<small>**Namespace**: SpaceUsurper</small>

Describes the properties a bullet should have for a certain period of time, in sequence.

<small>**Inheritance**: [Object](https://docs.microsoft.com/en-us/dotnet/api/system.object?view=netframework-4.5) → [HotloadedData](HotloadedData.md) → BulletKeyframeData</small>

!!! note
    This resource type supports `#includes`, so it can inherit properties
    from other resources of the same type.
## Properties

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [`#include`](HotloadedData-1/Include.md) | <small>(Inherited from [HotloadedData](HotloadedData-1.md)&lt;[BulletKeyframeData](BulletKeyframeData.md)&gt;)</small> | 
| [`acceleration`](BulletKeyframeData/acceleration.md) |  | 
| [`cantBeAffected`](BulletKeyframeData/cantBeAffected.md) | If true, not affected by RepelBullets / DestroyBullets / TransformBullets / AffectBulletsInRadius / GetBulletsInRadius / AddForceToBullets. | 
| [`chance`](BulletKeyframeData/chance.md) | Chance of using keyframe, from 0 to 1. | 
| [`colorA1`](BulletKeyframeData/colorA1.md) |  | 
| [`colorA2`](BulletKeyframeData/colorA2.md) |  | 
| [`colorB1`](BulletKeyframeData/colorB1.md) |  | 
| [`colorB2`](BulletKeyframeData/colorB2.md) |  | 
| [`colorBlinkTime`](BulletKeyframeData/colorBlinkTime.md) | Time it takes to lerp between color1 and color2. | 
| [`colorC1`](BulletKeyframeData/colorC1.md) |  | 
| [`colorC2`](BulletKeyframeData/colorC2.md) |  | 
| [`crossDistance`](BulletKeyframeData/crossDistance.md) |  | 
| [`crossWidth`](BulletKeyframeData/crossWidth.md) |  | 
| [`duration`](BulletKeyframeData/duration.md) |  | 
| [`easingType`](BulletKeyframeData/easingType.md) | The easing type used when easing into the next keyframe. | 
| [`facingMode`](BulletKeyframeData/facingMode.md) |  | 
| [`facingSpeedPercent`](BulletKeyframeData/facingSpeedPercent.md) |  | 
| [`frictionPercent`](BulletKeyframeData/frictionPercent.md) |  | 
| [`glowA`](BulletKeyframeData/glowA.md) |  | 
| [`glowB`](BulletKeyframeData/glowB.md) |  | 
| [`glowC`](BulletKeyframeData/glowC.md) |  | 
| [`ignorePixelCollision`](BulletKeyframeData/ignorePixelCollision.md) | Use when a bullet should start on a pxc without colliding with it until later. | 
| [`ignorePlayerCollision`](BulletKeyframeData/ignorePlayerCollision.md) | Only applies to this keyframe, unlike the general version of this func which means the bullet can never hit the player. | 
| [`isPositive`](BulletKeyframeData/isPositive.md) | Whether the player would generally want to collide with the bullet on this keyframe. | 
| [`length`](BulletKeyframeData/length.md) |  | 
| [`loopEnd`](BulletKeyframeData/loopEnd.md) | Keyframe will be ignored if we are on or past loop number N (non-inclusive). | 
| [`loopModulus`](BulletKeyframeData/loopModulus.md) | Keyframe active every N loops. | 
| [`loopStart`](BulletKeyframeData/loopStart.md) | Keyframe will be ignored until we are on loop number N or greater. | 
| [`moveAngle`](BulletKeyframeData/moveAngle.md) | Relative to the starting direction (unless useAbsoluteAngles is true). | 
| [`moveMode`](BulletKeyframeData/moveMode.md) |  | 
| [`next`](BulletKeyframeData/next.md) | If this returns a valid frame, goto that frame instead of the next-in-sequence keyframe. | 
| [`opacity`](BulletKeyframeData/opacity.md) | Modifier value for the colors' opacities. | 
| [`pixelDamagePercent`](BulletKeyframeData/pixelDamagePercent.md) | The percent of max damage the bullet has available this keyframe. | 
| [`posLerpSpeed`](BulletKeyframeData/posLerpSpeed.md) |  | 
| [`proximityEnabled`](BulletKeyframeData/proximityEnabled.md) | Whether the bullet should check proximity to target units on this keyframe (true by default). | 
| [`radius`](BulletKeyframeData/radius.md) |  | 
| [`rectSize`](BulletKeyframeData/rectSize.md) |  | 
| [`rectWidthMods`](BulletKeyframeData/rectWidthMods.md) |  | 
| [`rotationSpeed`](BulletKeyframeData/rotationSpeed.md) |  | 
| [`sprite`](BulletKeyframeData/SpritePath.md) |  | 
| [`spriteIndex`](BulletKeyframeData/SpriteIndex.md) |  | 
| [`sprites`](BulletKeyframeData/SpritePaths.md) |  | 
| [`targetFacingAngle`](BulletKeyframeData/targetFacingAngle.md) |  | 
| [`targetPos`](BulletKeyframeData/targetPos.md) | If moveMode is Target, lerp to this position instead of using velocity. | 
| [`velocityMode`](BulletKeyframeData/velocityMode.md) |  | 

</div>

## Handlers

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [`onKeyframe`](BulletKeyframeData/OnKeyframe.md) | Actions to run at the start of this keyframe. | 

</div>

