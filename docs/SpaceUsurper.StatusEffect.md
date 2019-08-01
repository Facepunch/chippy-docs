# SpaceUsurper.StatusEffect
## Properties
| Type | Name | Get Set |
| ---: | ---- | :-----: |
| [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) | Charge | get, set |
| [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) | ChargePercent | get, set |
| [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) | ChargeRequired | get, set |
| [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) | ElapsedTime | get, set |
| [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) | IsSelected | get, set |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | Level | get, set |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | NumLevels | get, set |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | NumStatusBullets | get |
## Methods
| Return Type | Name | Parameters |
| ----------: | ---- | ---------- |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | Activate | |
| [Bullet](SpaceUsurper.Bullet.md) | AddBullet | [DataPath](SpaceUsurper.DataPath.md)&lt;[BulletData](SpaceUsurper.BulletData.md)&gt; *path*, [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *pos*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *angle*, [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *addVelocity*, [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) *mirrorBulletAngles*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *sizeMultiplier*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *opacityMultiplier*, [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *level*|
| [PlayerGun](SpaceUsurper.PlayerGun.md) | AddGun | [DataPath](SpaceUsurper.DataPath.md)&lt;[PlayerGunData](SpaceUsurper.PlayerGunData.md)&gt; *path*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *angle*, [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *level*|
| [BulletPattern](SpaceUsurper.BulletPattern.md) | AddPattern | [DataPath](SpaceUsurper.DataPath.md)&lt;[PatternData](SpaceUsurper.PatternData.md)&gt; *path*, [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *pos*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *angle*, [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) *mirrorPatternRotation*, [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) *mirrorBulletAngles*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *sizeMultiplier*, [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *loopNum*, [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *level*, [DataPath](SpaceUsurper.DataPath.md)&lt;[StatusEffectData](SpaceUsurper.StatusEffectData.md)&gt;[] *statusPaths*, [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5)[] *statusIndices*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | ClearCharge | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | DespawnAddedBullets | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | DespawnAddedPatterns | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | DespawnFirstBullet | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | DespawnGuns | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | DespawnLastBullet | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | Disable | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | Execute | |
| [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) | LevelDown | [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *count*|
| [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) | LevelUp | [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) *count*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | NoLongerSelectable | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | SetCharge | [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *charge*|
