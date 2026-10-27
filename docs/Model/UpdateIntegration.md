# UpdateIntegration

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**auto_refund** | **bool** | Whether canceling a license bought through Stripe refunds its payment. Can only be turned on when the integration&#39;s &#x60;canRefund&#x60; is true: the API key has the Refunds: Write permission. | [optional]
**subscription_grace_days** | **int** | Days a subscription license stays valid after its period ends while its renewal is unpaid, as Stripe retries the payment. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
