# Sendpost::StatsApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**account_subaccount_stat_subaccount_id_aggregate_get**](StatsApi.md#account_subaccount_stat_subaccount_id_aggregate_get) | **GET** /account/subaccount/stat/{subaccount_id}/aggregate | Get Aggregate Stats |
| [**account_subaccount_stat_subaccount_id_get**](StatsApi.md#account_subaccount_stat_subaccount_id_get) | **GET** /account/subaccount/stat/{subaccount_id} | List Stats |
| [**get_aggregate_stats_by_group**](StatsApi.md#get_aggregate_stats_by_group) | **GET** /account/subaccount/stat/{subaccount_id}/group | Get Group Aggregate Stats |


## account_subaccount_stat_subaccount_id_aggregate_get

> <AggregateStat> account_subaccount_stat_subaccount_id_aggregate_get(from, to, subaccount_id)

Get Aggregate Stats

Retrieve summarized email statistics for a sub-account over a date range. Unlike daily stats, this returns a single record with totals across all days—ideal for high-level reporting.  **Response includes total counts for:** - `processed` - Total emails submitted - `delivered` - Successfully delivered - `dropped` - Blocked before sending - `hardBounced` / `softBounced` - Bounce breakdowns - `opens` / `clicks` - Engagement totals - `unsubscribed` / `spams` - Negative signals  **Use Cases:** - Monthly performance reports - Executive dashboards - Billing period summaries - Year-over-year comparisons - SLA compliance reports  **Example:** To get Q1 2024 totals: ``` GET /account/subaccount/stat/11/aggregate?from=2024-01-01&to=2024-03-31 ```  **Note:** Maximum date range is 366 days (1 year). 

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: accountAuth
  config.api_key['X-Account-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-Account-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::StatsApi.new
from = Date.parse('2024-01-01') # Date | Start date for aggregation (inclusive). Format YYYY-MM-DD.
to = Date.parse('2024-03-31') # Date | End date for aggregation (inclusive). Max 366 days from `from` date.
subaccount_id = 11 # Integer | The unique ID of the sub-account.

begin
  # Get Aggregate Stats
  result = api_instance.account_subaccount_stat_subaccount_id_aggregate_get(from, to, subaccount_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling StatsApi->account_subaccount_stat_subaccount_id_aggregate_get: #{e}"
end
```

#### Using the account_subaccount_stat_subaccount_id_aggregate_get_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<AggregateStat>, Integer, Hash)> account_subaccount_stat_subaccount_id_aggregate_get_with_http_info(from, to, subaccount_id)

```ruby
begin
  # Get Aggregate Stats
  data, status_code, headers = api_instance.account_subaccount_stat_subaccount_id_aggregate_get_with_http_info(from, to, subaccount_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <AggregateStat>
rescue Sendpost::ApiError => e
  puts "Error when calling StatsApi->account_subaccount_stat_subaccount_id_aggregate_get_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **from** | **Date** | Start date for aggregation (inclusive). Format YYYY-MM-DD. |  |
| **to** | **Date** | End date for aggregation (inclusive). Max 366 days from &#x60;from&#x60; date. |  |
| **subaccount_id** | **Integer** | The unique ID of the sub-account. |  |

### Return type

[**AggregateStat**](AggregateStat.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## account_subaccount_stat_subaccount_id_get

> <Array<Stat>> account_subaccount_stat_subaccount_id_get(from, to, subaccount_id)

List Stats

Retrieve daily email statistics for a specific sub-account. Returns one record per day within the date range, perfect for charting trends and identifying patterns.  **Metrics Per Day:** | Metric | Description | |--------|-------------| | `processed` | Emails submitted to SendPost | | `delivered` | Successfully delivered to recipient's mailbox | | `dropped` | Blocked before sending (suppressed, invalid, etc.) | | `hardBounced` | Permanent failures (invalid address, domain doesn't exist) | | `softBounced` | Temporary failures (mailbox full, server down) | | `opens` | Total email opens (includes multiple opens per recipient) | | `clicks` | Total link clicks | | `unsubscribed` | Recipients who unsubscribed | | `spams` | Emails marked as spam by recipients |  **Key Rates to Calculate:** - Delivery Rate = `delivered / processed × 100` - Open Rate = `opens / delivered × 100` - Click Rate = `clicks / delivered × 100` - Bounce Rate = `(hardBounced + softBounced) / processed × 100`  **Use Cases:** - Daily performance dashboard - Week-over-week trend analysis - Identifying delivery issues early - SLA monitoring and reporting  **Note:** Maximum date range is 31 days. Both `from` and `to` dates are inclusive. 

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: accountAuth
  config.api_key['X-Account-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-Account-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::StatsApi.new
from = Date.parse('2024-01-01') # Date | Start date for stats retrieval (inclusive). Format YYYY-MM-DD.
to = Date.parse('2024-01-31') # Date | End date for stats retrieval (inclusive). Must be after `from` date with max 31 days range.
subaccount_id = 11 # Integer | The unique ID of the sub-account to retrieve stats for.

begin
  # List Stats
  result = api_instance.account_subaccount_stat_subaccount_id_get(from, to, subaccount_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling StatsApi->account_subaccount_stat_subaccount_id_get: #{e}"
end
```

#### Using the account_subaccount_stat_subaccount_id_get_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<Stat>>, Integer, Hash)> account_subaccount_stat_subaccount_id_get_with_http_info(from, to, subaccount_id)

```ruby
begin
  # List Stats
  data, status_code, headers = api_instance.account_subaccount_stat_subaccount_id_get_with_http_info(from, to, subaccount_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<Stat>>
rescue Sendpost::ApiError => e
  puts "Error when calling StatsApi->account_subaccount_stat_subaccount_id_get_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **from** | **Date** | Start date for stats retrieval (inclusive). Format YYYY-MM-DD. |  |
| **to** | **Date** | End date for stats retrieval (inclusive). Must be after &#x60;from&#x60; date with max 31 days range. |  |
| **subaccount_id** | **Integer** | The unique ID of the sub-account to retrieve stats for. |  |

### Return type

[**Array&lt;Stat&gt;**](Stat.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_aggregate_stats_by_group

> <AggregateStat> get_aggregate_stats_by_group(group, from, to, subaccount_id)

Get Group Aggregate Stats

Retrieve aggregated email statistics filtered by a specific group/tag. Groups are labels you assign when sending emails to categorize and segment your analytics.  **What are Groups?** Groups (also called tags) are strings you attach to emails when sending. They help you: - Track different email types (transactional vs marketing) - Segment by campaign or feature - Compare performance across categories  **Setting Groups When Sending:** ```json {   \"from\": { \"email\": \"orders@shop.com\" },   \"to\": [{ \"email\": \"customer@example.com\" }],   \"subject\": \"Order Confirmation\",   \"groups\": [\"order-confirmations\", \"transactional\"] } ```  **Use Cases:** - Compare welcome email vs password reset performance - Track marketing campaign performance by campaign ID - Measure transactional vs promotional email metrics - Analyze A/B test results by variant group  **Example:** Get stats for \"welcome-emails\" group: ``` GET /account/subaccount/stat/11/group?group=welcome-emails&from=2024-01-01&to=2024-03-31 ```  **Note:** Maximum date range is 366 days. 

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: accountAuth
  config.api_key['X-Account-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-Account-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::StatsApi.new
group = 'order-confirmations' # String | The group/tag name to filter statistics by. Must match the group name used when sending emails.
from = Date.parse('2024-01-01') # Date | Start date for aggregation (inclusive). Format YYYY-MM-DD.
to = Date.parse('2013-10-20') # Date | The ending date for the aggregated stats (Note: `from` should be earlier than `to` and the date range should not exceed 366 days) 
subaccount_id = 11 # Integer | The ID of the subaccount to retrieve

begin
  # Get Group Aggregate Stats
  result = api_instance.get_aggregate_stats_by_group(group, from, to, subaccount_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling StatsApi->get_aggregate_stats_by_group: #{e}"
end
```

#### Using the get_aggregate_stats_by_group_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<AggregateStat>, Integer, Hash)> get_aggregate_stats_by_group_with_http_info(group, from, to, subaccount_id)

```ruby
begin
  # Get Group Aggregate Stats
  data, status_code, headers = api_instance.get_aggregate_stats_by_group_with_http_info(group, from, to, subaccount_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <AggregateStat>
rescue Sendpost::ApiError => e
  puts "Error when calling StatsApi->get_aggregate_stats_by_group_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **group** | **String** | The group/tag name to filter statistics by. Must match the group name used when sending emails. |  |
| **from** | **Date** | Start date for aggregation (inclusive). Format YYYY-MM-DD. |  |
| **to** | **Date** | The ending date for the aggregated stats (Note: &#x60;from&#x60; should be earlier than &#x60;to&#x60; and the date range should not exceed 366 days)  |  |
| **subaccount_id** | **Integer** | The ID of the subaccount to retrieve |  |

### Return type

[**AggregateStat**](AggregateStat.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

