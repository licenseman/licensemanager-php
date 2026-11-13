# IntegrationMapping

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**integration_id** | **string** |  |
**provider** | **string** |  |
**product_id** | **string** |  |
**policy_id** | **string** |  |
**external_product_id** | **string** | Id of the product in the provider: &#x60;prod_…&#x60; in Stripe, &#x60;pro_…&#x60; in Paddle. |
**external_price_id** | **string** | Id of the price in the provider: &#x60;price_…&#x60; in Stripe, &#x60;pri_…&#x60; in Paddle. |
**stripe_product_id** | **string** | Deprecated: use &#x60;externalProductId&#x60;, which it equals. |
**stripe_price_id** | **string** | Deprecated: use &#x60;externalPriceId&#x60;, which it equals. |
**product_name** | **string** | Name of the provider&#39;s product when it was mapped. |
**price** | [**\LicenseManager\Model\Price**](Price.md) |  |
**recurring** | [**\LicenseManager\Model\IntegrationMappingRecurring**](IntegrationMappingRecurring.md) |  |
**status** | **string** | &#x60;error&#x60; when the price can no longer be paid, explained by &#x60;statusReason&#x60;. |
**status_reason** | **string** |  |
**created_at** | **\DateTime** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
