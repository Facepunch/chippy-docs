# BulletData Resource

<small>**Namespace**: SpaceUsurper</small>

<small>**Inheritance**: [Object](https://docs.microsoft.com/en-us/dotnet/api/system.object?view=netframework-4.5) → [HotloadedData](HotloadedData.md) → BulletData</small>

!!! note
    This resource type supports `#includes`, so it can inherit properties
    from other resources of the same type.
## Properties

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [`#include`](HotloadedData-1/Include.md) | <small>(Inherited from [HotloadedData](HotloadedData-1.md)&lt;[BulletData](BulletData.md)&gt;)</small> | 
| [`anchored`](BulletData/anchored.md) | Set this to true if something else moves this bullet (eg. parent pattern). | 
| [`borderWarningColor`](BulletData/borderWarningColor.md) | The color of the bullet when just out of camera bounds (uses current colorA when not set). | 
| [`borderWarningGlow`](BulletData/borderWarningGlow.md) | How much the bullet glows when just out of camera bounds. | 
| [`borderWarningMinOpacity`](BulletData/borderWarningMinOpacity.md) | How opaque the edges of the border warning are. | 
| [`bounds`](BulletData/Bounds.md) |  | 
| [`cantBeDestroyed`](BulletData/cantBeDestroyed.md) |  | 
| [`circleSkew`](BulletData/circleSkew.md) | Amount of skew (stretching in forward direction) when bullet traveling at max skew speed. | 
| [`circleSkewDist`](BulletData/circleSkewDist.md) | Distance (per fixed frame) required for full skew. | 
| [`circleSkewEasingType`](BulletData/circleSkewEasingType.md) |  | 
| [`collideInAllDirections`](BulletData/collideInAllDirections.md) | If true, bullet rotates the direction it checks for collisions with pixels, and doesn't resolve visual overlaps (defaults to false). Used for turrets/drones/etc. | 
| [`collideWithPixels`](BulletData/collideWithPixels.md) |  | 
| [`colorA1`](BulletData/colorA1.md) |  | 
| [`colorA2`](BulletData/colorA2.md) |  | 
| [`colorB1`](BulletData/colorB1.md) |  | 
| [`colorB2`](BulletData/colorB2.md) |  | 
| [`colorBlinkEasingType`](BulletData/colorBlinkEasingType.md) |  | 
| [`colorBlinkStartTime`](BulletData/colorBlinkStartTime.md) | So that bullets in the same volley can have different color timing offsets. | 
| [`colorC1`](BulletData/colorC1.md) |  | 
| [`colorC2`](BulletData/colorC2.md) |  | 
| [`debugText`](BulletData/debugText.md) |  | 
| [`debugVector`](BulletData/debugVector.md) |  | 
| [`depthLevel`](BulletData/depthLevel.md) |  | 
| [`despawnAfterKeyframes`](BulletData/despawnAfterKeyframes.md) | If true, bullet despawns as soon as it runs out of keyframes, regardless of its lifetime. | 
| [`despawnOnPlayerHit`](BulletData/despawnOnPlayerHit.md) | Defaults to true. | 
| [`despawnStyle`](BulletData/despawnStyle.md) |  | 
| [`despawnTime`](BulletData/despawnTime.md) |  | 
| [`despawnWhenAllPatternsRemoved`](BulletData/despawnWhenAllPatternsRemoved.md) | Defaults to false. | 
| [`dontCheckBounds`](BulletData/dontCheckBounds.md) | If true, don't disable this bullet based on being outside of arena. | 
| [`extraFrameSize`](BulletData/extraFrameSize.md) | Number of extra spritesheet frames to use instead - (N+1)x(N+1) instead of 1x1. | 
| [`flipX`](BulletData/flipX.md) |  | 
| [`flipY`](BulletData/flipY.md) |  | 
| [`force`](BulletData/force.md) | How much force it applies to pxcs it hits (also affected by pixelDamagePercent). | 
| [`grazeSize`](BulletData/grazeSize.md) |  | 
| [`ignorePlayerCollision`](BulletData/ignorePlayerCollision.md) | Don't EVER collide with player - for when using bullet as visual effect, or when shot by player. | 
| [`impactPattern`](BulletData/impactPattern.md) |  | 
| [`impulseFrictionPercent`](BulletData/impulseFrictionPercent.md) | How quickly the bullet slows down impulse velocity (default is 0.05). | 
| [`isPlayerBullet`](BulletData/isPlayerBullet.md) | Whether the bullet should be considered to be shot by the player. | 
| [`isStrictlyVisual`](BulletData/isStrictlyVisual.md) | Can never be Affected, Repelled, Destroyed, etc. Use for background bullets or other visual effects. | 
| [`keyframes`](BulletData/keyframes.md) |  | 
| [`lifetime`](BulletData/lifetime.md) |  | 
| [`mass`](BulletData/mass.md) | How well the bullet resists being repelled (if unset, it defaults to 1). | 
| [`noCollisionLeniency`](BulletData/noCollisionLeniency.md) | For small bullets, don't have a smaller hitbox than visuals when colliding with player. | 
| [`outOfBoundsRadiusFactor`](BulletData/outOfBoundsRadiusFactor.md) | How far off camera until this bullet is removed (multiplied by out radius) (defaults to 4f). (also used for border warning range) | 
| [`parallaxSpeed`](BulletData/parallaxSpeed.md) |  | 
| [`partDamageFactor`](BulletData/partDamageFactor.md) | Damage multiplier when hitting a part instead of a single pixel (default is 1). | 
| [`proximityRange`](BulletData/proximityRange.md) |  | 
| [`proximityUnits`](BulletData/proximityUnits.md) |  | 
| [`pushStrength`](BulletData/pushStrength.md) |  | 
| [`quickReflect`](BulletData/quickReflect.md) | Reflect instantly instead of animating. | 
| [`reflectLimit`](BulletData/reflectLimit.md) | Number of times bullet can reflect before despawning automatically. | 
| [`sfxHitPixel`](BulletData/sfxHitPixel.md) |  | 
| [`sfxHitPlayer`](BulletData/sfxHitPlayer.md) |  | 
| [`shapeType`](BulletData/shapeType.md) |  | 
| [`shouldLoop`](BulletData/shouldLoop.md) |  | 
| [`shouldOverrideStatusEffect`](BulletData/shouldOverrideStatusEffect.md) | Decides if the current bullet should be overridden with a status effect. | 
| [`shouldReflect`](BulletData/shouldReflect.md) | If bullet should reflect when hitting a pixel. | 
| [`spriteForwardOffset`](BulletData/spriteForwardOffset.md) | Amount the sprite is adjusted in forward direction. | 
| [`spriteScale`](BulletData/spriteScale.md) | Extra scale for sprite. | 
| [`startFacingAngle`](BulletData/startFacingAngle.md) | Start with this rotation instead of facing the current direction. | 
| [`startMoveAngle`](BulletData/startMoveAngle.md) | Start with this move angle instead of moving in the pattern's current direction. | 
| [`startSpeed`](BulletData/startSpeed.md) |  | 
| [`statusCycleTime`](BulletData/statusCycleTime.md) | If this bullet has overridden statuses, this is the time to cycle between them. | 
| [`statusLevel`](BulletData/statusLevel.md) | The amount of status levels to add. | 
| [`statusPaths`](BulletData/statusPaths.md) | The status effects that can be used to override. | 
| [`stopPatternsOnDespawn`](BulletData/stopPatternsOnDespawn.md) | Whether anchored patterns stop when the bullet is finished. | 
| [`totalPixelDamage`](BulletData/totalPixelDamage.md) | The max amount of damage this bullet can deal. | 
| [`useAbsoluteAngles`](BulletData/useAbsoluteAngles.md) | If true, don't add startAngle to keyframe angles. | 
| [`useRawDeltaTime`](BulletData/useRawDeltaTime.md) | Ignore time-scaling. | 

</div>

## Handlers

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [`onDestroyPixel`](BulletData/OnDestroyPixel.md) |  | 
| [`onHitPart`](BulletData/OnHitPart.md) |  | 
| [`onHitPartProtected`](BulletData/OnHitPartProtected.md) |  | 
| [`onHitPixel`](BulletData/OnHitPixel.md) |  | 
| [`onHitPlayer`](BulletData/OnHitPlayer.md) |  | 
| [`onLifetimeFinished`](BulletData/OnLifetimeFinished.md) |  | 
| [`onOutOfBounds`](BulletData/OnOutOfBounds.md) |  | 
| [`onProximity`](BulletData/OnProximity.md) |  | 
| [`onRemove`](BulletData/OnRemove.md) |  | 
| [`onStart`](BulletData/OnStart.md) |  | 
| [`onUpdate`](BulletData/OnFixedUpdate.md) |  | 

</div>

