# ProductStats

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**license_count** | **int** | Number of licenses of the product. |
**active_license_count** | **int** | Number of licenses that haven&#39;t expired, and that a machine validated in the last 90 days. |
**new_license_count** | **int** | Number of licenses created in the last 30 days, today included, in UTC. |
**expiring_license_count** | **int** | Number of licenses expiring in the next 30 days. |
**expired_license_count** | **int** | Number of licenses that expired in the last 30 days. |
**active_machine_count** | **int** | Number of active machines of the licenses of the product. |
**in_use_license_count** | **int** | Number of licenses with at least one active machine. |
**seat_count** | **int** | Sum of the maximum numbers of machines of the licenses that haven&#39;t expired. Licenses without a maximum are left out. |
**used_seat_count** | **int** | Number of active machines of the licenses counted in &#x60;seatCount&#x60;, at most their maximum number of machines each. |
**full_license_count** | **int** | Number of licenses counted in &#x60;seatCount&#x60; active on their maximum number of machines. |
**days** | **\DateTime[]** | The 30 days covered by the daily stats, from the oldest one, in UTC. |
**months** | **string[]** | The 12 months covered by the monthly stats, from the oldest one, in UTC. |
**new_licenses_by_day** | **int[]** | Number of licenses created each day, aligned on &#x60;days&#x60;. |
**new_licenses_by_month** | **int[]** | Number of licenses created each month, aligned on &#x60;months&#x60;. |
**new_licenses_by_policy** | [**\LicenseManager\Model\ProductStatsNewLicensesByPolicyInner[]**](ProductStatsNewLicensesByPolicyInner.md) | Number of licenses of each policy created each day and each month, for the policies with licenses created over the covered months. |
**revenue** | [**\LicenseManager\Model\Revenue[]**](Revenue.md) | Revenue in each currency licenses were sold in, from the one with the most licenses sold. Amounts aren&#39;t converted between currencies. |
**activations_by_version** | [**\LicenseManager\Model\ProductStatsActivationsByVersionInner[]**](ProductStatsActivationsByVersionInner.md) | Successful activations of the licenses of the product each day, per version of the application, from the most recent one. |
**active_machines_by_version** | [**\LicenseManager\Model\ProductStatsActiveMachinesByVersionInner[]**](ProductStatsActiveMachinesByVersionInner.md) | Number of active machines running each version of the application, from the most recent one. |
**active_machines_by_platform** | [**\LicenseManager\Model\ProductStatsActiveMachinesByPlatformInner[]**](ProductStatsActiveMachinesByPlatformInner.md) | Number of active machines on each platform, from the one with the most machines. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
