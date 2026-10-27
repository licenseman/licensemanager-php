# SubscriptionStats

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**active_count** | **int** | Number of ongoing subscriptions: &#x60;active&#x60;, &#x60;trialing&#x60; or &#x60;past_due&#x60;. |
**trialing_count** | **int** |  |
**past_due_count** | **int** | Number of them whose renewal failed, as Stripe retries it: their licenses stay valid for the integration&#39;s grace days. |
**canceling_count** | **int** | Number of them set to end at the end of their period. |
**new_count** | **int** | Number of subscriptions started in the last 30 days. |
**ended_count** | **int** | Number of subscriptions that ended in the last 30 days. |
**churn_rate** | **float** | Share of the subscriptions ongoing 30 days ago that ended since, from 0 to 1. |
**new_by_month** | **int[]** | Number of subscriptions started each month, aligned on &#x60;months&#x60;. |
**ended_by_month** | **int[]** | Number of subscriptions that ended each month, aligned on &#x60;months&#x60;. |
**active_by_month** | **int[]** | Number of ongoing subscriptions at the end of each month, aligned on &#x60;months&#x60;, today for this month. |
**mrr** | [**\LicenseManager\Model\Mrr[]**](Mrr.md) | MRR in each currency, from the highest number of subscriptions. Amounts aren&#39;t converted between currencies. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
