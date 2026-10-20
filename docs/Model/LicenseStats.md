# LicenseStats

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**from** | **\DateTime** | First day covered, in UTC. |
**to** | **\DateTime** | Last day covered, in UTC: today. |
**days** | **\DateTime[]** | The 90 days covered, from the oldest one, in UTC. |
**activations_by_machine** | [**\LicenseManager\Model\LicenseStatsActivationsByMachineInner[]**](LicenseStatsActivationsByMachineInner.md) | Machines that activated the license in the period, from the one with the most activations. |
**activations_by_version** | [**\LicenseManager\Model\LicenseStatsActivationsByVersionInner[]**](LicenseStatsActivationsByVersionInner.md) | Versions of the application that activated the license in the period, from the most recent one. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
