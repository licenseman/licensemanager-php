# Machine

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**license_id** | **string** |  |
**fingerprint** | **string** | Identifies the machine. Unique within the license. |
**platform** | **string** |  |
**name** | **string** |  |
**status** | **string** | Whether the machine counts as using the license. A &#x60;locked&#x60; machine doesn&#39;t, and its validations are refused with &#x60;machine_locked&#x60;: it overrode a machine that came back. See &#x60;validateKey&#x60;. |
**version** | **string** | Version of the application last validated on the machine. |
**overridden_by_machine_id** | **string** | For a machine deactivated or locked by automatic machine changes, the machine that took its place. Validating the key on a deactivated machine that has one takes its place back. &#x60;null&#x60; otherwise. |
**last_validated_at** | **\DateTime** | When the license was last validated on the machine. |
**created_at** | **\DateTime** |  |
**updated_at** | **\DateTime** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
