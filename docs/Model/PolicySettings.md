# PolicySettings

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**duration** | [**\LicenseManager\Model\PolicySettingsDuration**](PolicySettingsDuration.md) |  | [optional]
**max_machines** | **int** | Maximum number of active machines of the licenses created with this policy, copied to each of them. &#x60;null&#x60; for no limit. Defaults to &#x60;null&#x60;. | [optional]
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the licenses created with this policy, in seconds, copied to each of them. At least one hour (&#x60;3600&#x60;). Defaults to one week. | [optional]
**max_version** | [**\LicenseManager\Model\PolicySettingsMaxVersion**](PolicySettingsMaxVersion.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
