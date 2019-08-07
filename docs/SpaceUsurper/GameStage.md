# GameStage Class

<small>**Namespace**: SpaceUsurper</small>

<small>**Inheritance**: [Object](https://docs.microsoft.com/en-us/dotnet/api/system.object?view=netframework-4.5) → [Stage](Stage.md) → GameStage</small>

## Properties

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [BaseBgColor](GameStage/BaseBgColor.md) |  | 
| [BehaviourHandler](Stage/BehaviourHandler.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [BgColor](GameStage/BgColor.md) |  | 
| [BossFormCount](GameStage/BossFormCount.md) |  | 
| [BossFormNumber](GameStage/BossFormNumber.md) |  | 
| [Bounds](GameStage/Bounds.md) |  | 
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
| [AddFlatTimeScale(float, float)](Stage/AddFlatTimeScale.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AddForceToBullets(Vector2, float, float, EasingType, RadialDirectionMode, Vector2, Bullet)](Stage/AddForceToBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AddPattern(DataPath&lt;[PatternData](PatternData.md)&gt;, Vector2, float, bool, bool, float, int, int, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[], [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[])](Stage/AddPattern.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AddSprite(DataPath&lt;[SpriteData](SpriteData.md)&gt;, Vector2, float, Vector2, DepthLevel)](Stage/AddSprite.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AddTimeScale(float, float, EasingType)](Stage/AddTimeScale.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AffectBulletsInRadius(Vector2, float, ActionList, ParameterCollection, bool, bool)](Stage/AffectBulletsInRadius.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AffectPlayer(ActionList, ParameterCollection)](Stage/AffectPlayer.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AffectTouchingBullets(Bullet, ActionList, bool, ParameterCollection, bool, bool)](Stage/AffectTouchingBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AffectTouchingUnits(Bullet, ActionList, bool, ParameterCollection)](Stage/AffectTouchingUnits.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [AffectUnitsInRadius(Vector2, float, ActionList, ParameterCollection)](Stage/AffectUnitsInRadius.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [ClearAccelVectorFunc()](GameStage/ClearAccelVectorFunc.md) |  | 
| [ClearGridColorFunc()](GameStage/ClearGridColorFunc.md) |  | 
| [ClearNumTimesShot(DataPath&lt;[PatternData](PatternData.md)&gt;)](Stage/ClearNumTimesShot.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DespawnAddedPatterns(DataPath&lt;[PatternData](PatternData.md)&gt;)](Stage/DespawnAddedPatterns.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DespawnPatterns(DataPath&lt;[PatternData](PatternData.md)&gt;)](Stage/DespawnPatterns.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DestroyBullets(Vector2, float, Bullet, Color)](Stage/DestroyBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DestroyUnit(String)](GameStage/DestroyUnit.md) |  | 
| [DoesUnitExist(Unit)](Stage/DoesUnitExist.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DrawDebugLine(Vector2, Vector2, float)](Stage/DrawDebugLine.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [DrawDebugLine(Vector2, Vector2, Color, float, float, float)](Stage/DrawDebugLine.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [Get(String)](Stage/Get.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [GetClosestUnit(Vector2, String)](GameStage/GetClosestUnit.md) |  | 
| [GetDistanceToUnit(Vector2, String)](GameStage/GetDistanceToUnit.md) |  | 
| [GetNumBullets(DataPath&lt;[BulletData](BulletData.md)&gt;)](Stage/GetNumBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [GetNumNearbyUnits(Vector2, String, float)](GameStage/GetNumNearbyUnits.md) |  | 
| [GetNumTimesShot(DataPath&lt;[PatternData](PatternData.md)&gt;)](Stage/GetNumTimesShot.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [GetNumUnits(String, bool)](GameStage/GetNumUnits.md) |  | 
| [GetUnit(String)](GameStage/GetUnit.md) |  | 
| [GetUnits(String)](GameStage/GetUnits.md) |  | 
| [IsRaycastHit(Vector2, Vector2, bool, bool, Unit)](Stage/IsRaycastHit.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [LerpBounds(Rect, float, EasingType)](GameStage/LerpBounds.md) |  | 
| [PlaySfx(String, Vector2, float, float, float)](Stage/PlaySfx.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [PlaySfx(String, float, float, float)](Stage/PlaySfx.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [Raycast(Vector2, Vector2, bool, bool, Unit)](Stage/Raycast.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [RemoteControlNearbyUnits(Vector2, String, float, ActionList, DataPath&lt;[BulletData](BulletData.md)&gt;, float)](GameStage/RemoteControlNearbyUnits.md) |  | 
| [RepelBullets(Vector2, float, float, float, EasingType, RadialDirectionMode, Vector2, DataPath&lt;[BulletData](BulletData.md)&gt;, Bullet, Color)](Stage/RepelBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [RepelPlayer(Vector2, float, float, float, EasingType)](Stage/RepelPlayer.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [RepelUnits(Vector2, float, float, EasingType, RadialDirectionMode, Vector2, String, DataPath&lt;[BulletData](BulletData.md)&gt;)](Stage/RepelUnits.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetBgColor(Color, float, EasingType)](Stage/SetBgColor.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetBgColorFunc(ScriptFunc&lt;[Color](https://docs.unity3d.com/ScriptReference/Color.html)&gt;)](GameStage/SetBgColorFunc.md) |  | 
| [SetBounds(Rect, bool)](GameStage/SetBounds.md) |  | 
| [SetCameraSize(float)](Stage/SetCameraSize.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetChromaticAberration(float)](Stage/SetChromaticAberration.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetColorFilter(Color)](Stage/SetColorFilter.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetContrast(float)](Stage/SetContrast.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetDebrisForce(Vector2)](Stage/SetDebrisForce.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetGridColor(Color, float, EasingType)](GameStage/SetGridColor.md) |  | 
| [SetGridColorFunc(ScriptFunc&lt;[Color](https://docs.unity3d.com/ScriptReference/Color.html)&gt;)](GameStage/SetGridColorFunc.md) |  | 
| [SetGridEdgeScale(float, float, EasingType)](GameStage/SetGridEdgeScale.md) |  | 
| [SetGridEdgeWarp(float, float, EasingType)](GameStage/SetGridEdgeWarp.md) |  | 
| [SetGridEdgeWidth(float, float, EasingType)](GameStage/SetGridEdgeWidth.md) |  | 
| [SetGridSpacing(Vector2, float, EasingType)](GameStage/SetGridSpacing.md) |  | 
| [SetGridThickness(float, float, EasingType)](GameStage/SetGridThickness.md) |  | 
| [SetHueShift(float)](Stage/SetHueShift.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetLetterboxColor(Color, float, EasingType)](GameStage/SetLetterboxColor.md) |  | 
| [SetLoopingSfxMaxDistance(int, float)](Stage/SetLoopingSfxMaxDistance.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetLoopingSfxPitch(int, float)](Stage/SetLoopingSfxPitch.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetLoopingSfxPosition(int, Vector2)](Stage/SetLoopingSfxPosition.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetLoopingSfxVolume(int, float)](Stage/SetLoopingSfxVolume.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetPlayer(DataPath&lt;[PlayerData](PlayerData.md)&gt;)](GameStage/SetPlayer.md) |  | 
| [SetSaturation(float)](Stage/SetSaturation.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetState(String)](Stage/SetState.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetTemperature(float)](Stage/SetTemperature.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SetViewSizeLerpSpeed(float)](Stage/SetViewSizeLerpSpeed.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [ShakeCamera(float, float, EasingType, bool)](Stage/ShakeCamera.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnBullet(DataPath&lt;[BulletData](BulletData.md)&gt;, Vector2, float, Vector2, bool, float, float, int, int)](Stage/SpawnBullet.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnBullet(DataPath&lt;[BulletData](BulletData.md)&gt;, Vector2, Vector2, Vector2, bool, float, float, int, int)](Stage/SpawnBullet.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnPattern(DataPath&lt;[PatternData](PatternData.md)&gt;, Vector2, float, bool, bool, float, int, int, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[], [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[])](Stage/SpawnPattern.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnPattern([DataPath](DataPath-1.md)&lt;[PatternData](PatternData.md)&gt;[], int, Vector2, float, bool, bool, float, int, int, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[], [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[])](Stage/SpawnPattern.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnPattern(DataPath&lt;[PatternData](PatternData.md)&gt;, Vector2, Vector2, bool, bool, float, int, int, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[], [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[])](Stage/SpawnPattern.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnPattern([DataPath](DataPath-1.md)&lt;[PatternData](PatternData.md)&gt;[], int, Vector2, Vector2, bool, bool, float, int, int, [DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;[], [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[])](Stage/SpawnPattern.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [SpawnUnit(String, Vector2, Vector2, Direction)](GameStage/SpawnUnit.md) |  | 
| [StartLoopingSfx(String, Vector2, float, float, float)](Stage/StartLoopingSfx.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [StopLoopingSfx(int)](Stage/StopLoopingSfx.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [TransformBullets(Vector2, float, Bullet, DataPath&lt;[BulletData](BulletData.md)&gt;, float)](Stage/TransformBullets.md) | <small>(Inherited from [Stage](Stage.md))</small> | 
| [ZoomCamera(float, float, float, EasingType, bool)](Stage/ZoomCamera.md) | <small>(Inherited from [Stage](Stage.md))</small> | 

</div>
