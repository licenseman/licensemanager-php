# Customer

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**product_id** | **string** |  |
**email** | **string** |  |
**name** | **string** | Display name of the customer. &#x60;null&#x60; when unknown. |
**license_count** | **int** | Number of licenses of this customer. |
**stripe_customer_id** | **string** | Id of the Stripe customer, when the customer bought licenses through the Stripe integration as a Stripe customer. &#x60;null&#x60; otherwise, e.g. for a guest checkout. |
**created_at** | **\DateTime** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
