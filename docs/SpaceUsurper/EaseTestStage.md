# EaseTestStage Class

<small>**Namespace**: SpaceUsurper</small>

<small>**Inheritance**: [Object](https://docs.microsoft.com/en-us/dotnet/api/system.object?view=netframework-4.5) → [Stage](Stage.md) → EaseTestStage</small>

## Properties

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [BehaviourHandler](Stage/BehaviourHandler.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [BossFormCount](Stage/BossFormCount.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [BossFormNumber](Stage/BossFormNumber.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [CameraHandler](Stage/CameraHandler.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [FixedDeltaTime](Stage/FixedDeltaTime.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [FixedElapsedTime](Stage/FixedElapsedTime.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [IsMenuStage](Stage/IsMenuStage.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [IsPaused](Stage/IsPaused.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [MiscDebugToggle](Stage/MiscDebugToggle.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [NumBullets](Stage/NumBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [NumShotPatterns](Stage/NumShotPatterns.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [NumSpawnedPatterns](Stage/NumSpawnedPatterns.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [RawFixedDeltaTime](Stage/RawFixedDeltaTime.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [RawFixedElapsedTime](Stage/RawFixedElapsedTime.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SongHandler](Stage/SongHandler.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpeechHandler](Stage/SpeechHandler.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [StageProgress](Stage/StageProgress.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [TextHandler](Stage/TextHandler.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [TimeScaleHandler](Stage/TimeScaleHandler.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [UnitHandler](Stage/UnitHandler.md) | <small>(Inherited from [Stage](Stage.md))</small> | 

</div>

## Methods

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [AddFlatTimeScale(Single, Single)](Stage/AddFlatTimeScale.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AddForceToBullets(Vector2, Single, Single, EasingType, RadialDirectionMode, Vector2, Bullet)](Stage/AddForceToBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AddPattern(DataPath&lt;PatternData&gt;, Vector2, Single, Boolean, Boolean, Single, Int32, Int32, DataPath&lt;StatusEffectData&gt;[], Int32[])](Stage/AddPattern.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AddSprite(DataPath&lt;SpriteData&gt;, Vector2, Single, Vector2, DepthLevel)](Stage/AddSprite.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AddTimeScale(Single, Single, EasingType)](Stage/AddTimeScale.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AffectBulletsInRadius(Vector2, Single, ActionList, ParameterCollection, Boolean, Boolean)](Stage/AffectBulletsInRadius.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AffectPlayer(ActionList, ParameterCollection)](Stage/AffectPlayer.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AffectTouchingBullets(Bullet, ActionList, Boolean, ParameterCollection, Boolean, Boolean)](Stage/AffectTouchingBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AffectTouchingUnits(Bullet, ActionList, Boolean, ParameterCollection)](Stage/AffectTouchingUnits.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AffectUnitsInRadius(Vector2, Single, ActionList, ParameterCollection)](Stage/AffectUnitsInRadius.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [ClearNumTimesShot(DataPath&lt;PatternData&gt;)](Stage/ClearNumTimesShot.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DespawnAddedPatterns(DataPath&lt;PatternData&gt;)](Stage/DespawnAddedPatterns.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DespawnPatterns(DataPath&lt;PatternData&gt;)](Stage/DespawnPatterns.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DestroyBullets(Vector2, Single, Bullet, Color)](Stage/DestroyBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DoesUnitExist(Unit)](Stage/DoesUnitExist.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DrawDebugLine(Vector2, Vector2, Single)](Stage/DrawDebugLine.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DrawDebugLine(Vector2, Vector2, Color, Single, Single, Single)](Stage/DrawDebugLine.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [Get(String)](Stage/Get.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [GetNumBullets(DataPath&lt;BulletData&gt;)](Stage/GetNumBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [GetNumTimesShot(DataPath&lt;PatternData&gt;)](Stage/GetNumTimesShot.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [GetUnit(String)](Stage/GetUnit.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [IsRaycastHit(Vector2, Vector2, Boolean, Boolean, Unit)](Stage/IsRaycastHit.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [PlaySfx(String, Vector2, Single, Single, Single)](Stage/PlaySfx.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [PlaySfx(String, Single, Single, Single)](Stage/PlaySfx.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [Raycast(Vector2, Vector2, Boolean, Boolean, Unit)](Stage/Raycast.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [RepelBullets(Vector2, Single, Single, Single, EasingType, RadialDirectionMode, Vector2, DataPath&lt;BulletData&gt;, Bullet, Color)](Stage/RepelBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [RepelPlayer(Vector2, Single, Single, Single, EasingType)](Stage/RepelPlayer.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [RepelUnits(Vector2, Single, Single, EasingType, RadialDirectionMode, Vector2, String, DataPath&lt;BulletData&gt;)](Stage/RepelUnits.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetBgColor(Color, Single, EasingType)](Stage/SetBgColor.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetCameraSize(Single)](Stage/SetCameraSize.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetChromaticAberration(Single)](Stage/SetChromaticAberration.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetColorFilter(Color)](Stage/SetColorFilter.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetContrast(Single)](Stage/SetContrast.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetDebrisForce(Vector2)](Stage/SetDebrisForce.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetHueShift(Single)](Stage/SetHueShift.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetLoopingSfxMaxDistance(Int32, Single)](Stage/SetLoopingSfxMaxDistance.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetLoopingSfxPitch(Int32, Single)](Stage/SetLoopingSfxPitch.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetLoopingSfxPosition(Int32, Vector2)](Stage/SetLoopingSfxPosition.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetLoopingSfxVolume(Int32, Single)](Stage/SetLoopingSfxVolume.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetSaturation(Single)](Stage/SetSaturation.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetState(String)](Stage/SetState.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetTemperature(Single)](Stage/SetTemperature.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetViewSizeLerpSpeed(Single)](Stage/SetViewSizeLerpSpeed.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [ShakeCamera(Single, Single, EasingType, Boolean)](Stage/ShakeCamera.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnBullet(DataPath&lt;BulletData&gt;, Vector2, Single, Vector2, Boolean, Single, Single, Int32, Int32)](Stage/SpawnBullet.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnBullet(DataPath&lt;BulletData&gt;, Vector2, Vector2, Vector2, Boolean, Single, Single, Int32, Int32)](Stage/SpawnBullet.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnPattern(DataPath&lt;PatternData&gt;, Vector2, Single, Boolean, Boolean, Single, Int32, Int32, DataPath&lt;StatusEffectData&gt;[], Int32[])](Stage/SpawnPattern.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnPattern(DataPath&lt;PatternData&gt;[], Int32, Vector2, Single, Boolean, Boolean, Single, Int32, Int32, DataPath&lt;StatusEffectData&gt;[], Int32[])](Stage/SpawnPattern.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnPattern(DataPath&lt;PatternData&gt;, Vector2, Vector2, Boolean, Boolean, Single, Int32, Int32, DataPath&lt;StatusEffectData&gt;[], Int32[])](Stage/SpawnPattern.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnPattern(DataPath&lt;PatternData&gt;[], Int32, Vector2, Vector2, Boolean, Boolean, Single, Int32, Int32, DataPath&lt;StatusEffectData&gt;[], Int32[])](Stage/SpawnPattern.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [StartLoopingSfx(String, Vector2, Single, Single, Single)](Stage/StartLoopingSfx.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [StopLoopingSfx(Int32)](Stage/StopLoopingSfx.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [TransformBullets(Vector2, Single, Bullet, DataPath&lt;BulletData&gt;, Single)](Stage/TransformBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [ZoomCamera(Single, Single, Single, EasingType, Boolean)](Stage/ZoomCamera.md) | <small>(Inherited from [Stage](Stage.md))</small> | 

</div>

