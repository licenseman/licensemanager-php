# Event

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**type** | [**\LicenseManager\Model\EventType**](EventType.md) |  |
**created_at** | **\DateTime** |  |
**payload** | **array<string,mixed>** | Details of the event, depending on its &#x60;type&#x60;. |
**policy_id** | **string** |  |
**license_id** | **string** |  |
**machine_id** | **string** |  |
**machine** | [**\LicenseManager\Model\EventMachine**](EventMachine.md) |  |
**actor** | [**\LicenseManager\Model\EventActor**](EventActor.md) |  |
**country** | **string** | ISO 3166-1 alpha-2 code of the country of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |
**latitude** | **float** | Approximate latitude of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |
**longitude** | **float** | Approximate longitude of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
