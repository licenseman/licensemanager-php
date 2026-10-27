# CreateToken

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**scope** | **string[]** | Permissions of the token. A write permission implies the other ones of its resource, like the read one: &#x60;license:write&#x60; implies &#x60;license:read&#x60; and &#x60;license:cancel&#x60;. A token creating a token can only give the permissions it has. |
**expires_in_seconds** | **int** | How long the token works, in seconds, from 60 (1 minute) to 31536000 (365 days). Defaults to 900 (15 minutes). A token creating a token can&#39;t give it a later expiration than its own: it&#39;s shortened to it. | [optional] [default to 900]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
