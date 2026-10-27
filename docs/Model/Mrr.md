# Mrr

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**currency** | **string** |  |
**mrr** | **float** | Monthly recurring revenue: the price of every ongoing subscription in the currency, times its quantity, brought to one month (a year counts for a twelfth), before taxes and discounts. |
**by_interval** | [**\LicenseManager\Model\MrrByIntervalInner[]**](MrrByIntervalInner.md) | Ongoing subscriptions and MRR of each billing period, like monthly and yearly, from the highest MRR. |
**by_policy** | [**\LicenseManager\Model\MrrByPolicyInner[]**](MrrByPolicyInner.md) | MRR of each policy, from the highest. |
**by_month** | **float[]** | MRR at the end of each month, aligned on &#x60;months&#x60;, today for this month, at the current prices of the subscriptions. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
