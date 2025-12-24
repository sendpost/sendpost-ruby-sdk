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

Allocates a new IP resource to the account. 

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
ip_allocation_request = Sendpost::IPAllocationRequest.new({overflow_pool: true, ips: ['34.21.14.11']}) # IPAllocationRequest | 

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

Deletes a specific IP resource based on the provided IP ID. 

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
ip_id = 56 # Integer | The ID of the IP resource to delete

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
| **ip_id** | **Integer** | The ID of the IP resource to delete |  |

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

Retrieves a list of all IPs associated with the main account. 

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
  limit: 56, # Integer | Number of records to return per request
  offset: 56, # Integer | Number of initial records to skip
  search: 'search_example' # String | Case insensitive search against IP's public IP address
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
| **limit** | **Integer** | Number of records to return per request | [optional] |
| **offset** | **Integer** | Number of initial records to skip | [optional] |
| **search** | **String** | Case insensitive search against IP&#39;s public IP address | [optional] |

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

Retrieves detailed information about a specific IP based on the provided ID. 

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
ip_id = 56 # Integer | The ID of the IP resource to retrieve

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
| **ip_id** | **Integer** | The ID of the IP resource to retrieve |  |

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

Updates an existing IP resource based on the provided IP ID. 

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
ip_update_request = Sendpost::IPUpdateRequest.new({auto_warmup_enabled: false}) # IPUpdateRequest | 
ip_id = 56 # Integer | The ID of the IP resource to update

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
| **ip_id** | **Integer** | The ID of the IP resource to update |  |

### Return type

[**IP**](IP.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

