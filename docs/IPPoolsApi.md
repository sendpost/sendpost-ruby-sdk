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

Creates a new IPPool with the specified name, IPs, and third-party sending providers.

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
ip_pool_create_request = Sendpost::IPPoolCreateRequest.new # IPPoolCreateRequest | 

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

Delete a specific IPPool based on its ID.

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'

api_instance = Sendpost::IPPoolsApi.new
ippool_id = 756 # Integer | The ID of the IPPool to delete

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
| **ippool_id** | **Integer** | The ID of the IPPool to delete |  |

### Return type

[**IPPoolDeleteResponse**](IPPoolDeleteResponse.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_all_ip_pools

> <Array<IPPool>> get_all_ip_pools(opts)

List IPPools

Retrieves a list of all IPPools and information about all IPs contained in that pool.

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
  limit: 10, # Integer | Number of records to return per request
  offset: 0, # Integer | Number of initial records to skip
  search: 'Transactional' # String | Case insensitive search against IPPool name
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
| **limit** | **Integer** | Number of records to return per request | [optional] |
| **offset** | **Integer** | Number of initial records to skip | [optional] |
| **search** | **String** | Case insensitive search against IPPool name | [optional] |

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

Retrieves details of a specific IPPool based on its ID.

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
ippool_id = 74 # Integer | The ID of the IPPool whose information you want to retrieve

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
| **ippool_id** | **Integer** | The ID of the IPPool whose information you want to retrieve |  |

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

Update the details of an existing IPPool by its ID.

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'

api_instance = Sendpost::IPPoolsApi.new
ip_pool_update_request = Sendpost::IPPoolUpdateRequest.new # IPPoolUpdateRequest | 
ippool_id = 756 # Integer | The ID of the IPPool to update

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
| **ippool_id** | **Integer** | The ID of the IPPool to update |  |

### Return type

[**IPPool**](IPPool.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

