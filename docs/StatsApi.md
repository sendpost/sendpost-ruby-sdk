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

Retrieves aggregated email stats for a specific sub-account for a date range.   **Note**: The maximum date range is 366 days. 

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
from = Date.parse('2013-10-20') # Date | Start date for stats retrieval.
to = Date.parse('2013-10-20') # Date | Date to which stats should be retrieved ( Note than from date should be earlier than to date. Also the difference between from and to date shouldn't ne more than 60 days ) 
subaccount_id = 11 # Integer | The ID of the subaccount to retrieve

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
| **from** | **Date** | Start date for stats retrieval. |  |
| **to** | **Date** | Date to which stats should be retrieved ( Note than from date should be earlier than to date. Also the difference between from and to date shouldn&#39;t ne more than 60 days )  |  |
| **subaccount_id** | **Integer** | The ID of the subaccount to retrieve |  |

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

Retrieves a list of email stats for a specific sub-account within a given date range. Both `from` and `to` dates are inclusive.   **Note**: The maximum date range is 31 days. 

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
from = Date.parse('2013-10-20') # Date | Start date for stats retrieval.
to = Date.parse('2013-10-20') # Date | Date to which stats should be retrieved ( Note than from date should be earlier than to date. Also the difference between from and to date shouldn't ne more than 60 days ) 
subaccount_id = 11 # Integer | The ID of the subaccount to retrieve

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
| **from** | **Date** | Start date for stats retrieval. |  |
| **to** | **Date** | Date to which stats should be retrieved ( Note than from date should be earlier than to date. Also the difference between from and to date shouldn&#39;t ne more than 60 days )  |  |
| **subaccount_id** | **Integer** | The ID of the subaccount to retrieve |  |

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

Retrieves aggregated email stats for a specific group in a sub-account for the specified daterange. The maximum daterange for which these stats can be retrieved is 366 days. Ensure that the difference between the `from` and `to` dates does not exceed 366 days. 

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
group = 'group_example' # String | Group whose aggregated stats need to be retrieved
from = Date.parse('2013-10-20') # Date | The starting date for the aggregated stats
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
| **group** | **String** | Group whose aggregated stats need to be retrieved |  |
| **from** | **Date** | The starting date for the aggregated stats |  |
| **to** | **Date** | The ending date for the aggregated stats (Note: &#x60;from&#x60; should be earlier than &#x60;to&#x60; and the date range should not exceed 366 days)  |  |
| **subaccount_id** | **Integer** | The ID of the subaccount to retrieve |  |

### Return type

[**AggregateStat**](AggregateStat.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

