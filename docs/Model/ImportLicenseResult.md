# ImportLicenseResult

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**index** | **int** | Position of the license in &#x60;licenses&#x60;, from 0. |
**key** | **string** |  |
**status** | **string** | &#x60;created&#x60;: imported. &#x60;skipped&#x60;: a license of the product already uses the key, like one imported before: it&#39;s left as is. &#x60;failed&#x60;: not imported, see &#x60;error&#x60;. |
**license_id** | **string** | Id of the license created, or of the one using the key. |
**error** | [**\LicenseManager\Model\ImportLicenseResultError**](ImportLicenseResultError.md) |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
