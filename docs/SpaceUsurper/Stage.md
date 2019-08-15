# Stage Class

<small>**Namespace**: SpaceUsurper</small>

<small>**Inheritance**: [Object](https://docs.microsoft.com/en-us/dotnet/api/system.object?view=netframework-4.5) → Stage</small>

## Properties

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [BehaviourHandler](Stage/BehaviourHandler.md) |  | 
| [BossFormCount](Stage/BossFormCount.md) |  | 
| [BossFormNumber](Stage/BossFormNumber.md) |  | 
| [CameraHandler](Stage/CameraHandler.md) |  | 
| [FixedDeltaTime](Stage/FixedDeltaTime.md) |  | 
| [FixedElapsedTime](Stage/FixedElapsedTime.md) |  | 
| [IsMenuStage](Stage/IsMenuStage.md) |  | 
| [IsPaused](Stage/IsPaused.md) |  | 
| [MiscDebugToggle](Stage/MiscDebugToggle.md) |  | 
| [NumBullets](Stage/NumBullets.md) |  | 
| [NumShotPatterns](Stage/NumShotPatterns.md) |  | 
| [NumSpawnedPatterns](Stage/NumSpawnedPatterns.md) |  | 
| [RawFixedDeltaTime](Stage/RawFixedDeltaTime.md) |  | 
| [RawFixedElapsedTime](Stage/RawFixedElapsedTime.md) |  | 
| [SongHandler](Stage/SongHandler.md) |  | 
| [SpeechHandler](Stage/SpeechHandler.md) |  | 
| [StageProgress](Stage/StageProgress.md) |  | 
| [TextHandler](Stage/TextHandler.md) |  | 
| [TimeScaleHandler](Stage/TimeScaleHandler.md) |  | 
| [UnitHandler](Stage/UnitHandler.md) |  | 

</div>

## Methods

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [AddFlatTimeScale(Single, Single)](Stage/AddFlatTimeScale.md) |  | 
| [AddForceToBullets(Vector2, Single, Single, EasingType, RadialDirectionMode, Vector2, Bullet)](Stage/AddForceToBullets.md) |  | 
| [AddPattern(DataPath&lt;PatternData&gt;, Vector2, Single, Boolean, Boolean, Single, Int32, Int32, DataPath&lt;StatusEffectData&gt;[], Int32[])](Stage/AddPattern.md) |  | 
| [AddSprite(DataPath&lt;SpriteData&gt;, Vector2, Single, Vector2, DepthLevel)](Stage/AddSprite.md) |  | 
| [AddTimeScale(Single, Single, EasingType)](Stage/AddTimeScale.md) |  | 
| [AffectBulletsInRadius(Vector2, Single, ActionList, ParameterCollection, Boolean, Boolean)](Stage/AffectBulletsInRadius.md) |  | 
| [AffectPlayer(ActionList, ParameterCollection)](Stage/AffectPlayer.md) |  | 
| [AffectTouchingBullets(Bullet, ActionList, Boolean, ParameterCollection, Boolean, Boolean)](Stage/AffectTouchingBullets.md) |  | 
| [AffectTouchingUnits(Bullet, ActionList, Boolean, ParameterCollection)](Stage/AffectTouchingUnits.md) |  | 
| [AffectUnitsInRadius(Vector2, Single, ActionList, ParameterCollection)](Stage/AffectUnitsInRadius.md) |  | 
| [ClearNumTimesShot(DataPath&lt;PatternData&gt;)](Stage/ClearNumTimesShot.md) |  | 
| [DespawnAddedPatterns(DataPath&lt;PatternData&gt;)](Stage/DespawnAddedPatterns.md) |  | 
| [DespawnPatterns(DataPath&lt;PatternData&gt;)](Stage/DespawnPatterns.md) |  | 
| [DestroyBullets(Vector2, Single, Bullet, Color)](Stage/DestroyBullets.md) |  | 
| [DoesUnitExist(Unit)](Stage/DoesUnitExist.md) |  | 
| [DrawDebugLine(Vector2, Vector2, Single)](Stage/DrawDebugLine.md) |  | 
| [DrawDebugLine(Vector2, Vector2, Color, Single, Single, Single)](Stage/DrawDebugLine.md) |  | 
| [Get(String)](Stage/Get.md) |  | 
| [GetNumBullets(DataPath&lt;BulletData&gt;)](Stage/GetNumBullets.md) |  | 
| [GetNumTimesShot(DataPath&lt;PatternData&gt;)](Stage/GetNumTimesShot.md) |  | 
| [GetUnit(String)](Stage/GetUnit.md) |  | 
| [IsRaycastHit(Vector2, Vector2, Boolean, Boolean, Unit)](Stage/IsRaycastHit.md) |  | 
| [PlaySfx(String, Vector2, Single, Single, Single)](Stage/PlaySfx.md) |  | 
| [PlaySfx(String, Single, Single, Single)](Stage/PlaySfx.md) |  | 
| [Raycast(Vector2, Vector2, Boolean, Boolean, Unit)](Stage/Raycast.md) |  | 
| [RepelBullets(Vector2, Single, Single, Single, EasingType, RadialDirectionMode, Vector2, DataPath&lt;BulletData&gt;, Bullet, Color)](Stage/RepelBullets.md) |  | 
| [RepelPlayer(Vector2, Single, Single, Single, EasingType)](Stage/RepelPlayer.md) |  | 
| [RepelUnits(Vector2, Single, Single, EasingType, RadialDirectionMode, Vector2, String, DataPath&lt;BulletData&gt;)](Stage/RepelUnits.md) |  | 
| [SetBgColor(Color, Single, EasingType)](Stage/SetBgColor.md) |  | 
| [SetCameraSize(Single)](Stage/SetCameraSize.md) |  | 
| [SetChromaticAberration(Single)](Stage/SetChromaticAberration.md) |  | 
| [SetColorFilter(Color)](Stage/SetColorFilter.md) |  | 
| [SetContrast(Single)](Stage/SetContrast.md) |  | 
| [SetDebrisForce(Vector2)](Stage/SetDebrisForce.md) |  | 
| [SetHueShift(Single)](Stage/SetHueShift.md) |  | 
| [SetLoopingSfxMaxDistance(Int32, Single)](Stage/SetLoopingSfxMaxDistance.md) |  | 
| [SetLoopingSfxPitch(Int32, Single)](Stage/SetLoopingSfxPitch.md) |  | 
| [SetLoopingSfxPosition(Int32, Vector2)](Stage/SetLoopingSfxPosition.md) |  | 
| [SetLoopingSfxVolume(Int32, Single)](Stage/SetLoopingSfxVolume.md) |  | 
| [SetSaturation(Single)](Stage/SetSaturation.md) |  | 
| [SetState(String)](Stage/SetState.md) |  | 
| [SetTemperature(Single)](Stage/SetTemperature.md) |  | 
| [SetViewSizeLerpSpeed(Single)](Stage/SetViewSizeLerpSpeed.md) |  | 
| [ShakeCamera(Single, Single, EasingType, Boolean)](Stage/ShakeCamera.md) |  | 
| [SpawnBullet(DataPath&lt;BulletData&gt;, Vector2, Single, Vector2, Boolean, Single, Single, Int32, Int32)](Stage/SpawnBullet.md) |  | 
| [SpawnBullet(DataPath&lt;BulletData&gt;, Vector2, Vector2, Vector2, Boolean, Single, Single, Int32, Int32)](Stage/SpawnBullet.md) |  | 
| [SpawnPattern(DataPath&lt;PatternData&gt;, Vector2, Single, Boolean, Boolean, Single, Int32, Int32, DataPath&lt;StatusEffectData&gt;[], Int32[])](Stage/SpawnPattern.md) |  | 
| [SpawnPattern(DataPath&lt;PatternData&gt;[], Int32, Vector2, Single, Boolean, Boolean, Single, Int32, Int32, DataPath&lt;StatusEffectData&gt;[], Int32[])](Stage/SpawnPattern.md) |  | 
| [SpawnPattern(DataPath&lt;PatternData&gt;, Vector2, Vector2, Boolean, Boolean, Single, Int32, Int32, DataPath&lt;StatusEffectData&gt;[], Int32[])](Stage/SpawnPattern.md) |  | 
| [SpawnPattern(DataPath&lt;PatternData&gt;[], Int32, Vector2, Vector2, Boolean, Boolean, Single, Int32, Int32, DataPath&lt;StatusEffectData&gt;[], Int32[])](Stage/SpawnPattern.md) |  | 
| [StartLoopingSfx(String, Vector2, Single, Single, Single)](Stage/StartLoopingSfx.md) |  | 
| [StopLoopingSfx(Int32)](Stage/StopLoopingSfx.md) |  | 
| [TransformBullets(Vector2, Single, Bullet, DataPath&lt;BulletData&gt;, Single)](Stage/TransformBullets.md) |  | 
| [ZoomCamera(Single, Single, Single, EasingType, Boolean)](Stage/ZoomCamera.md) |  | 

</div>

