# CreatePolicy

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**name** | **string** |  |
**slug** | **string** | Unique within the product. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. | [optional]
**is_default** | **bool** | &#x60;true&#x60; makes this policy the product&#39;s default, in place of the current one. | [optional]
**duration** | [**\LicenseManager\Model\PolicySettingsDuration**](PolicySettingsDuration.md) |  | [optional]
**max_machines** | **int** | Maximum number of active machines of the licenses created with this policy, copied to each of them. &#x60;null&#x60; for no limit. Defaults to &#x60;null&#x60;. | [optional]
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the licenses created with this policy, in seconds, copied to each of them. At least one hour (&#x60;3600&#x60;). Defaults to one week. | [optional]
**max_version** | [**\LicenseManager\Model\PolicySettingsMaxVersion**](PolicySettingsMaxVersion.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
