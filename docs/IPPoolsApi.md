# Sendpost::IPPoolsApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_ip_pool**](IPPoolsApi.md#create_ip_pool) | **POST** /account/ippool | Create IPPool |
| [**delete_ip_pool**](IPPoolsApi.md#delete_ip_pool) | **DELETE** /account/ippool/{ippool_id} | Delete IPPool |
| [**get_all_ip_pools**](IPPoolsApi.md#get_all_ip_pools) | **GET** /account/ippool | List IPPools |
| [**get_ip_pool_by_id**](IPPoolsApi.md#get_ip_pool_by_id) | **GET** /account/ippool/{ippool_id} | Get IPPool |
| [**update_ip_pool**](IPPoolsApi.md#update_ip_pool) | **PUT** /account/ippool/{ippool_id} | Update IPPool |


## create_ip_pool

> <IPPool> create_ip_pool(ip_pool_create_request)

Create IPPool

Create a new IP pool to organize your sending infrastructure. Pools group IPs and third-party sending providers (TPSPs) for intelligent routing.  **Pool Components:** - **IPs:** Dedicated IP addresses from your account - **TPSPs:** Third-party sending providers (SendGrid, Mailgun, etc.)  **TPSP Types:** | Value | Provider | |-------|----------| | `0` | Amazon SES | | `1` | SendGrid | | `2` | Mailgun | | `3` | Custom SMTP | | `4` | PostMark | | `5` | Gmail |  **Routing Strategies:** - `0` = Round Robin - Distribute traffic evenly - `1` = Email Provider - Route by recipient's mailbox provider - `2` = Volume Percentage - Split by defined percentages - `3` = Sending Domain - Route by your from domain  **Use Cases:** - Separate transactional from marketing emails - Route high-volume traffic through TPSPs - Implement provider-specific routing for deliverability - Create backup pools for failover  **Naming Best Practices:** - Use descriptive names: `Transactional_Orders`, `Marketing_Newsletter` - Include purpose: `HighPriority_Alerts`, `Bulk_Promotions` 

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

api_instance = Sendpost::IPPoolsApi.new
ip_pool_create_request = Sendpost::IPPoolCreateRequest.new({name: 'Marketing Promotional'}) # IPPoolCreateRequest | 

begin
  # Create IPPool
  result = api_instance.create_ip_pool(ip_pool_create_request)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling IPPoolsApi->create_ip_pool: #{e}"
end
```

#### Using the create_ip_pool_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IPPool>, Integer, Hash)> create_ip_pool_with_http_info(ip_pool_create_request)

```ruby
begin
  # Create IPPool
  data, status_code, headers = api_instance.create_ip_pool_with_http_info(ip_pool_create_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IPPool>
rescue Sendpost::ApiError => e
  puts "Error when calling IPPoolsApi->create_ip_pool_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ip_pool_create_request** | [**IPPoolCreateRequest**](IPPoolCreateRequest.md) |  |  |

### Return type

[**IPPool**](IPPool.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_ip_pool

> <IPPoolDeleteResponse> delete_ip_pool(ippool_id)

Delete IPPool

Remove an IP pool from your account. This action is irreversible.  **⚠️ Before Deleting:** - Ensure no sub-accounts are actively using this pool - Update any sending configurations that reference this pool - IPs in the pool will become unassigned (not deleted)  **Note:** The default system pool cannot be deleted. 

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

api_instance = Sendpost::IPPoolsApi.new
ippool_id = 756 # Integer | The unique ID of the IP pool to delete.

begin
  # Delete IPPool
  result = api_instance.delete_ip_pool(ippool_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling IPPoolsApi->delete_ip_pool: #{e}"
end
```

#### Using the delete_ip_pool_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IPPoolDeleteResponse>, Integer, Hash)> delete_ip_pool_with_http_info(ippool_id)

```ruby
begin
  # Delete IPPool
  data, status_code, headers = api_instance.delete_ip_pool_with_http_info(ippool_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IPPoolDeleteResponse>
rescue Sendpost::ApiError => e
  puts "Error when calling IPPoolsApi->delete_ip_pool_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ippool_id** | **Integer** | The unique ID of the IP pool to delete. |  |

### Return type

[**IPPoolDeleteResponse**](IPPoolDeleteResponse.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_all_ip_pools

> <Array<IPPool>> get_all_ip_pools(opts)

List IPPools

Retrieve all IP pools configured for your account. IP pools group IPs and third-party sending providers (TPSPs) for intelligent traffic routing.  **Pool Types:** | Type | Value | Description | |------|-------|-------------| | Shared | `0` | Pool uses shared IPs (shared with other SendPost customers) | | Dedicated | `1` | Pool uses dedicated IPs (exclusive to your account) |  **Routing Strategies:** | Strategy | Value | Description | |----------|-------|-------------| | Round Robin | `0` | Distribute traffic evenly across pool members | | Email Provider | `1` | Route based on recipient's mailbox provider (Gmail, Yahoo, etc.) | | Volume Percentage | `2` | Split traffic by defined percentages | | Sending Domain | `3` | Route based on your sending domain |  **Use Cases:** - Audit your sending infrastructure configuration - View IPs and TPSPs in each pool - Plan routing strategy changes - Verify pool setup before sending campaigns 

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

api_instance = Sendpost::IPPoolsApi.new
opts = {
  limit: 10, # Integer | Number of records to return per request. Default 20.
  offset: 0, # Integer | Number of initial records to skip for pagination.
  search: 'Transactional' # String | Case insensitive search against IP pool names.
}

begin
  # List IPPools
  result = api_instance.get_all_ip_pools(opts)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling IPPoolsApi->get_all_ip_pools: #{e}"
end
```

#### Using the get_all_ip_pools_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<IPPool>>, Integer, Hash)> get_all_ip_pools_with_http_info(opts)

```ruby
begin
  # List IPPools
  data, status_code, headers = api_instance.get_all_ip_pools_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<IPPool>>
rescue Sendpost::ApiError => e
  puts "Error when calling IPPoolsApi->get_all_ip_pools_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **limit** | **Integer** | Number of records to return per request. Default 20. | [optional][default to 20] |
| **offset** | **Integer** | Number of initial records to skip for pagination. | [optional][default to 0] |
| **search** | **String** | Case insensitive search against IP pool names. | [optional] |

### Return type

[**Array&lt;IPPool&gt;**](IPPool.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_ip_pool_by_id

> <IPPool> get_ip_pool_by_id(ippool_id)

Get IPPool

Retrieve complete details about a specific IP pool, including all IPs and TPSPs assigned to it.  **Response Includes:** - Pool name, ID, and creation date - Complete list of IPs with warmup status - All configured TPSPs with their settings - Current routing strategy and metadata - Warmup and monitoring configuration  **Use Cases:** - Verify pool configuration before sending - Check which IPs/TPSPs are in a pool - Debug routing issues - Audit pool settings for compliance 

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

api_instance = Sendpost::IPPoolsApi.new
ippool_id = 74 # Integer | The unique ID of the IP pool to retrieve.

begin
  # Get IPPool
  result = api_instance.get_ip_pool_by_id(ippool_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling IPPoolsApi->get_ip_pool_by_id: #{e}"
end
```

#### Using the get_ip_pool_by_id_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IPPool>, Integer, Hash)> get_ip_pool_by_id_with_http_info(ippool_id)

```ruby
begin
  # Get IPPool
  data, status_code, headers = api_instance.get_ip_pool_by_id_with_http_info(ippool_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IPPool>
rescue Sendpost::ApiError => e
  puts "Error when calling IPPoolsApi->get_ip_pool_by_id_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ippool_id** | **Integer** | The unique ID of the IP pool to retrieve. |  |

### Return type

[**IPPool**](IPPool.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## update_ip_pool

> <IPPool> update_ip_pool(ip_pool_update_request, ippool_id)

Update IPPool

Modify an existing IP pool's configuration, including name, IPs, TPSPs, and routing strategy.  **What Can Be Updated:** - Pool name - IP addresses assigned to the pool - Third-party sending providers (TPSPs) - Routing strategy and metadata - Warmup and monitoring settings  **Use Cases:** - Add new IPs to scale capacity - Remove underperforming IPs - Change routing strategy - Add/remove TPSP integrations - Rename pool for clarity  **Best Practices:** - Test routing changes during low-traffic periods - Ensure at least one sending option remains in the pool - Document changes for team awareness 

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'

api_instance = Sendpost::IPPoolsApi.new
ip_pool_update_request = Sendpost::IPPoolUpdateRequest.new # IPPoolUpdateRequest | 
ippool_id = 756 # Integer | The unique ID of the IP pool to update.

begin
  # Update IPPool
  result = api_instance.update_ip_pool(ip_pool_update_request, ippool_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling IPPoolsApi->update_ip_pool: #{e}"
end
```

#### Using the update_ip_pool_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IPPool>, Integer, Hash)> update_ip_pool_with_http_info(ip_pool_update_request, ippool_id)

```ruby
begin
  # Update IPPool
  data, status_code, headers = api_instance.update_ip_pool_with_http_info(ip_pool_update_request, ippool_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IPPool>
rescue Sendpost::ApiError => e
  puts "Error when calling IPPoolsApi->update_ip_pool_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ip_pool_update_request** | [**IPPoolUpdateRequest**](IPPoolUpdateRequest.md) |  |  |
| **ippool_id** | **Integer** | The unique ID of the IP pool to update. |  |

### Return type

[**IPPool**](IPPool.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

