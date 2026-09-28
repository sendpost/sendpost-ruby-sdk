# Sendpost::IPApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**allocate_new_ip**](IPApi.md#allocate_new_ip) | **PUT** /account/ip/allocate | Allocate IP |
| [**delete_ip**](IPApi.md#delete_ip) | **DELETE** /account/ip/{ip_id} | Delete IP |
| [**get_all_ips**](IPApi.md#get_all_ips) | **GET** /account/ip/ | List IPs |
| [**get_specific_ip**](IPApi.md#get_specific_ip) | **GET** /account/ip/{ip_id} | Get IP |
| [**update_ip**](IPApi.md#update_ip) | **PUT** /account/ip/{ip_id} | Update IP |


## allocate_new_ip

> <IP> allocate_new_ip(ip_allocation_request)

Allocate IP

Request allocation of a new dedicated IP address to your account. New IPs start in warmup state to build sender reputation gradually.  **Warmup Process:** - New IPs have limited daily sending capacity - Volume increases automatically each day while `autoWarmupEnabled` is set - Full capacity typically reached after 30-45 days - Consistent, engagement-positive sending accelerates warmup  **When to Allocate New IPs:** - Scaling beyond current IP capacity - Separating different email streams (transactional vs marketing) - Geographic IP requirements - Replacing an IP with poor reputation  **Best Practices:** - Dedicated IPs require consistent volume (10k+ emails/month ideal) - Low volume on dedicated IPs can harm deliverability - Consider shared IPs for low-volume senders 

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

api_instance = Sendpost::IPApi.new
ip_allocation_request = Sendpost::IPAllocationRequest.new({ips: [34.21.14.11,  34.21.14.12]}) # IPAllocationRequest | 

begin
  # Allocate IP
  result = api_instance.allocate_new_ip(ip_allocation_request)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling IPApi->allocate_new_ip: #{e}"
end
```

#### Using the allocate_new_ip_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IP>, Integer, Hash)> allocate_new_ip_with_http_info(ip_allocation_request)

```ruby
begin
  # Allocate IP
  data, status_code, headers = api_instance.allocate_new_ip_with_http_info(ip_allocation_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IP>
rescue Sendpost::ApiError => e
  puts "Error when calling IPApi->allocate_new_ip_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ip_allocation_request** | [**IPAllocationRequest**](IPAllocationRequest.md) |  |  |

### Return type

[**IP**](IP.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_ip

> <IPDeletionResponse> delete_ip(ip_id)

Delete IP

Remove an IP address from your account. This action is irreversible.  **⚠️ Before Deleting:** - Remove the IP from all IP pools first - Ensure no active sending relies on this IP - Consider impact on overall sending capacity  **Note:** You cannot delete an IP that is currently assigned to an IP pool. 

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

api_instance = Sendpost::IPApi.new
ip_id = 11322 # Integer | The unique ID of the IP resource to delete.

begin
  # Delete IP
  result = api_instance.delete_ip(ip_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling IPApi->delete_ip: #{e}"
end
```

#### Using the delete_ip_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IPDeletionResponse>, Integer, Hash)> delete_ip_with_http_info(ip_id)

```ruby
begin
  # Delete IP
  data, status_code, headers = api_instance.delete_ip_with_http_info(ip_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IPDeletionResponse>
rescue Sendpost::ApiError => e
  puts "Error when calling IPApi->delete_ip_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ip_id** | **Integer** | The unique ID of the IP resource to delete. |  |

### Return type

[**IPDeletionResponse**](IPDeletionResponse.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_all_ips

> <Array<IP>> get_all_ips(opts)

List IPs

Retrieve all IP addresses allocated to your account. IPs are the foundation of your sending infrastructure and directly impact deliverability.  **IP Types:** | Type | Value | Description | |------|-------|-------------| | Shared | `0` | IP shared with other SendPost senders. Cost-effective, reputation is pooled. | | Dedicated | `1` | Exclusive IP for your account. Full control over sender reputation. |  **IP States:** | State | Value | Description | |-------|-------|-------------| | Warmup | `0` | New IP building reputation. Volume is limited and gradually increases. | | Normal | `1` | Fully warmed IP ready for normal sending volume. |  **Warmup Information:** - `autoWarmupEnabled` - Whether SendPost is automatically increasing volume  **Use Cases:** - Monitor IP warmup progress for new IPs - Audit shared vs dedicated IP allocation - Plan IP pool configurations - Check available sending capacity 

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

api_instance = Sendpost::IPApi.new
opts = {
  limit: 50, # Integer | Number of records to return per request. Default 20.
  offset: 0, # Integer | Number of initial records to skip for pagination.
  search: '52.34' # String | Case insensitive search against public IP addresses.
}

begin
  # List IPs
  result = api_instance.get_all_ips(opts)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling IPApi->get_all_ips: #{e}"
end
```

#### Using the get_all_ips_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<IP>>, Integer, Hash)> get_all_ips_with_http_info(opts)

```ruby
begin
  # List IPs
  data, status_code, headers = api_instance.get_all_ips_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<IP>>
rescue Sendpost::ApiError => e
  puts "Error when calling IPApi->get_all_ips_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **limit** | **Integer** | Number of records to return per request. Default 20. | [optional][default to 20] |
| **offset** | **Integer** | Number of initial records to skip for pagination. | [optional][default to 0] |
| **search** | **String** | Case insensitive search against public IP addresses. | [optional] |

### Return type

[**Array&lt;IP&gt;**](IP.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_specific_ip

> <IP> get_specific_ip(ip_id)

Get IP

Retrieve detailed information about a specific IP address, including its warmup status, type, and configuration.  **Use Cases:** - Check warmup progress for a new dedicated IP - Verify IP configuration before adding to a pool - Debug deliverability issues by checking IP state - Monitor auto-warmup progress 

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

api_instance = Sendpost::IPApi.new
ip_id = 11322 # Integer | The unique ID of the IP resource to retrieve.

begin
  # Get IP
  result = api_instance.get_specific_ip(ip_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling IPApi->get_specific_ip: #{e}"
end
```

#### Using the get_specific_ip_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IP>, Integer, Hash)> get_specific_ip_with_http_info(ip_id)

```ruby
begin
  # Get IP
  data, status_code, headers = api_instance.get_specific_ip_with_http_info(ip_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IP>
rescue Sendpost::ApiError => e
  puts "Error when calling IPApi->get_specific_ip_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ip_id** | **Integer** | The unique ID of the IP resource to retrieve. |  |

### Return type

[**IP**](IP.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## update_ip

> <IP> update_ip(ip_update_request, ip_id)

Update IP

Modify settings for an existing IP address. Use this to manage warmup configuration.  **Configurable Settings:** - `autoWarmupEnabled` - Enable/disable automatic warmup schedule  **Use Cases:** - Pause auto-warmup during low-volume periods - Re-enable warmup after manual intervention - Adjust warmup settings based on sending patterns 

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

api_instance = Sendpost::IPApi.new
ip_update_request = Sendpost::IPUpdateRequest.new # IPUpdateRequest | 
ip_id = 11322 # Integer | The unique ID of the IP resource to update.

begin
  # Update IP
  result = api_instance.update_ip(ip_update_request, ip_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling IPApi->update_ip: #{e}"
end
```

#### Using the update_ip_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IP>, Integer, Hash)> update_ip_with_http_info(ip_update_request, ip_id)

```ruby
begin
  # Update IP
  data, status_code, headers = api_instance.update_ip_with_http_info(ip_update_request, ip_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IP>
rescue Sendpost::ApiError => e
  puts "Error when calling IPApi->update_ip_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ip_update_request** | [**IPUpdateRequest**](IPUpdateRequest.md) |  |  |
| **ip_id** | **Integer** | The unique ID of the IP resource to update. |  |

### Return type

[**IP**](IP.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

