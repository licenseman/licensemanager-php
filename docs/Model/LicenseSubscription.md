# LicenseSubscription

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**provider** | **string** | Provider of the subscription. |
**external_id** | **string** | Id of the subscription in the provider: &#x60;sub_…&#x60; in Stripe and in Paddle. |
**stripe_subscription_id** | **string** | Deprecated: use &#x60;externalId&#x60;, which it equals. |
**status** | **string** | Status of the subscription in the provider. Stripe: &#x60;active&#x60;, &#x60;trialing&#x60;, &#x60;past_due&#x60; while a failed payment is retried, &#x60;canceled&#x60;, &#x60;unpaid&#x60;, &#x60;paused&#x60;, &#x60;incomplete&#x60; or &#x60;incomplete_expired&#x60;. Paddle: &#x60;active&#x60;, &#x60;trialing&#x60;, &#x60;past_due&#x60;, &#x60;paused&#x60; or &#x60;canceled&#x60;. |
**interval** | **string** |  |
**interval_count** | **int** | Number of intervals between payments. |
**quantity** | **int** | Units subscribed, multiplying the policy&#39;s machines. |
**price** | [**\LicenseManager\Model\Price**](Price.md) | Price of one unit for one period, before taxes. |
**current_period_end** | **\DateTime** | End of the paid period, when the subscription renews or ends. |
**cancel_at_period_end** | **bool** | Whether the subscription ends at the end of the period. |
**ended_at** | **\DateTime** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
