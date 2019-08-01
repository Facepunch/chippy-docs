# SpaceUsurper.MovementController
## Properties
| Type | Name | Get Set |
| ---: | ---- | :-----: |
| [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) | Position | get, set |
| [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) | Velocity | get, set |
| [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) | VelocityPercent | get |
## Methods
| Return Type | Name | Parameters |
| ----------: | ---- | ---------- |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | AddForce | [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *force*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | AddPhysicsForce | [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.5) *name*, [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *force*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | AddVelocity | [Vector2](https://docs.unity3d.com/ScriptReference/Vector2.html) *vel*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | ClearPhysics | |
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | SetAcceleration | [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *acceleration*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | SetFrictionPercentMax | [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *frictionPercentMax*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | SetFrictionPercentMin | [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *frictionPercentMin*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | SetMass | [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *mass*|
| [void](https://docs.microsoft.com/en-us/dotnet/api/system.void?view=netframework-4.5) | SetTopSpeed | [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *topSpeed*|
