# IntegrationMapping

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**integration_id** | **string** |  |
**product_id** | **string** |  |
**policy_id** | **string** |  |
**stripe_product_id** | **string** |  |
**stripe_price_id** | **string** |  |
**product_name** | **string** | Name of the Stripe product when it was mapped. |
**price** | [**\LicenseManager\Model\Price**](Price.md) |  |
**recurring** | [**\LicenseManager\Model\IntegrationMappingRecurring**](IntegrationMappingRecurring.md) |  |
**status** | **string** | &#x60;error&#x60; when the price can no longer be paid, explained by &#x60;statusReason&#x60;. |
**status_reason** | **string** |  |
**created_at** | **\DateTime** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
