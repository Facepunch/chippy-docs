# Unit Class

<small>**Namespace**: SpaceUsurper</small>

<small>**Inheritance**: [Object](https://docs.microsoft.com/en-us/dotnet/api/system.object?view=netframework-4.5) → [Drawable](Drawable.md) → Unit</small>

## Properties

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [CoreHpPercent](Unit/CoreHpPercent.md) |  | 
| [CorePos](Unit/CorePos.md) |  | 
| [CurrAnimName](Unit/CurrAnimName.md) |  | 
| [CurrentCore](Unit/CurrentCore.md) |  | 
| [CurrentState](Unit/CurrentState.md) |  | 
| [CurrFormData](Unit/CurrFormData.md) |  | 
| [CurrFormNum](Unit/CurrFormNum.md) |  | 
| [CurrPxcFrameNum](Unit/CurrPxcFrameNum.md) |  | 
| [DataPath](Unit/DataPath.md) |  | 
| [ElapsedFormTime](Unit/ElapsedFormTime.md) |  | 
| [ElapsedTime](Unit/ElapsedTime.md) |  | 
| [ExistingPixelCount](Unit/ExistingPixelCount.md) |  | 
| [ExistingPixelPercent](Unit/ExistingPixelPercent.md) |  | 
| [FacingAngle](Unit/FacingAngle.md) |  | 
| [FacingVector](Unit/FacingVector.md) |  | 
| [HasFullyEnteredBounds](Unit/HasFullyEnteredBounds.md) |  | 
| [HasFullyEnteredLevel](Unit/HasFullyEnteredLevel.md) |  | 
| [HidePercent](Unit/HidePercent.md) |  | 
| [ImplodeProgress](Unit/ImplodeProgress.md) |  | 
| [IsActive](Unit/IsActive.md) | While active, not eligible to be re-used in pools. | 
| [IsAnimPlaying](Unit/IsAnimPlaying.md) |  | 
| [IsDestroyed](Unit/IsDestroyed.md) |  | 
| [IsFullyInBounds](Unit/IsFullyInBounds.md) |  | 
| [IsFullyInLevel](Unit/IsFullyInLevel.md) |  | 
| [IsHidden](Unit/IsHidden.md) |  | 
| [IsHiding](Unit/IsHiding.md) |  | 
| [IsImploding](Unit/IsImploding.md) |  | 
| [IsPartiallyInBounds](Unit/IsPartiallyInBounds.md) |  | 
| [IsPartiallyInLevel](Unit/IsPartiallyInLevel.md) |  | 
| [IsRevealing](Unit/IsRevealing.md) |  | 
| [IsRotatingToFace](Unit/IsRotatingToFace.md) |  | 
| [IsSpawning](Unit/IsSpawning.md) |  | 
| [Movement](Unit/Movement.md) |  | 
| [NumActiveParts](Unit/NumActiveParts.md) |  | 
| [NumDestroyedParts](Unit/NumDestroyedParts.md) |  | 
| [NumDestroyedPixels](Unit/NumDestroyedPixels.md) |  | 
| [NumShotPatterns](Unit/NumShotPatterns.md) |  | 
| [NumShotPatternsThisForm](Unit/NumShotPatternsThisForm.md) |  | 
| [NumSpeechBubbles](Unit/NumSpeechBubbles.md) |  | 
| [Opacity](Unit/Opacity.md) |  | 
| [OriginalSpawnPos](Unit/OriginalSpawnPos.md) |  | 
| [OutOfBoundsPercent](Unit/OutOfBoundsPercent.md) |  | 
| [Position](Unit/Position.md) |  | 
| [Radius](Unit/Radius.md) |  | 
| [SpawnPercent](Unit/SpawnPercent.md) |  | 
| [SpawnPos](Unit/SpawnPos.md) |  | 
| [TimeScale](Unit/TimeScale.md) |  | 
| [TimeSinceCoreHit](Unit/TimeSinceCoreHit.md) |  | 
| [TotalPixelCount](Unit/TotalPixelCount.md) |  | 
| [TotalVelocity](Unit/TotalVelocity.md) |  | 
| [Velocity](Unit/Velocity.md) |  | 

</div>

## Methods

<div markdown="1" class="member-table">

| Name | Description |
| :--- | ----------- |
| [AddForce(Vector2)](Unit/AddForce.md) |  | 
| [AddPattern(DataPath&lt;[PatternData](PatternData.md)&gt;, Vector2, float, bool, bool, float, int, int)](Unit/AddPattern.md) |  | 
| [AddRotationForce(Vector2, Vector2, float)](Unit/AddRotationForce.md) |  | 
| [AddTimeScale(float, float, EasingType)](Unit/AddTimeScale.md) |  | 
| [AddVelocity(Vector2)](Unit/AddVelocity.md) |  | 
| [AdjustPartCounter(String, int)](Unit/AdjustPartCounter.md) |  | 
| [AimTowards(float, float)](Unit/AimTowards.md) |  | 
| [CalculateBaseFormProgress(int)](Unit/CalculateBaseFormProgress.md) |  | 
| [CancelRotateToFace()](Unit/CancelRotateToFace.md) |  | 
| [ChargePattern([DataPath](DataPath-1.md)&lt;[PatternData](PatternData.md)&gt;[], int, String, PartSelectMode, float, MirrorMode, FlipPatternMode, float, ScriptFunc&lt;[Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html)&gt;, float, int, int, float, int, int, List&lt;[DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;&gt;, float)](Unit/ChargePattern.md) |  | 
| [ChargePattern(DataPath&lt;[PatternData](PatternData.md)&gt;, String, PartSelectMode, float, MirrorMode, FlipPatternMode, float, ScriptFunc&lt;[Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html)&gt;, float, int, int, float, int, int, List&lt;[DataPath](DataPath-1.md)&lt;[StatusEffectData](StatusEffectData.md)&gt;&gt;, float)](Unit/ChargePattern.md) |  | 
| [ClearAccelVectorFunc()](Unit/ClearAccelVectorFunc.md) |  | 
| [ClearAnimQueue()](Unit/ClearAnimQueue.md) |  | 
| [ClearAutoRotateSpeedFunc()](Unit/ClearAutoRotateSpeedFunc.md) |  | 
| [ClearCoreLookFunc()](Unit/ClearCoreLookFunc.md) |  | 
| [ClearCoreLookSpeed()](Unit/ClearCoreLookSpeed.md) |  | 
| [ClearFacingLerpSpeedFunc()](Unit/ClearFacingLerpSpeedFunc.md) |  | 
| [ClearFacingModeFunc()](Unit/ClearFacingModeFunc.md) |  | 
| [ClearMovementModeFunc()](Unit/ClearMovementModeFunc.md) |  | 
| [ClearPosLerpSpeedFunc()](Unit/ClearPosLerpSpeedFunc.md) |  | 
| [ClearTargetFacingAngleFunc()](Unit/ClearTargetFacingAngleFunc.md) |  | 
| [ClearTargetPosFunc()](Unit/ClearTargetPosFunc.md) |  | 
| [DestroyPart(String)](Unit/DestroyPart.md) |  | 
| [DestroyPixels(String, ScriptFunc&lt;[int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)&gt;)](Unit/DestroyPixels.md) |  | 
| [Disable()](Unit/Disable.md) |  | 
| [DisconnectPixelChunk(IntRange)](Unit/DisconnectPixelChunk.md) |  | 
| [DisconnectPixels(String)](Unit/DisconnectPixels.md) |  | 
| [DoesPartExist(String)](Unit/DoesPartExist.md) |  | 
| [DoesPixelExist(int)](Unit/DoesPixelExist.md) |  | 
| [Flash(Color, float, EasingType, float)](Unit/Flash.md) |  | 
| [FlashEdgePixels(String, Color, float, EasingType, bool, bool)](Unit/FlashEdgePixels.md) |  | 
| [FlashPart(String, Color, float, float, EasingType, CoreColorType)](Unit/FlashPart.md) |  | 
| [FlashPixel(int, Color, float, EasingType)](Unit/FlashPixel.md) |  | 
| [FlashPixels(IntRange, Color, float, EasingType)](Unit/FlashPixels.md) |  | 
| [ForcePixelConnectionCheck()](Unit/ForcePixelConnectionCheck.md) |  | 
| [GetLaserAngle(String, int)](Unit/GetLaserAngle.md) |  | 
| [GetNumParts(String, bool)](Unit/GetNumParts.md) |  | 
| [GetNumReqs(String, bool)](Unit/GetNumReqs.md) |  | 
| [GetPart(String, int)](Unit/GetPart.md) |  | 
| [GetPartPos(String, int)](Unit/GetPartPos.md) |  | 
| [GetPixel(int)](Unit/GetPixel.md) |  | 
| [GetPixel(Vector2, bool)](Unit/GetPixel.md) |  | 
| [GetRandomPixel()](Unit/GetRandomPixel.md) |  | 
| [HealParts(String, float)](Unit/HealParts.md) |  | 
| [HealPixels(String, float)](Unit/HealPixels.md) |  | 
| [Implode()](Unit/Implode.md) |  | 
| [Look(String, Vector2, float, float, float, float)](Unit/Look.md) |  | 
| [Nudge(Vector2, float, EasingType)](Unit/Nudge.md) |  | 
| [PixelBoundsContainsPos(Vector2)](Unit/PixelBoundsContainsPos.md) |  | 
| [PlayAnim(String, bool, bool, LoopMode, EasingType, bool)](Unit/PlayAnim.md) |  | 
| [Raycast(Vector2, Vector2, bool, bool)](Unit/Raycast.md) |  | 
| [RefreshEdgePixelColor(String, bool, bool)](Unit/RefreshEdgePixelColor.md) |  | 
| [RemovePixels(IntRange)](Unit/RemovePixels.md) |  | 
| [RemoveSpeechBubbles(String, PartSelectMode)](Unit/RemoveSpeechBubbles.md) |  | 
| [RemoveSpeechBubbles()](Unit/RemoveSpeechBubbles.md) |  | 
| [RepulsionCirclesContainPos(Vector2)](Unit/RepulsionCirclesContainPos.md) |  | 
| [Respawn(float, float, int)](Unit/Respawn.md) |  | 
| [Respawn(String, float, float, int)](Unit/Respawn.md) |  | 
| [Rotate180Degrees(float, EasingType)](Unit/Rotate180Degrees.md) |  | 
| [RotateClockwise(float, EasingType)](Unit/RotateClockwise.md) |  | 
| [RotateClockwiseOnlyDiagonal(float, EasingType)](Unit/RotateClockwiseOnlyDiagonal.md) |  | 
| [RotateCounterClockwise(float, EasingType)](Unit/RotateCounterClockwise.md) |  | 
| [RotateCounterClockwiseOnlyDiagonal(float, EasingType)](Unit/RotateCounterClockwiseOnlyDiagonal.md) |  | 
| [RotateToFace(Direction, float, EasingType)](Unit/RotateToFace.md) |  | 
| [ScriptFuncParamTest(ScriptFunc&lt;[String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.5)&gt;)](Unit/ScriptFuncParamTest.md) |  | 
| [SelectPart(String, PartSelectMode)](Unit/SelectPart.md) |  | 
| [SetAccelVectorFunc(ScriptFunc&lt;[Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html)&gt;)](Unit/SetAccelVectorFunc.md) |  | 
| [SetAnimSpeed(float)](Unit/SetAnimSpeed.md) |  | 
| [SetAutoRotateSpeedFunc(ScriptFunc&lt;[float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5)&gt;)](Unit/SetAutoRotateSpeedFunc.md) |  | 
| [SetAvoidUnitStrength(float)](Unit/SetAvoidUnitStrength.md) |  | 
| [SetBehaviour(DataPath&lt;[FsmData](FsmData.md)&gt;)](Unit/SetBehaviour.md) |  | 
| [SetColorBlinkTimes(String, float, float, EasingType)](Unit/SetColorBlinkTimes.md) |  | 
| [SetCoreLookFunc(ScriptFunc&lt;[Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html)&gt;)](Unit/SetCoreLookFunc.md) |  | 
| [SetCoreLookSpeed(float)](Unit/SetCoreLookSpeed.md) |  | 
| [SetDormant(bool)](Unit/SetDormant.md) |  | 
| [SetEdgePixelColor(String, Color, bool, bool)](Unit/SetEdgePixelColor.md) |  | 
| [SetEdgePixelOriginalType(bool, bool)](Unit/SetEdgePixelOriginalType.md) |  | 
| [SetEdgePixelType(PixelType, bool, bool)](Unit/SetEdgePixelType.md) |  | 
| [SetFacingAngle(float)](Unit/SetFacingAngle.md) |  | 
| [SetFacingDirection(Direction)](Unit/SetFacingDirection.md) |  | 
| [SetFacingLerpSpeedFunc(ScriptFunc&lt;[float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5)&gt;)](Unit/SetFacingLerpSpeedFunc.md) |  | 
| [SetFacingModeFunc(ScriptFunc&lt;[UnitFacingMode](UnitFacingMode.md)&gt;)](Unit/SetFacingModeFunc.md) |  | 
| [SetHidden(bool, float)](Unit/SetHidden.md) |  | 
| [SetInvulnerable(bool)](Unit/SetInvulnerable.md) |  | 
| [SetLaserActive(String, bool)](Unit/SetLaserActive.md) |  | 
| [SetLaserAimSpeed(String, float)](Unit/SetLaserAimSpeed.md) |  | 
| [SetLaserAnimSpeeds(String, float, float)](Unit/SetLaserAnimSpeeds.md) |  | 
| [SetLaserAutoRotate(String, bool)](Unit/SetLaserAutoRotate.md) |  | 
| [SetLaserAutoRotateSpeed(String, float)](Unit/SetLaserAutoRotateSpeed.md) |  | 
| [SetLaserDangerous(String, bool)](Unit/SetLaserDangerous.md) |  | 
| [SetLaserDps(String, float)](Unit/SetLaserDps.md) |  | 
| [SetLaserLength(String, float)](Unit/SetLaserLength.md) |  | 
| [SetLaserLengthLerpSpeed(String, float)](Unit/SetLaserLengthLerpSpeed.md) |  | 
| [SetLaserOffColors(String, Color, Color)](Unit/SetLaserOffColors.md) |  | 
| [SetLaserOnColors(String, Color, Color)](Unit/SetLaserOnColors.md) |  | 
| [SetLaserTargetAngle(String, float)](Unit/SetLaserTargetAngle.md) |  | 
| [SetLaserWidths(String, float, float, float, float)](Unit/SetLaserWidths.md) |  | 
| [SetLookTarget(String, Vector2, float)](Unit/SetLookTarget.md) |  | 
| [SetMovementModeFunc(ScriptFunc&lt;[UnitMovementMode](UnitMovementMode.md)&gt;)](Unit/SetMovementModeFunc.md) |  | 
| [SetOpacity(float)](Unit/SetOpacity.md) |  | 
| [SetPixelColors(IntRange, Color)](Unit/SetPixelColors.md) |  | 
| [SetPosition(Vector2)](Unit/SetPosition.md) |  | 
| [SetPosLerpSpeedFunc(ScriptFunc&lt;[float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5)&gt;)](Unit/SetPosLerpSpeedFunc.md) |  | 
| [SetRepelUnitStrength(float)](Unit/SetRepelUnitStrength.md) |  | 
| [SetRotationForce(float)](Unit/SetRotationForce.md) |  | 
| [SetScale(Vector2)](Unit/SetScale.md) |  | 
| [SetShaderDepthX(float)](Unit/SetShaderDepthX.md) |  | 
| [SetShaderDepthY(float)](Unit/SetShaderDepthY.md) |  | 
| [SetShaderFreqX(float)](Unit/SetShaderFreqX.md) |  | 
| [SetShaderFreqY(float)](Unit/SetShaderFreqY.md) |  | 
| [SetShaderIntensity(float)](Unit/SetShaderIntensity.md) |  | 
| [SetShaderSpeedX(float)](Unit/SetShaderSpeedX.md) |  | 
| [SetShaderSpeedY(float)](Unit/SetShaderSpeedY.md) |  | 
| [SetShaderTimeFactor1(float)](Unit/SetShaderTimeFactor1.md) |  | 
| [SetShaderTimeFactor2(float)](Unit/SetShaderTimeFactor2.md) |  | 
| [SetShaderTimeFactor3(float)](Unit/SetShaderTimeFactor3.md) |  | 
| [SetState(String)](Unit/SetState.md) |  | 
| [SetTargetFacingAngleFunc(ScriptFunc&lt;[float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5)&gt;)](Unit/SetTargetFacingAngleFunc.md) |  | 
| [SetTargetPosFunc(ScriptFunc&lt;[Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html)&gt;)](Unit/SetTargetPosFunc.md) |  | 
| [SetVelocity(Vector2)](Unit/SetVelocity.md) |  | 
| [Shake(float, float, EasingType)](Unit/Shake.md) |  | 
| [SpawnBubble(LocalizedString, String, PartSelectMode, float, Func&lt;[Color](https://docs.unity3d.com/ScriptReference/Color.html)&gt;, Func&lt;[Color](https://docs.unity3d.com/ScriptReference/Color.html)&gt;, Func&lt;[float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5)&gt;, Func&lt;[Color](https://docs.unity3d.com/ScriptReference/Color.html)&gt;, FloatingTextFont, int)](Unit/SpawnBubble.md) |  | 
| [SpawnNextForm()](Unit/SpawnNextForm.md) |  | 
| [StopChargingPatterns(String, String)](Unit/StopChargingPatterns.md) |  | 
| [StopPatterns(String, String)](Unit/StopPatterns.md) |  | 
| [StopRespawning(String)](Unit/StopRespawning.md) |  | 
| [TintPixels(IntRange, Color)](Unit/TintPixels.md) |  | 
| [ToggleHidden(float)](Unit/ToggleHidden.md) |  | 
| [ToggleLaserActive(String)](Unit/ToggleLaserActive.md) |  | 
| [ToggleLaserDangerous(String)](Unit/ToggleLaserDangerous.md) |  | 
| [Twist(float, float, EasingType)](Unit/Twist.md) |  | 

</div>

