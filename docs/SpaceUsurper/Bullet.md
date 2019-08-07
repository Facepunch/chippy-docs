# Bullet Class

<small>**Namespace**: SpaceUsurper</small>

A projectile produced by a [BulletPattern](BulletPattern.md), which
can optionally collide with a [Player](Player.md) or
a [Unit](Unit.md).

<small>**Inheritance**: [Object](https://docs.microsoft.com/en-us/dotnet/api/system.object?view=netframework-4.5) → Bullet</small>

## Properties

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [BulletNum](Bullet/BulletNum.md) |  | 
| [CantBeAffected](Bullet/CantBeAffected.md) |  | 
| [CantBeDestroyed](Bullet/CantBeDestroyed.md) |  | 
| [ChildBullet](Bullet/ChildBullet.md) |  | 
| [CollideWithPixels](Bullet/CollideWithPixels.md) |  | 
| [CollideWithPlayer](Bullet/CollideWithPlayer.md) |  | 
| [CurrDamageAvailable](Bullet/CurrDamageAvailable.md) |  | 
| [CurrForceStrength](Bullet/CurrForceStrength.md) |  | 
| [DataPath](Bullet/DataPath.md) |  | 
| [ElapsedFrameTime](Bullet/ElapsedFrameTime.md) |  | 
| [ElapsedLifetime](Bullet/ElapsedLifetime.md) |  | 
| [FacingAngle](Bullet/FacingAngle.md) |  | 
| [FacingDirection](Bullet/FacingDirection.md) |  | 
| [FloatVar](Bullet/FloatVar.md) |  | 
| [HasParentPattern](Bullet/HasParentPattern.md) |  | 
| [ImpulseVelocity](Bullet/ImpulseVelocity.md) |  | 
| [IntVar](Bullet/IntVar.md) |  | 
| [IsActive](Bullet/IsActive.md) |  | 
| [IsAnchored](Bullet/IsAnchored.md) |  | 
| [IsFinishedAdvancingKeyframes](Bullet/IsFinishedAdvancingKeyframes.md) |  | 
| [IsPlayerBullet](Bullet/IsPlayerBullet.md) |  | 
| [IsPositive](Bullet/IsPositive.md) |  | 
| [IsRedirected](Bullet/IsRedirected.md) |  | 
| [IsStatusVisualBullet](Bullet/IsStatusVisualBullet.md) |  | 
| [LastPos](Bullet/LastPos.md) |  | 
| [Level](Bullet/Level.md) |  | 
| [LoopNum](Bullet/LoopNum.md) |  | 
| [Mass](Bullet/Mass.md) |  | 
| [MoveMode](Bullet/MoveMode.md) |  | 
| [NumBullets](Bullet/NumBullets.md) |  | 
| [NumShotPatternsConstant](Bullet/NumShotPatternsConstant.md) |  | 
| [ParentBullet](Bullet/ParentBullet.md) |  | 
| [PatternNum](Bullet/PatternNum.md) |  | 
| [PlayerCollideable](Bullet/PlayerCollideable.md) |  | 
| [PosA](Bullet/PosA.md) |  | 
| [PosB](Bullet/PosB.md) |  | 
| [Position](Bullet/Position.md) | Current position of the bullet. | 
| [PxcCollideable](Bullet/PxcCollideable.md) |  | 
| [PxcDamageDealt](Bullet/PxcDamageDealt.md) |  | 
| [Radius](Bullet/Radius.md) |  | 
| [ShouldOverrideStatus](Bullet/ShouldOverrideStatus.md) |  | 
| [SpawnPos](Bullet/SpawnPos.md) |  | 
| [StartTime](Bullet/StartTime.md) |  | 
| [StatusLevel](Bullet/StatusLevel.md) |  | 
| [TimeScale](Bullet/TimeScale.md) |  | 
| [TotalLifetime](Bullet/TotalLifetime.md) |  | 
| [TotalPxcDamage](Bullet/TotalPxcDamage.md) |  | 
| [VectorVar](Bullet/VectorVar.md) |  | 
| [Velocity](Bullet/Velocity.md) |  | 

</div>

## Methods

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [AddBullet(DataPath&lt;[BulletData](BulletData.md)&gt;, Vector2, float, float)](Bullet/AddBullet.md) |  | 
| [AddForce(Vector2)](Bullet/AddForce.md) |  | 
| [AddImpulseVelocity(Vector2)](Bullet/AddImpulseVelocity.md) |  | 
| [AddPattern(DataPath&lt;[PatternData](PatternData.md)&gt;, float, MirrorMode, float)](Bullet/AddPattern.md) |  | 
| [AddText(String, Vector2, Color, Color, Color, Vector2, FloatingTextFont, String, float, float, float, float, BulletTextAlignment, bool, float)](Bullet/AddText.md) |  | 
| [AddTimeScale(float, float, EasingType)](Bullet/AddTimeScale.md) |  | 
| [AddVelocity(Vector2)](Bullet/AddVelocity.md) |  | 
| [AffectTouchingBullets(ActionList, bool, ParameterCollection, bool)](Bullet/AffectTouchingBullets.md) |  | 
| [AffectTouchingUnits(ActionList, bool, ParameterCollection)](Bullet/AffectTouchingUnits.md) |  | 
| [ClearRedirect()](Bullet/ClearRedirect.md) |  | 
| [CreateBulletImpactEffect(Vector2, Vector2, float)](Bullet/CreateBulletImpactEffect.md) |  | 
| [DamagePlayer()](Bullet/DamagePlayer.md) |  | 
| [Despawn()](Bullet/Despawn.md) |  | 
| [DespawnText(Vector2, float, EasingType)](Bullet/DespawnText.md) |  | 
| [Flash(Color, float, EasingType, float, float, bool)](Bullet/Flash.md) |  | 
| [GetTextSize()](Bullet/GetTextSize.md) |  | 
| [GetVolleyBullet(int)](Bullet/GetVolleyBullet.md) |  | 
| [HitPlayer()](Bullet/HitPlayer.md) |  | 
| [Impact(Vector2, Vector2)](Bullet/Impact.md) |  | 
| [IsTouchingPlayer()](Bullet/IsTouchingPlayer.md) |  | 
| [OverrideColorBlinkTime(float)](Bullet/OverrideColorBlinkTime.md) |  | 
| [OverrideColors(Color, Color, Color, Color, Color, Color)](Bullet/OverrideColors.md) |  | 
| [OverrideColors(Color, Color, Color)](Bullet/OverrideColors.md) |  | 
| [Redirect(Vector2)](Bullet/Redirect.md) |  | 
| [Reflect(Unit, Vector2, Vector2, bool)](Bullet/Reflect.md) |  | 
| [SetBounds(Rect)](Bullet/SetBounds.md) |  | 
| [SetDespawnStyle(DespawnStyle)](Bullet/SetDespawnStyle.md) |  | 
| [SetDespawnTime(float)](Bullet/SetDespawnTime.md) |  | 
| [SetFacingAngle(float)](Bullet/SetFacingAngle.md) |  | 
| [SetFacingDirection(Vector2)](Bullet/SetFacingDirection.md) |  | 
| [SetFloatVar(float)](Bullet/SetFloatVar.md) |  | 
| [SetImpulseVelocity(Vector2)](Bullet/SetImpulseVelocity.md) |  | 
| [SetIntVar(int)](Bullet/SetIntVar.md) |  | 
| [SetKeyframe(int)](Bullet/SetKeyframe.md) | Sets the bullet keyframe immediately. | 
| [SetKeyframe_Legacy(int)](Bullet/SetKeyframe_Legacy.md) |  | 
| [SetPosB(Vector2)](Bullet/SetPosB.md) |  | 
| [SetPosition(Vector2)](Bullet/SetPosition.md) |  | 
| [SetStatusLevel(int)](Bullet/SetStatusLevel.md) |  | 
| [SetTextCharacterSpacing(float)](Bullet/SetTextCharacterSpacing.md) |  | 
| [SetTextColor(Color)](Bullet/SetTextColor.md) |  | 
| [SetTextColorA(Color)](Bullet/SetTextColorA.md) |  | 
| [SetTextColorB(Color)](Bullet/SetTextColorB.md) |  | 
| [SetTextColorBlinkTime(float)](Bullet/SetTextColorBlinkTime.md) |  | 
| [SetTextLerpSpeed(float)](Bullet/SetTextLerpSpeed.md) |  | 
| [SetTextLineSpacing(float)](Bullet/SetTextLineSpacing.md) |  | 
| [SetTextMessage(String)](Bullet/SetTextMessage.md) |  | 
| [SetTextNumChars(int)](Bullet/SetTextNumChars.md) |  | 
| [SetTextOffset(Vector2)](Bullet/SetTextOffset.md) |  | 
| [SetTextOpacity(float)](Bullet/SetTextOpacity.md) |  | 
| [SetTextOutlineColor(Color)](Bullet/SetTextOutlineColor.md) |  | 
| [SetTextOutlineWidth(float)](Bullet/SetTextOutlineWidth.md) |  | 
| [SetTextScale(Vector2)](Bullet/SetTextScale.md) |  | 
| [SetTextSize(float)](Bullet/SetTextSize.md) |  | 
| [SetTextStartChars(int)](Bullet/SetTextStartChars.md) |  | 
| [SetTextWordSpacing(float)](Bullet/SetTextWordSpacing.md) |  | 
| [SetVectorVar(Vector2)](Bullet/SetVectorVar.md) |  | 
| [SetVelocity(Vector2)](Bullet/SetVelocity.md) |  | 
| [Transform(DataPath&lt;[BulletData](BulletData.md)&gt;, float, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[])](Bullet/Transform.md) |  | 

</div>

