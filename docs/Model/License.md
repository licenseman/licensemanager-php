# License

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**product_id** | **string** |  |
**policy_id** | **string** |  |
**customer_id** | **string** |  |
**key** | **string** | Unique within the product. Case sensitive: &#x60;validateKey&#x60; compares keys exactly. |
**created_at** | **\DateTime** |  |
**expires_at** | **\DateTime** | &#x60;null&#x60; when the license never expires. |
**meta** | **array<string,mixed>** | Free-form JSON object. |
**stripe_payment_intent_id** | **string** | Id of the Stripe payment intent that paid the license, when it was bought through the Stripe integration. &#x60;null&#x60; otherwise, or when nothing was paid. |
**max_machines** | **int** | Maximum number of active machines the license can be used on. &#x60;null&#x60; when there&#39;s no limit. Can be lower than &#x60;activeMachineCount&#x60; after it was lowered: machines aren&#39;t deactivated to match it. |
**max_offline_duration_seconds** | **int** | Longest the applications can run offline with the license: the license tokens returned by &#x60;validateKey&#x60; expire this long after they&#39;re issued, unless the license expires sooner. |
**active_machine_count** | **int** | Number of active machines the license is used on. |
**last_activated_at** | **\DateTime** | Last time a machine validated the license key. &#x60;null&#x60; when it was never validated. |
**max_version** | [**\LicenseManager\Model\LicenseMaxVersion**](LicenseMaxVersion.md) |  |
**price** | [**\LicenseManager\Model\Price**](Price.md) |  |
**status** | [**\LicenseManager\Model\LicenseStatus**](LicenseStatus.md) |  |
**updated_at** | **\DateTime** | Last time the license&#39;s settings were edited, not when its key was validated. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
