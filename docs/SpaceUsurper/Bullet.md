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
| [AddBullet(DataPath&lt;BulletData&gt;, Vector2, Single, Single)](Bullet/AddBullet.md) |  | 
| [AddForce(Vector2)](Bullet/AddForce.md) |  | 
| [AddImpulseVelocity(Vector2)](Bullet/AddImpulseVelocity.md) |  | 
| [AddPattern(DataPath&lt;PatternData&gt;, Single, MirrorMode, Single)](Bullet/AddPattern.md) |  | 
| [AddText(String, Vector2, Color, Color, Color, Vector2, FloatingTextFont, String, Single, Single, Single, Single, BulletTextAlignment, Boolean, Single)](Bullet/AddText.md) |  | 
| [AddTimeScale(Single, Single, EasingType)](Bullet/AddTimeScale.md) |  | 
| [AddVelocity(Vector2)](Bullet/AddVelocity.md) |  | 
| [AffectTouchingBullets(ActionList, Boolean, ParameterCollection, Boolean)](Bullet/AffectTouchingBullets.md) |  | 
| [AffectTouchingUnits(ActionList, Boolean, ParameterCollection)](Bullet/AffectTouchingUnits.md) |  | 
| [ClearRedirect()](Bullet/ClearRedirect.md) |  | 
| [CreateBulletImpactEffect(Vector2, Vector2, Single)](Bullet/CreateBulletImpactEffect.md) |  | 
| [DamagePlayer()](Bullet/DamagePlayer.md) |  | 
| [Despawn()](Bullet/Despawn.md) |  | 
| [DespawnText(Vector2, Single, EasingType)](Bullet/DespawnText.md) |  | 
| [Flash(Color, Single, EasingType, Single, Single, Boolean)](Bullet/Flash.md) |  | 
| [GetTextSize()](Bullet/GetTextSize.md) |  | 
| [GetVolleyBullet(Int32)](Bullet/GetVolleyBullet.md) |  | 
| [HitPlayer()](Bullet/HitPlayer.md) |  | 
| [Impact(Vector2, Vector2)](Bullet/Impact.md) |  | 
| [IsTouchingPlayer()](Bullet/IsTouchingPlayer.md) |  | 
| [OverrideColorBlinkTime(Single)](Bullet/OverrideColorBlinkTime.md) |  | 
| [OverrideColors(Color, Color, Color, Color, Color, Color)](Bullet/OverrideColors.md) |  | 
| [OverrideColors(Color, Color, Color)](Bullet/OverrideColors.md) |  | 
| [Redirect(Vector2)](Bullet/Redirect.md) |  | 
| [Reflect(Unit, Vector2, Vector2, Boolean)](Bullet/Reflect.md) |  | 
| [SetBounds(Rect)](Bullet/SetBounds.md) |  | 
| [SetDespawnStyle(DespawnStyle)](Bullet/SetDespawnStyle.md) |  | 
| [SetDespawnTime(Single)](Bullet/SetDespawnTime.md) |  | 
| [SetFacingAngle(Single)](Bullet/SetFacingAngle.md) |  | 
| [SetFacingDirection(Vector2)](Bullet/SetFacingDirection.md) |  | 
| [SetFloatVar(Single)](Bullet/SetFloatVar.md) |  | 
| [SetImpulseVelocity(Vector2)](Bullet/SetImpulseVelocity.md) |  | 
| [SetIntVar(Int32)](Bullet/SetIntVar.md) |  | 
| [SetKeyframe(Int32)](Bullet/SetKeyframe.md) | Sets the bullet keyframe immediately. | 
| [SetKeyframe_Legacy(Int32)](Bullet/SetKeyframe_Legacy.md) |  | 
| [SetPosB(Vector2)](Bullet/SetPosB.md) |  | 
| [SetPosition(Vector2)](Bullet/SetPosition.md) |  | 
| [SetStatusLevel(Int32)](Bullet/SetStatusLevel.md) |  | 
| [SetTextCharacterSpacing(Single)](Bullet/SetTextCharacterSpacing.md) |  | 
| [SetTextColor(Color)](Bullet/SetTextColor.md) |  | 
| [SetTextColorA(Color)](Bullet/SetTextColorA.md) |  | 
| [SetTextColorB(Color)](Bullet/SetTextColorB.md) |  | 
| [SetTextColorBlinkTime(Single)](Bullet/SetTextColorBlinkTime.md) |  | 
| [SetTextLerpSpeed(Single)](Bullet/SetTextLerpSpeed.md) |  | 
| [SetTextLineSpacing(Single)](Bullet/SetTextLineSpacing.md) |  | 
| [SetTextMessage(String)](Bullet/SetTextMessage.md) |  | 
| [SetTextNumChars(Int32)](Bullet/SetTextNumChars.md) |  | 
| [SetTextOffset(Vector2)](Bullet/SetTextOffset.md) |  | 
| [SetTextOpacity(Single)](Bullet/SetTextOpacity.md) |  | 
| [SetTextOutlineColor(Color)](Bullet/SetTextOutlineColor.md) |  | 
| [SetTextOutlineWidth(Single)](Bullet/SetTextOutlineWidth.md) |  | 
| [SetTextScale(Vector2)](Bullet/SetTextScale.md) |  | 
| [SetTextSize(Single)](Bullet/SetTextSize.md) |  | 
| [SetTextStartChars(Int32)](Bullet/SetTextStartChars.md) |  | 
| [SetTextWordSpacing(Single)](Bullet/SetTextWordSpacing.md) |  | 
| [SetVectorVar(Vector2)](Bullet/SetVectorVar.md) |  | 
| [SetVelocity(Vector2)](Bullet/SetVelocity.md) |  | 
| [Transform(DataPath&lt;BulletData&gt;, Single, DataPath&lt;StatusEffectData&gt;[])](Bullet/Transform.md) |  | 

</div>

