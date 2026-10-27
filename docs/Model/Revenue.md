# Revenue

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**currency** | **string** | ISO 4217 code of the currency of the revenue. |
**license_count** | **int** | Number of licenses sold in the currency, free ones included, canceled ones left out. |
**total** | **float** | Sum of the prices of the licenses sold in the currency, in major units, canceled ones left out. |
**canceled_license_count** | **int** | Number of canceled licenses sold in the currency. |
**canceled_total** | **float** | Sum of the prices of the canceled licenses sold in the currency, in major units: revenue lost to cancellations. |
**this_month** | **float** | Revenue of the current month, in UTC. |
**last_month** | **float** | Revenue of the previous month, in UTC. |
**last30_days** | **float** | Revenue of the last 30 days, today included, in UTC. |
**by_day** | **float[]** | Revenue each day, aligned on &#x60;days&#x60;. |
**by_month** | **float[]** | Revenue each month, aligned on &#x60;months&#x60;. |
**by_policy** | [**\LicenseManager\Model\ProductStatsNewLicensesByPolicyInner[]**](ProductStatsNewLicensesByPolicyInner.md) | Revenue of the licenses of each policy, for the policies with licenses sold in the currency over the covered months. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
