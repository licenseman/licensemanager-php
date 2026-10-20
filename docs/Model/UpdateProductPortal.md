# UpdateProductPortal

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**enabled** | **bool** | Whether customers can use the customer portal. When disabled, it answers &#x60;404&#x60;. | [optional]
**brand_color** | **string** | Background of the portal&#39;s side panel, as &#x60;#rrggbb&#x60;, stored lower cased. &#x60;null&#x60; for the default color. | [optional]
**accent_color** | **string** | Color of the portal&#39;s inputs and buttons, as &#x60;#rrggbb&#x60;, stored lower cased. &#x60;null&#x60; for the default color. | [optional]
**return_url** | **string** | Link back to your website shown in the portal, when the portal&#39;s URL has no allowed &#x60;return_url&#x60;. &#x60;null&#x60; for no link. | [optional]
**return_domains** | **string[]** | Domains the portal&#39;s &#x60;return_url&#x60; query parameter may point to, their subdomains included. Other return URLs are ignored, in favor of &#x60;returnUrl&#x60;. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
