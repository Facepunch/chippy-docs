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
| [AddFlatTimeScale(float, float)](Stage/AddFlatTimeScale.md) |  | 
| [AddForceToBullets(Vector2, float, float, EasingType, RadialDirectionMode, Vector2, Bullet)](Stage/AddForceToBullets.md) |  | 
| [AddPattern(DataPath&lt;[PatternData](PatternData.md)&gt;, Vector2, float, bool, bool, float, int, int, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[], [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[])](Stage/AddPattern.md) |  | 
| [AddSprite(DataPath&lt;[SpriteData](SpriteData.md)&gt;, Vector2, float, Vector2, DepthLevel)](Stage/AddSprite.md) |  | 
| [AddTimeScale(float, float, EasingType)](Stage/AddTimeScale.md) |  | 
| [AffectBulletsInRadius(Vector2, float, ActionList, ParameterCollection, bool, bool)](Stage/AffectBulletsInRadius.md) |  | 
| [AffectPlayer(ActionList, ParameterCollection)](Stage/AffectPlayer.md) |  | 
| [AffectTouchingBullets(Bullet, ActionList, bool, ParameterCollection, bool, bool)](Stage/AffectTouchingBullets.md) |  | 
| [AffectTouchingUnits(Bullet, ActionList, bool, ParameterCollection)](Stage/AffectTouchingUnits.md) |  | 
| [AffectUnitsInRadius(Vector2, float, ActionList, ParameterCollection)](Stage/AffectUnitsInRadius.md) |  | 
| [ClearNumTimesShot(DataPath&lt;[PatternData](PatternData.md)&gt;)](Stage/ClearNumTimesShot.md) |  | 
| [DespawnAddedPatterns(DataPath&lt;[PatternData](PatternData.md)&gt;)](Stage/DespawnAddedPatterns.md) |  | 
| [DespawnPatterns(DataPath&lt;[PatternData](PatternData.md)&gt;)](Stage/DespawnPatterns.md) |  | 
| [DestroyBullets(Vector2, float, Bullet, Color)](Stage/DestroyBullets.md) |  | 
| [DoesUnitExist(Unit)](Stage/DoesUnitExist.md) |  | 
| [DrawDebugLine(Vector2, Vector2, float)](Stage/DrawDebugLine.md) |  | 
| [DrawDebugLine(Vector2, Vector2, Color, float, float, float)](Stage/DrawDebugLine.md) |  | 
| [Get(String)](Stage/Get.md) |  | 
| [GetNumBullets(DataPath&lt;[BulletData](BulletData.md)&gt;)](Stage/GetNumBullets.md) |  | 
| [GetNumTimesShot(DataPath&lt;[PatternData](PatternData.md)&gt;)](Stage/GetNumTimesShot.md) |  | 
| [GetUnit(String)](Stage/GetUnit.md) |  | 
| [IsRaycastHit(Vector2, Vector2, bool, bool, Unit)](Stage/IsRaycastHit.md) |  | 
| [PlaySfx(String, Vector2, float, float, float)](Stage/PlaySfx.md) |  | 
| [PlaySfx(String, float, float, float)](Stage/PlaySfx.md) |  | 
| [Raycast(Vector2, Vector2, bool, bool, Unit)](Stage/Raycast.md) |  | 
| [RepelBullets(Vector2, float, float, float, EasingType, RadialDirectionMode, Vector2, DataPath&lt;[BulletData](BulletData.md)&gt;, Bullet, Color)](Stage/RepelBullets.md) |  | 
| [RepelPlayer(Vector2, float, float, float, EasingType)](Stage/RepelPlayer.md) |  | 
| [RepelUnits(Vector2, float, float, EasingType, RadialDirectionMode, Vector2, String, DataPath&lt;[BulletData](BulletData.md)&gt;)](Stage/RepelUnits.md) |  | 
| [SetBgColor(Color, float, EasingType)](Stage/SetBgColor.md) |  | 
| [SetCameraSize(float)](Stage/SetCameraSize.md) |  | 
| [SetChromaticAberration(float)](Stage/SetChromaticAberration.md) |  | 
| [SetColorFilter(Color)](Stage/SetColorFilter.md) |  | 
| [SetContrast(float)](Stage/SetContrast.md) |  | 
| [SetDebrisForce(Vector2)](Stage/SetDebrisForce.md) |  | 
| [SetHueShift(float)](Stage/SetHueShift.md) |  | 
| [SetLoopingSfxMaxDistance(int, float)](Stage/SetLoopingSfxMaxDistance.md) |  | 
| [SetLoopingSfxPitch(int, float)](Stage/SetLoopingSfxPitch.md) |  | 
| [SetLoopingSfxPosition(int, Vector2)](Stage/SetLoopingSfxPosition.md) |  | 
| [SetLoopingSfxVolume(int, float)](Stage/SetLoopingSfxVolume.md) |  | 
| [SetSaturation(float)](Stage/SetSaturation.md) |  | 
| [SetState(String)](Stage/SetState.md) |  | 
| [SetTemperature(float)](Stage/SetTemperature.md) |  | 
| [SetViewSizeLerpSpeed(float)](Stage/SetViewSizeLerpSpeed.md) |  | 
| [ShakeCamera(float, float, EasingType, bool)](Stage/ShakeCamera.md) |  | 
| [SpawnBullet(DataPath&lt;[BulletData](BulletData.md)&gt;, Vector2, float, Vector2, bool, float, float, int, int)](Stage/SpawnBullet.md) |  | 
| [SpawnBullet(DataPath&lt;[BulletData](BulletData.md)&gt;, Vector2, Vector2, Vector2, bool, float, float, int, int)](Stage/SpawnBullet.md) |  | 
| [SpawnPattern(DataPath&lt;[PatternData](PatternData.md)&gt;, Vector2, float, bool, bool, float, int, int, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[], [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[])](Stage/SpawnPattern.md) |  | 
| [SpawnPattern([DataPath](DataPath-1.md)&lt;[PatternData](PatternData.md)&gt;[], int, Vector2, float, bool, bool, float, int, int, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[], [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[])](Stage/SpawnPattern.md) |  | 
| [SpawnPattern(DataPath&lt;[PatternData](PatternData.md)&gt;, Vector2, Vector2, bool, bool, float, int, int, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[], [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[])](Stage/SpawnPattern.md) |  | 
| [SpawnPattern([DataPath](DataPath-1.md)&lt;[PatternData](PatternData.md)&gt;[], int, Vector2, Vector2, bool, bool, float, int, int, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[], [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[])](Stage/SpawnPattern.md) |  | 
| [StartLoopingSfx(String, Vector2, float, float, float)](Stage/StartLoopingSfx.md) |  | 
| [StopLoopingSfx(int)](Stage/StopLoopingSfx.md) |  | 
| [TransformBullets(Vector2, float, Bullet, DataPath&lt;[BulletData](BulletData.md)&gt;, float)](Stage/TransformBullets.md) |  | 
| [ZoomCamera(float, float, float, EasingType, bool)](Stage/ZoomCamera.md) |  | 

</div>

