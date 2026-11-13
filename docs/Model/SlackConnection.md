# SlackConnection

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**team_id** | **string** |  |
**team_name** | **string** |  |
**channel_id** | **string** |  |
**channel_name** | **string** | Name of the channel when it was connected, with its &#x60;#&#x60;. |
**configuration_url** | **string** | Page of the installation in Slack. |
**events** | **string[]** | Notifications the channel gets: &#x60;purchased&#x60; (a license bought through Stripe or Paddle), &#x60;renewed&#x60; (a subscription renewal paid), &#x60;payment_failed&#x60; (a subscription payment failed) and &#x60;canceled&#x60; (a license canceled, or its subscription ended). |
**status** | **string** | &#x60;revoked&#x60; once Slack refuses the messages, like when the app was removed from the workspace or the channel deleted: remove it and add it again. |
**status_reason** | **string** |  |
**last_sent_at** | **\DateTime** |  |
**created_at** | **\DateTime** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
