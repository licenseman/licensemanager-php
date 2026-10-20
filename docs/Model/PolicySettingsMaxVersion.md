# PolicySettingsMaxVersion

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**type** | **string** |  |
**version** | **string** | &#x60;\&quot;2\&quot;&#x60; allows every 2.y.z version: the minor versions and bug fixes of version 2. &#x60;\&quot;2.3\&quot;&#x60; allows every 2.3.z version: the bug fixes of version 2.3. Bug fixes can&#39;t be locked, so patch numbers like &#x60;\&quot;2.3.1\&quot;&#x60; are rejected. |
**major_after** | [**\LicenseManager\Model\LockMaxVersionMajorAfter**](LockMaxVersionMajorAfter.md) |  |
**minor_after** | [**\LicenseManager\Model\LockMaxVersionMinorAfter**](LockMaxVersionMinorAfter.md) |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
