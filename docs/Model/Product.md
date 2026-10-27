# Product

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**slug** | **string** |  |
**name** | **string** |  |
**is_test_from_product_id** | **string** | For test products, id of the live product they&#39;re a sandbox of. &#x60;null&#x60; for live products. |
**logo_url** | **string** | Public URL of the product&#39;s logo, shown in the web app and the customer portal. &#x60;null&#x60; without a logo. |
**portal** | [**\LicenseManager\Model\PortalSettings**](PortalSettings.md) |  |
**auto_machine_change** | **bool** | Whether a new machine validating a license already on its max machines takes the place of the license&#39;s machine validated the longest ago, rather than being refused with &#x60;machine_limit_reached&#x60;. When the replaced machine is validated again, it takes its place back and the machine that replaced it is locked. See &#x60;validateKey&#x60;. |
**created_at** | **\DateTime** |  |
**updated_at** | **\DateTime** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
