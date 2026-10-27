# Policy

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**product_id** | **string** |  |
**slug** | **string** |  |
**name** | **string** |  |
**is_default** | **bool** | Whether this is the product&#39;s default policy. Each product has exactly one. |
**duration** | [**\LicenseManager\Model\PolicyDuration**](PolicyDuration.md) |  |
**max_machines** | **int** | Maximum number of active machines of the licenses created with this policy. &#x60;null&#x60; when there&#39;s no limit. |
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the licenses created with this policy, in seconds. |
**max_version** | [**\LicenseManager\Model\PolicyMaxVersion**](PolicyMaxVersion.md) |  |
**money_back_guarantee_days** | **int** | Number of days after their creation during which customers can cancel the licenses created with this policy, from the customer portal or with &#x60;cancelLicense&#x60;. &#x60;null&#x60; when they can&#39;t. |
**license_count** | **int** | Number of licenses following this policy. |
**created_at** | **\DateTime** |  |
**updated_at** | **\DateTime** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
