# SpaceUsurper.BulletPattern
## Properties
| Type | Name | Get Set |
| ---: | ---- | :-----: |
| [Rotation](SpaceUsurper.Rotation.md) | CurrentAngle | get, set |
| [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) | ElapsedTime | get, set |
| [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) | IsActive | get, set |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | Level | get, set |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | LoopNum | get, set |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | NumChildBullets | get |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | NumShotPatternsConstant | get, set |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | NumSpawnedPatternsConstant | get, set |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | NumVolleys | get, set |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | PatternNum | get, set |
| [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) | PatternProgress | get, set |
| [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) | Position | get, set |
| [PatternShape](SpaceUsurper.PatternShape.md) | Shape | get, set |
## Methods
| Return Type | Name | Parameters |
| ----------: | ---- | ---------- |
| [Bullet](SpaceUsurper.Bullet.md) | AddBullet | [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *pos*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *angle*, [DataPath](SpaceUsurper.DataPath.md)&lt;[BulletData](SpaceUsurper.BulletData.md)&gt; *path*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *sizeMultiplier*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *simulateTime*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | AffectBullets | [ActionList](SpaceUsurper.ActionList.md) *actions*, ParameterCollection *fsmParams*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | DespawnBulletAnchor | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | Finish | |
