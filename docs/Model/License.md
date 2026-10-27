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
**cancellable_until** | **\DateTime** | End of the money back guarantee: until then, the customer can cancel the license from the customer portal, or with a token. Set from the policy&#39;s &#x60;moneyBackGuaranteeDays&#x60; when the license is created. &#x60;null&#x60; when the customer can&#39;t cancel it. |
**canceled_at** | **\DateTime** | When the license was canceled: validating its key fails since. &#x60;null&#x60; when it wasn&#39;t. |
**cancellation_reason** | [**\LicenseManagerModelCancellationReasonString**](\LicenseManagerModelCancellationReasonString.md) |  |
**cancellation_comment** | **string** | Comment given when the license was canceled. &#x60;null&#x60; when there&#39;s none. |
**stripe_refund_id** | **string** | Id of the Stripe refund of the license&#39;s payment once it was canceled, through the Stripe integration. &#x60;null&#x60; otherwise. |
**updated_at** | **\DateTime** | Last time the license&#39;s settings were edited, not when its key was validated. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
