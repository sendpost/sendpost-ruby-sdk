# Sendpost::StatsAApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_account_aggregate_stats**](StatsAApi.md#get_account_aggregate_stats) | **GET** /account/stat/aggregate | Get Account Aggregate Stats |
| [**get_account_aggregate_stats_by_group**](StatsAApi.md#get_account_aggregate_stats_by_group) | **GET** /account/stat/aggregate/group | Get Account Group Aggregate Stats |
| [**get_account_stats_by_group**](StatsAApi.md#get_account_stats_by_group) | **GET** /account/stat/group | List Account Group Stats |
| [**get_all_account_stats**](StatsAApi.md#get_all_account_stats) | **GET** /account/stat | List Account Stats |


## get_account_aggregate_stats

> <AggregateStats> get_account_aggregate_stats(from, to)

Get Account Aggregate Stats

Retrieve summarized email statistics across all sub-accounts for a date range. Returns a single aggregated record—perfect for high-level reporting and dashboards.  **Use Cases:** - Annual email program review - Quarterly business reports - Month-over-month comparison - Board-level metrics - ROI calculations for email program  **Example:** Get full year stats for 2024: ``` GET /account/stat/aggregate?from=2024-01-01&to=2024-12-31 ```  **Note:** Maximum date range is 366 days (1 year). 

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

api_instance = Sendpost::StatsAApi.new
from = Date.parse('2024-01-01') # Date | Start date for aggregation (inclusive). Format YYYY-MM-DD.
to = Date.parse('2024-12-31') # Date | End date for aggregation (inclusive). Max 366 days from `from` date.

begin
  # Get Account Aggregate Stats
  result = api_instance.get_account_aggregate_stats(from, to)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling StatsAApi->get_account_aggregate_stats: #{e}"
end
```

#### Using the get_account_aggregate_stats_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<AggregateStats>, Integer, Hash)> get_account_aggregate_stats_with_http_info(from, to)

```ruby
begin
  # Get Account Aggregate Stats
  data, status_code, headers = api_instance.get_account_aggregate_stats_with_http_info(from, to)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <AggregateStats>
rescue Sendpost::ApiError => e
  puts "Error when calling StatsAApi->get_account_aggregate_stats_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **from** | **Date** | Start date for aggregation (inclusive). Format YYYY-MM-DD. |  |
| **to** | **Date** | End date for aggregation (inclusive). Max 366 days from &#x60;from&#x60; date. |  |

### Return type

[**AggregateStats**](AggregateStats.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_account_aggregate_stats_by_group

> <AggregateStat> get_account_aggregate_stats_by_group(group, from, to)

Get Account Group Aggregate Stats

Retrieve summarized email statistics for a specific group across all sub-accounts. Returns a single aggregated record for the group—ideal for campaign reporting.  **Use Cases:** - Annual performance report for a specific product integration - Compare total metrics for different campaigns - Summarize email performance for a specific customer segment - Calculate ROI for a marketing campaign by group  **Example:** Get yearly stats for Shopify integration: ``` GET /account/stat/aggregate/group?group=shopify&from=2024-01-01&to=2024-12-31 ```  **Note:** Maximum date range is 366 days (1 year). 

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

api_instance = Sendpost::StatsAApi.new
group = 'shopify' # String | The group/tag name to filter and aggregate statistics by.
from = Date.parse('2024-01-01') # Date | Start date for aggregation (inclusive). Format YYYY-MM-DD.
to = Date.parse('2024-12-31') # Date | End date for aggregation (inclusive). Max 366 days from `from` date.

begin
  # Get Account Group Aggregate Stats
  result = api_instance.get_account_aggregate_stats_by_group(group, from, to)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling StatsAApi->get_account_aggregate_stats_by_group: #{e}"
end
```

#### Using the get_account_aggregate_stats_by_group_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<AggregateStat>, Integer, Hash)> get_account_aggregate_stats_by_group_with_http_info(group, from, to)

```ruby
begin
  # Get Account Group Aggregate Stats
  data, status_code, headers = api_instance.get_account_aggregate_stats_by_group_with_http_info(group, from, to)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <AggregateStat>
rescue Sendpost::ApiError => e
  puts "Error when calling StatsAApi->get_account_aggregate_stats_by_group_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **group** | **String** | The group/tag name to filter and aggregate statistics by. |  |
| **from** | **Date** | Start date for aggregation (inclusive). Format YYYY-MM-DD. |  |
| **to** | **Date** | End date for aggregation (inclusive). Max 366 days from &#x60;from&#x60; date. |  |

### Return type

[**AggregateStat**](AggregateStat.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_account_stats_by_group

> <Array<Stat>> get_account_stats_by_group(group, from, to)

List Account Group Stats

Retrieve daily email statistics for a specific group across all sub-accounts. Returns one record per day, filtered by the group/tag you specify.  **What are Groups?** Groups (tags) are labels attached to emails when sending. They enable segmented analytics across your entire account.  **Common Group Strategies:** | Strategy | Example Groups | |----------|----------------| | By Product | `shopify`, `wordpress`, `api-direct` | | By Type | `transactional`, `marketing`, `alerts` | | By Team | `sales-team`, `support`, `engineering` | | By Campaign | `black-friday-2024`, `summer-sale` |  **Use Cases:** - Compare performance across products/integrations - Track specific campaign performance account-wide - Analyze transactional vs marketing metrics - Benchmark different teams' email performance  **Note:** Maximum date range is 31 days. 

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

api_instance = Sendpost::StatsAApi.new
group = 'shopify' # String | The group/tag name to filter statistics by.
from = Date.parse('2024-01-01') # Date | Start date for stats retrieval (inclusive). Format YYYY-MM-DD.
to = Date.parse('2024-01-31') # Date | End date for stats retrieval (inclusive). Max 31 days from `from` date.

begin
  # List Account Group Stats
  result = api_instance.get_account_stats_by_group(group, from, to)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling StatsAApi->get_account_stats_by_group: #{e}"
end
```

#### Using the get_account_stats_by_group_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<Stat>>, Integer, Hash)> get_account_stats_by_group_with_http_info(group, from, to)

```ruby
begin
  # List Account Group Stats
  data, status_code, headers = api_instance.get_account_stats_by_group_with_http_info(group, from, to)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<Stat>>
rescue Sendpost::ApiError => e
  puts "Error when calling StatsAApi->get_account_stats_by_group_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **group** | **String** | The group/tag name to filter statistics by. |  |
| **from** | **Date** | Start date for stats retrieval (inclusive). Format YYYY-MM-DD. |  |
| **to** | **Date** | End date for stats retrieval (inclusive). Max 31 days from &#x60;from&#x60; date. |  |

### Return type

[**Array&lt;Stat&gt;**](Stat.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_all_account_stats

> <Array<AccountStats>> get_all_account_stats(from, to)

List Account Stats

Retrieve daily email statistics aggregated across all sub-accounts. Returns one record per day within the date range—ideal for organization-wide reporting.  **Metrics Per Day:** | Metric | Description | |--------|-------------| | `processed` | Total emails submitted across all sub-accounts | | `delivered` | Successfully delivered to recipients | | `dropped` | Blocked before sending | | `hardBounced` | Permanent delivery failures | | `softBounced` | Temporary delivery failures | | `opens` | Total email opens | | `clicks` | Total link clicks | | `unsubscribed` | Recipients who unsubscribed | | `spams` | Spam complaints received |  **Use Cases:** - Organization-wide email performance dashboard - Billing and usage tracking across all sub-accounts - Executive reporting for email program health - Trend analysis across your entire email operation  **Note:** Maximum date range is 31 days. 

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

api_instance = Sendpost::StatsAApi.new
from = Date.parse('2024-01-01') # Date | Start date for stats retrieval (inclusive). Format YYYY-MM-DD.
to = Date.parse('2024-01-31') # Date | End date for stats retrieval (inclusive). Max 31 days from `from` date.

begin
  # List Account Stats
  result = api_instance.get_all_account_stats(from, to)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling StatsAApi->get_all_account_stats: #{e}"
end
```

#### Using the get_all_account_stats_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<AccountStats>>, Integer, Hash)> get_all_account_stats_with_http_info(from, to)

```ruby
begin
  # List Account Stats
  data, status_code, headers = api_instance.get_all_account_stats_with_http_info(from, to)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<AccountStats>>
rescue Sendpost::ApiError => e
  puts "Error when calling StatsAApi->get_all_account_stats_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **from** | **Date** | Start date for stats retrieval (inclusive). Format YYYY-MM-DD. |  |
| **to** | **Date** | End date for stats retrieval (inclusive). Max 31 days from &#x60;from&#x60; date. |  |

### Return type

[**Array&lt;AccountStats&gt;**](AccountStats.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

