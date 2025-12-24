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

Retrieve aggregated email statistics for all sub-accounts of a specific account for a given date range.

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
from = Date.parse('2019-01-01') # Date | The start date for retrieving aggregated stats (inclusive)
to = Date.parse('2019-12-31') # Date | The end date for retrieving aggregated stats (inclusive). The difference between `from` and `to` should not exceed 366 days.

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
| **from** | **Date** | The start date for retrieving aggregated stats (inclusive) |  |
| **to** | **Date** | The end date for retrieving aggregated stats (inclusive). The difference between &#x60;from&#x60; and &#x60;to&#x60; should not exceed 366 days. |  |

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

Gets aggregated email stats for a specific group in all sub-accounts of a specific account for the given daterange. The maximum daterange for which these stats can be retrieved is 366 days.

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
group = 'shopify' # String | Group whose aggregate stats need to be retrieved.
from = Date.parse('2019-01-01') # Date | Date from which stats should be retrieved (should be in the format `YYYY-MM-DD`).
to = Date.parse('2019-12-31') # Date | Date to which stats should be retrieved (should be in the format `YYYY-MM-DD`). Note that the difference between `from` and `to` should not be more than 366 days.

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
| **group** | **String** | Group whose aggregate stats need to be retrieved. |  |
| **from** | **Date** | Date from which stats should be retrieved (should be in the format &#x60;YYYY-MM-DD&#x60;). |  |
| **to** | **Date** | Date to which stats should be retrieved (should be in the format &#x60;YYYY-MM-DD&#x60;). Note that the difference between &#x60;from&#x60; and &#x60;to&#x60; should not be more than 366 days. |  |

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

Gets a list of all email stats for all sub-accounts of a specific account by group for a given daterange. The maximum daterange for which these stats can be retrieved is 31 days.

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
group = 'shopify' # String | Group whose stats need to be retrieved
from = Date.parse('2020-03-12') # Date | Date from which stats should be retrieved (should be in the format `YYYY-MM-DD`)
to = Date.parse('2020-04-14') # Date | Date to which stats should be retrieved (should be in the format `YYYY-MM-DD`). Note that the difference between `from` and `to` should not be more than 31 days.

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
| **group** | **String** | Group whose stats need to be retrieved |  |
| **from** | **Date** | Date from which stats should be retrieved (should be in the format &#x60;YYYY-MM-DD&#x60;) |  |
| **to** | **Date** | Date to which stats should be retrieved (should be in the format &#x60;YYYY-MM-DD&#x60;). Note that the difference between &#x60;from&#x60; and &#x60;to&#x60; should not be more than 31 days. |  |

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

Retrieve email statistics for all sub-accounts of a specific account for a given date range.

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
from = Date.parse('2020-03-12') # Date | The start date for retrieving stats (inclusive)
to = Date.parse('2020-04-14') # Date | The end date for retrieving stats (inclusive). The difference between `from` and `to` should not exceed 31 days.

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
| **from** | **Date** | The start date for retrieving stats (inclusive) |  |
| **to** | **Date** | The end date for retrieving stats (inclusive). The difference between &#x60;from&#x60; and &#x60;to&#x60; should not exceed 31 days. |  |

### Return type

[**Array&lt;AccountStats&gt;**](AccountStats.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

