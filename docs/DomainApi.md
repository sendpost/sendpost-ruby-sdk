# Sendpost::DomainApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_all_domains**](DomainApi.md#get_all_domains) | **GET** /subaccount/domain | List Domains |
| [**subaccount_domain_domain_id_delete**](DomainApi.md#subaccount_domain_domain_id_delete) | **DELETE** /subaccount/domain/{domain_id} | Delete Domain |
| [**subaccount_domain_domain_id_get**](DomainApi.md#subaccount_domain_domain_id_get) | **GET** /subaccount/domain/{domain_id} | Get Domain |
| [**subaccount_domain_post**](DomainApi.md#subaccount_domain_post) | **POST** /subaccount/domain | Create Domain |


## get_all_domains

> <Array<Domain>> get_all_domains(opts)

List Domains

Retrieve a list of all domains associated with the sub-account, including their DNS records and authentication status. 

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: subAccountAuth
  config.api_key['X-SubAccount-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-SubAccount-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::DomainApi.new
opts = {
  limit: 56, # Integer | Number of records to return per request
  offset: 56, # Integer | Number of initial records to skip
  search: 'search_example' # String | Case insensitive search against domain names
}

begin
  # List Domains
  result = api_instance.get_all_domains(opts)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->get_all_domains: #{e}"
end
```

#### Using the get_all_domains_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<Domain>>, Integer, Hash)> get_all_domains_with_http_info(opts)

```ruby
begin
  # List Domains
  data, status_code, headers = api_instance.get_all_domains_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<Domain>>
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->get_all_domains_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **limit** | **Integer** | Number of records to return per request | [optional] |
| **offset** | **Integer** | Number of initial records to skip | [optional] |
| **search** | **String** | Case insensitive search against domain names | [optional] |

### Return type

[**Array&lt;Domain&gt;**](Domain.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## subaccount_domain_domain_id_delete

> <DeleteResponse> subaccount_domain_domain_id_delete(domain_id)

Delete Domain

Delete a specific domain using its `id`.

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: subAccountAuth
  config.api_key['X-SubAccount-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-SubAccount-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::DomainApi.new
domain_id = 'domain_id_example' # String | The unique ID of the domain to delete.

begin
  # Delete Domain
  result = api_instance.subaccount_domain_domain_id_delete(domain_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->subaccount_domain_domain_id_delete: #{e}"
end
```

#### Using the subaccount_domain_domain_id_delete_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<DeleteResponse>, Integer, Hash)> subaccount_domain_domain_id_delete_with_http_info(domain_id)

```ruby
begin
  # Delete Domain
  data, status_code, headers = api_instance.subaccount_domain_domain_id_delete_with_http_info(domain_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <DeleteResponse>
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->subaccount_domain_domain_id_delete_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **domain_id** | **String** | The unique ID of the domain to delete. |  |

### Return type

[**DeleteResponse**](DeleteResponse.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## subaccount_domain_domain_id_get

> <Domain> subaccount_domain_domain_id_get(domain_id)

Get Domain

Retrieve details of a specific domain using its `id`.

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: subAccountAuth
  config.api_key['X-SubAccount-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-SubAccount-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::DomainApi.new
domain_id = 'domain_id_example' # String | The unique ID of the domain to retrieve.

begin
  # Get Domain
  result = api_instance.subaccount_domain_domain_id_get(domain_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->subaccount_domain_domain_id_get: #{e}"
end
```

#### Using the subaccount_domain_domain_id_get_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Domain>, Integer, Hash)> subaccount_domain_domain_id_get_with_http_info(domain_id)

```ruby
begin
  # Get Domain
  data, status_code, headers = api_instance.subaccount_domain_domain_id_get_with_http_info(domain_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Domain>
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->subaccount_domain_domain_id_get_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **domain_id** | **String** | The unique ID of the domain to retrieve. |  |

### Return type

[**Domain**](Domain.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## subaccount_domain_post

> <Domain> subaccount_domain_post(create_domain_request)

Create Domain

Add a new domain using its `name`.

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: subAccountAuth
  config.api_key['X-SubAccount-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-SubAccount-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::DomainApi.new
create_domain_request = Sendpost::CreateDomainRequest.new # CreateDomainRequest | 

begin
  # Create Domain
  result = api_instance.subaccount_domain_post(create_domain_request)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->subaccount_domain_post: #{e}"
end
```

#### Using the subaccount_domain_post_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Domain>, Integer, Hash)> subaccount_domain_post_with_http_info(create_domain_request)

```ruby
begin
  # Create Domain
  data, status_code, headers = api_instance.subaccount_domain_post_with_http_info(create_domain_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Domain>
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->subaccount_domain_post_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **create_domain_request** | [**CreateDomainRequest**](CreateDomainRequest.md) |  |  |

### Return type

[**Domain**](Domain.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

