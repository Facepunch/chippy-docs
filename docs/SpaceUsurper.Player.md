# SpaceUsurper.Player
## Properties
| Type | Name | Get Set |
| ---: | ---- | :-----: |
| [Player_Body](SpaceUsurper.Player_Body.md) | Body | get, set |
| [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) | ChunkCenterOfMassPos | get, set |
| [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) | ChunkDisconnectPos | get, set |
| [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) | DamageBonus | get, set |
| [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) | DeathPercent | get, set |
| [Player_Guns](SpaceUsurper.Player_Guns.md) | GunHandler | get, set |
| [Player_Health](SpaceUsurper.Player_Health.md) | Health | get, set |
| [Player_Input](SpaceUsurper.Player_Input.md) | Input | get, set |
| [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) | IsDead | get, set |
| [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) | IsIntangible | get, set |
| [MovementController](SpaceUsurper.MovementController.md) | Movement | get, set |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | NumChunkPixels | get, set |
| [Player_StatusEffects](SpaceUsurper.Player_StatusEffects.md) | StatusEffectHandler | get, set |
| [Player_Vibration](SpaceUsurper.Player_Vibration.md) | VibrationHandler | get, set |
## Methods
| Return Type | Name | Parameters |
| ----------: | ---- | ---------- |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | AddForce | [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *force*|
| [PlayerGun](SpaceUsurper.PlayerGun.md) | AddGun | [DataPath](SpaceUsurper.DataPath.md)&lt;[PlayerGunData](SpaceUsurper.PlayerGunData.md)&gt; *path*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *angle*, [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *level*|
| [BulletPattern](SpaceUsurper.BulletPattern.md) | AddPattern | [DataPath](SpaceUsurper.DataPath.md)&lt;[PatternData](SpaceUsurper.PatternData.md)&gt; *path*, [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *pos*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *angle*, [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) *mirrorPatternRotation*, [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) *mirrorBulletAngles*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *sizeMultiplier*, [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *loopNum*, [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *level*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | AddPhysicsForce | [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.5) *name*, [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *force*|
| [StatusEffect](SpaceUsurper.StatusEffect.md) | AddStatus | [DataPath](SpaceUsurper.DataPath.md)&lt;[StatusEffectData](SpaceUsurper.StatusEffectData.md)&gt; *path*, [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *count*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | Damage | [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *direction*, [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) *applyForceWhenInvulnerable*, [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.5) *damageSourceName*|
| [StatusEffect](SpaceUsurper.StatusEffect.md) | GetStatus | [DataPath](SpaceUsurper.DataPath.md)&lt;[StatusEffectData](SpaceUsurper.StatusEffectData.md)&gt; *path*|
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | GetStatusLevel | [DataPath](SpaceUsurper.DataPath.md)&lt;[StatusEffectData](SpaceUsurper.StatusEffectData.md)&gt; *path*|
| [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) | IsStatusSelected | [DataPath](SpaceUsurper.DataPath.md)&lt;[StatusEffectData](SpaceUsurper.StatusEffectData.md)&gt; *path*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | KillPlayer | [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *dir*|
| [PlayerGun](SpaceUsurper.PlayerGun.md) | ReplaceMainGun | [DataPath](SpaceUsurper.DataPath.md)&lt;[PlayerGunData](SpaceUsurper.PlayerGunData.md)&gt; *path*, [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *level*|
| [PlayerGun](SpaceUsurper.PlayerGun.md) | RestoreDefaultMainGun | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | SetPosition | [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *pos*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | Vibrate | [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *pos*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *strength*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *maxDist*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *time*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *horizThreshold*, [EasingType](SpaceUsurper.EasingType.md) *easingType*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | Vibrate | [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *strength*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *time*, [EasingType](SpaceUsurper.EasingType.md) *easingType*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | Vibrate | [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *left*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *right*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *time*, [EasingType](SpaceUsurper.EasingType.md) *easingType*|
