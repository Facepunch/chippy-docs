# SpaceUsurper.ProgressionManager
## Methods
| Return Type | Name | Parameters |
| ----------: | ---- | ---------- |
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | GetAttempts | [StageID](SpaceUsurper.StageID.md) *stageId*|
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | GetCompletedCount | [DataPath](SpaceUsurper.DataPath.md)&lt;[CampaignData](SpaceUsurper.CampaignData.md)&gt; *campaignPath*|
| [Medal](SpaceUsurper.Medal.md) | GetMedal | [StageID](SpaceUsurper.StageID.md) *stageId*|
| [Medal](SpaceUsurper.Medal.md) | GetMedal | [StageID](SpaceUsurper.StageID.md) *stageId*, [float](https://docs.microsoft.com/en-us/dotnet/api/system.single?view=netframework-4.5) *timeSeconds*|
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | GetMedalCount | [DataPath](SpaceUsurper.DataPath.md)&lt;[CampaignData](SpaceUsurper.CampaignData.md)&gt; *campaignPath*, [Medal](SpaceUsurper.Medal.md) *medal*|
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | GetStageCount | [DataPath](SpaceUsurper.DataPath.md)&lt;[CampaignData](SpaceUsurper.CampaignData.md)&gt; *campaignPath*|
| [int](https://docs.microsoft.com/en-us/dotnet/api/system.int32?view=netframework-4.5) | GetVictories | [StageID](SpaceUsurper.StageID.md) *stageId*|
| [bool](https://docs.microsoft.com/en-us/dotnet/api/system.boolean?view=netframework-4.5) | IsLevelCompleted | [StageID](SpaceUsurper.StageID.md) *stageId*|
