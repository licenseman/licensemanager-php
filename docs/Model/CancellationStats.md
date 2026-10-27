# CancellationStats

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**license_count** | **int** | Number of licenses with a money back guarantee: a &#x60;cancellableUntil&#x60;. |
**canceled_license_count** | **int** | Number of them that were canceled. |
**cancellable_license_count** | **int** | Number of them whose money back guarantee hasn&#39;t ended, and that weren&#39;t canceled: they can still be. |
**rate** | **float** | Share of them that were canceled, from 0 to 1: &#x60;canceledLicenseCount&#x60; over &#x60;licenseCount&#x60;. |
**canceled_by_day** | **int[]** | Number of them canceled each day, aligned on &#x60;days&#x60;, on the day of their cancellation. |
**canceled_by_month** | **int[]** | Number of them canceled each month, aligned on &#x60;months&#x60;, on the month of their cancellation. |
**by_reason** | [**\LicenseManager\Model\CancellationStatsByReasonInner[]**](CancellationStatsByReasonInner.md) | Number of them canceled for each reason, from the most given one. Reasons never given are left out. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
