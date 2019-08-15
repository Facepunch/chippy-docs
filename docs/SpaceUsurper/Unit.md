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
| [AddPattern(DataPath&lt;PatternData&gt;, Vector2, Single, Boolean, Boolean, Single, Int32, Int32)](Unit/AddPattern.md) |  | 
| [AddRotationForce(Vector2, Vector2, Single)](Unit/AddRotationForce.md) |  | 
| [AddTimeScale(Single, Single, EasingType)](Unit/AddTimeScale.md) |  | 
| [AddVelocity(Vector2)](Unit/AddVelocity.md) |  | 
| [AdjustPartCounter(String, Int32)](Unit/AdjustPartCounter.md) |  | 
| [AimTowards(Single, Single)](Unit/AimTowards.md) |  | 
| [CalculateBaseFormProgress(Int32)](Unit/CalculateBaseFormProgress.md) |  | 
| [CancelRotateToFace()](Unit/CancelRotateToFace.md) |  | 
| [ChargePattern(DataPath&lt;PatternData&gt;[], Int32, String, PartSelectMode, Single, MirrorMode, FlipPatternMode, Single, ScriptFunc&lt;Vector2&gt;, Single, Int32, Int32, Single, Int32, Int32, List&lt;DataPath&lt;StatusEffectData&gt;&gt;, Single)](Unit/ChargePattern.md) |  | 
| [ChargePattern(DataPath&lt;PatternData&gt;, String, PartSelectMode, Single, MirrorMode, FlipPatternMode, Single, ScriptFunc&lt;Vector2&gt;, Single, Int32, Int32, Single, Int32, Int32, List&lt;DataPath&lt;StatusEffectData&gt;&gt;, Single)](Unit/ChargePattern.md) |  | 
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
| [DestroyPixels(String, ScriptFunc&lt;Int32&gt;)](Unit/DestroyPixels.md) |  | 
| [Disable()](Unit/Disable.md) |  | 
| [DisconnectPixelChunk(IntRange)](Unit/DisconnectPixelChunk.md) |  | 
| [DisconnectPixels(String)](Unit/DisconnectPixels.md) |  | 
| [DoesPartExist(String)](Unit/DoesPartExist.md) |  | 
| [DoesPixelExist(Int32)](Unit/DoesPixelExist.md) |  | 
| [Flash(Color, Single, EasingType, Single)](Unit/Flash.md) |  | 
| [FlashEdgePixels(String, Color, Single, EasingType, Boolean, Boolean)](Unit/FlashEdgePixels.md) |  | 
| [FlashPart(String, Color, Single, Single, EasingType, CoreColorType)](Unit/FlashPart.md) |  | 
| [FlashPixel(Int32, Color, Single, EasingType)](Unit/FlashPixel.md) |  | 
| [FlashPixels(IntRange, Color, Single, EasingType)](Unit/FlashPixels.md) |  | 
| [ForcePixelConnectionCheck()](Unit/ForcePixelConnectionCheck.md) |  | 
| [GetLaserAngle(String, Int32)](Unit/GetLaserAngle.md) |  | 
| [GetNumParts(String, Boolean)](Unit/GetNumParts.md) |  | 
| [GetNumReqs(String, Boolean)](Unit/GetNumReqs.md) |  | 
| [GetPart(String, Int32)](Unit/GetPart.md) |  | 
| [GetPartPos(String, Int32)](Unit/GetPartPos.md) |  | 
| [GetPixel(Int32)](Unit/GetPixel.md) |  | 
| [GetPixel(Vector2, Boolean)](Unit/GetPixel.md) |  | 
| [GetRandomPixel()](Unit/GetRandomPixel.md) |  | 
| [HealParts(String, Single)](Unit/HealParts.md) |  | 
| [HealPixels(String, Single)](Unit/HealPixels.md) |  | 
| [Implode()](Unit/Implode.md) |  | 
| [Look(String, Vector2, Single, Single, Single, Single)](Unit/Look.md) |  | 
| [Nudge(Vector2, Single, EasingType)](Unit/Nudge.md) |  | 
| [PixelBoundsContainsPos(Vector2)](Unit/PixelBoundsContainsPos.md) |  | 
| [PlayAnim(String, Boolean, Boolean, LoopMode, EasingType, Boolean)](Unit/PlayAnim.md) |  | 
| [Raycast(Vector2, Vector2, Boolean, Boolean)](Unit/Raycast.md) |  | 
| [RefreshEdgePixelColor(String, Boolean, Boolean)](Unit/RefreshEdgePixelColor.md) |  | 
| [RemovePixels(IntRange)](Unit/RemovePixels.md) |  | 
| [RemoveSpeechBubbles(String, PartSelectMode)](Unit/RemoveSpeechBubbles.md) |  | 
| [RemoveSpeechBubbles()](Unit/RemoveSpeechBubbles.md) |  | 
| [RepulsionCirclesContainPos(Vector2)](Unit/RepulsionCirclesContainPos.md) |  | 
| [Respawn(Single, Single, Int32)](Unit/Respawn.md) |  | 
| [Respawn(String, Single, Single, Int32)](Unit/Respawn.md) |  | 
| [Rotate180Degrees(Single, EasingType)](Unit/Rotate180Degrees.md) |  | 
| [RotateClockwise(Single, EasingType)](Unit/RotateClockwise.md) |  | 
| [RotateClockwiseOnlyDiagonal(Single, EasingType)](Unit/RotateClockwiseOnlyDiagonal.md) |  | 
| [RotateCounterClockwise(Single, EasingType)](Unit/RotateCounterClockwise.md) |  | 
| [RotateCounterClockwiseOnlyDiagonal(Single, EasingType)](Unit/RotateCounterClockwiseOnlyDiagonal.md) |  | 
| [RotateToFace(Direction, Single, EasingType)](Unit/RotateToFace.md) |  | 
| [ScriptFuncParamTest(ScriptFunc&lt;String&gt;)](Unit/ScriptFuncParamTest.md) |  | 
| [SelectPart(String, PartSelectMode)](Unit/SelectPart.md) |  | 
| [SetAccelVectorFunc(ScriptFunc&lt;Vector2&gt;)](Unit/SetAccelVectorFunc.md) |  | 
| [SetAnimSpeed(Single)](Unit/SetAnimSpeed.md) |  | 
| [SetAutoRotateSpeedFunc(ScriptFunc&lt;Single&gt;)](Unit/SetAutoRotateSpeedFunc.md) |  | 
| [SetAvoidUnitStrength(Single)](Unit/SetAvoidUnitStrength.md) |  | 
| [SetBehaviour(DataPath&lt;FsmData&gt;)](Unit/SetBehaviour.md) |  | 
| [SetColorBlinkTimes(String, Single, Single, EasingType)](Unit/SetColorBlinkTimes.md) |  | 
| [SetCoreLookFunc(ScriptFunc&lt;Vector2&gt;)](Unit/SetCoreLookFunc.md) |  | 
| [SetCoreLookSpeed(Single)](Unit/SetCoreLookSpeed.md) |  | 
| [SetDormant(Boolean)](Unit/SetDormant.md) |  | 
| [SetEdgePixelColor(String, Color, Boolean, Boolean)](Unit/SetEdgePixelColor.md) |  | 
| [SetEdgePixelOriginalType(Boolean, Boolean)](Unit/SetEdgePixelOriginalType.md) |  | 
| [SetEdgePixelType(PixelType, Boolean, Boolean)](Unit/SetEdgePixelType.md) |  | 
| [SetFacingAngle(Single)](Unit/SetFacingAngle.md) |  | 
| [SetFacingDirection(Direction)](Unit/SetFacingDirection.md) |  | 
| [SetFacingLerpSpeedFunc(ScriptFunc&lt;Single&gt;)](Unit/SetFacingLerpSpeedFunc.md) |  | 
| [SetFacingModeFunc(ScriptFunc&lt;UnitFacingMode&gt;)](Unit/SetFacingModeFunc.md) |  | 
| [SetHidden(Boolean, Single)](Unit/SetHidden.md) |  | 
| [SetInvulnerable(Boolean)](Unit/SetInvulnerable.md) |  | 
| [SetLaserActive(String, Boolean)](Unit/SetLaserActive.md) |  | 
| [SetLaserAimSpeed(String, Single)](Unit/SetLaserAimSpeed.md) |  | 
| [SetLaserAnimSpeeds(String, Single, Single)](Unit/SetLaserAnimSpeeds.md) |  | 
| [SetLaserAutoRotate(String, Boolean)](Unit/SetLaserAutoRotate.md) |  | 
| [SetLaserAutoRotateSpeed(String, Single)](Unit/SetLaserAutoRotateSpeed.md) |  | 
| [SetLaserDangerous(String, Boolean)](Unit/SetLaserDangerous.md) |  | 
| [SetLaserDps(String, Single)](Unit/SetLaserDps.md) |  | 
| [SetLaserLength(String, Single)](Unit/SetLaserLength.md) |  | 
| [SetLaserLengthLerpSpeed(String, Single)](Unit/SetLaserLengthLerpSpeed.md) |  | 
| [SetLaserOffColors(String, Color, Color)](Unit/SetLaserOffColors.md) |  | 
| [SetLaserOnColors(String, Color, Color)](Unit/SetLaserOnColors.md) |  | 
| [SetLaserTargetAngle(String, Single)](Unit/SetLaserTargetAngle.md) |  | 
| [SetLaserWidths(String, Single, Single, Single, Single)](Unit/SetLaserWidths.md) |  | 
| [SetLookTarget(String, Vector2, Single)](Unit/SetLookTarget.md) |  | 
| [SetMovementModeFunc(ScriptFunc&lt;UnitMovementMode&gt;)](Unit/SetMovementModeFunc.md) |  | 
| [SetOpacity(Single)](Unit/SetOpacity.md) |  | 
| [SetPixelColors(IntRange, Color)](Unit/SetPixelColors.md) |  | 
| [SetPosition(Vector2)](Unit/SetPosition.md) |  | 
| [SetPosLerpSpeedFunc(ScriptFunc&lt;Single&gt;)](Unit/SetPosLerpSpeedFunc.md) |  | 
| [SetRepelUnitStrength(Single)](Unit/SetRepelUnitStrength.md) |  | 
| [SetRotationForce(Single)](Unit/SetRotationForce.md) |  | 
| [SetScale(Vector2)](Unit/SetScale.md) |  | 
| [SetShaderDepthX(Single)](Unit/SetShaderDepthX.md) |  | 
| [SetShaderDepthY(Single)](Unit/SetShaderDepthY.md) |  | 
| [SetShaderFreqX(Single)](Unit/SetShaderFreqX.md) |  | 
| [SetShaderFreqY(Single)](Unit/SetShaderFreqY.md) |  | 
| [SetShaderIntensity(Single)](Unit/SetShaderIntensity.md) |  | 
| [SetShaderSpeedX(Single)](Unit/SetShaderSpeedX.md) |  | 
| [SetShaderSpeedY(Single)](Unit/SetShaderSpeedY.md) |  | 
| [SetShaderTimeFactor1(Single)](Unit/SetShaderTimeFactor1.md) |  | 
| [SetShaderTimeFactor2(Single)](Unit/SetShaderTimeFactor2.md) |  | 
| [SetShaderTimeFactor3(Single)](Unit/SetShaderTimeFactor3.md) |  | 
| [SetState(String)](Unit/SetState.md) |  | 
| [SetTargetFacingAngleFunc(ScriptFunc&lt;Single&gt;)](Unit/SetTargetFacingAngleFunc.md) |  | 
| [SetTargetPosFunc(ScriptFunc&lt;Vector2&gt;)](Unit/SetTargetPosFunc.md) |  | 
| [SetVelocity(Vector2)](Unit/SetVelocity.md) |  | 
| [Shake(Single, Single, EasingType)](Unit/Shake.md) |  | 
| [SpawnBubble(LocalizedString, String, PartSelectMode, Single, Func&lt;Color&gt;, Func&lt;Color&gt;, Func&lt;Single&gt;, Func&lt;Color&gt;, FloatingTextFont, Int32)](Unit/SpawnBubble.md) |  | 
| [SpawnNextForm()](Unit/SpawnNextForm.md) |  | 
| [StopChargingPatterns(String, String)](Unit/StopChargingPatterns.md) |  | 
| [StopPatterns(String, String)](Unit/StopPatterns.md) |  | 
| [StopRespawning(String)](Unit/StopRespawning.md) |  | 
| [TintPixels(IntRange, Color)](Unit/TintPixels.md) |  | 
| [ToggleHidden(Single)](Unit/ToggleHidden.md) |  | 
| [ToggleLaserActive(String)](Unit/ToggleLaserActive.md) |  | 
| [ToggleLaserDangerous(String)](Unit/ToggleLaserDangerous.md) |  | 
| [Twist(Single, Single, EasingType)](Unit/Twist.md) |  | 

</div>

