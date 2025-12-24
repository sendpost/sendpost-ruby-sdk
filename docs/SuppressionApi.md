# Sendpost::SuppressionApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_suppression**](SuppressionApi.md#create_suppression) | **POST** /subaccount/suppression | Create Suppressions |
| [**delete_suppression**](SuppressionApi.md#delete_suppression) | **DELETE** /subaccount/suppression | Delete Suppressions |
| [**get_suppression_list**](SuppressionApi.md#get_suppression_list) | **GET** /subaccount/suppression | List Suppressions |


## create_suppression

> <Array<Suppression>> create_suppression(create_suppression_request)

Create Suppressions

Creates new suppressions by posting to the suppression resource. You can specify different types of suppressions including `hardBounce`, `manual`, `unsubscribe`, and `spamComplaint`. 

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

api_instance = Sendpost::SuppressionApi.new
create_suppression_request = Sendpost::CreateSuppressionRequest.new # CreateSuppressionRequest | 

begin
  # Create Suppressions
  result = api_instance.create_suppression(create_suppression_request)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->create_suppression: #{e}"
end
```

#### Using the create_suppression_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<Suppression>>, Integer, Hash)> create_suppression_with_http_info(create_suppression_request)

```ruby
begin
  # Create Suppressions
  data, status_code, headers = api_instance.create_suppression_with_http_info(create_suppression_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<Suppression>>
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->create_suppression_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **create_suppression_request** | [**CreateSuppressionRequest**](CreateSuppressionRequest.md) |  |  |

### Return type

[**Array&lt;Suppression&gt;**](Suppression.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_suppression

> <Array<DeleteSuppression200ResponseInner>> delete_suppression(delete_suppression_request)

Delete Suppressions

Deletes one or more suppressions for a given sub-account. The request can contain a list of emails to delete specific suppressions or delete a single suppression. 

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

api_instance = Sendpost::SuppressionApi.new
delete_suppression_request = Sendpost::DeleteSuppressionRequest.new # DeleteSuppressionRequest | 

begin
  # Delete Suppressions
  result = api_instance.delete_suppression(delete_suppression_request)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->delete_suppression: #{e}"
end
```

#### Using the delete_suppression_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<DeleteSuppression200ResponseInner>>, Integer, Hash)> delete_suppression_with_http_info(delete_suppression_request)

```ruby
begin
  # Delete Suppressions
  data, status_code, headers = api_instance.delete_suppression_with_http_info(delete_suppression_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<DeleteSuppression200ResponseInner>>
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->delete_suppression_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **delete_suppression_request** | [**DeleteSuppressionRequest**](DeleteSuppressionRequest.md) |  |  |

### Return type

[**Array&lt;DeleteSuppression200ResponseInner&gt;**](DeleteSuppression200ResponseInner.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## get_suppression_list

> <Array<Suppression>> get_suppression_list(from, to, opts)

List Suppressions

Retrieves a list of suppressions associated with a specific sub-account within a given date range. The maximum difference between `from` and `to` dates should not exceed 60 days. 

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

api_instance = Sendpost::SuppressionApi.new
from = Date.parse('2013-10-20') # Date | Start date for the suppression records
to = Date.parse('2013-10-20') # Date | End date for the suppression records (Note: `from` should be earlier than `to` and the date range should not exceed 60 days) 
opts = {
  limit: 56, # Integer | Number of records to return per request
  offset: 56, # Integer | Number of initial records to skip
  search: 'search_example', # String | Case-insensitive search against suppression email
  type: 'hardBounce' # String | Type of suppression. Valid values: `hardBounce`, `manual`, `spamComplaint`, `unsubscribe` 
}

begin
  # List Suppressions
  result = api_instance.get_suppression_list(from, to, opts)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->get_suppression_list: #{e}"
end
```

#### Using the get_suppression_list_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<Suppression>>, Integer, Hash)> get_suppression_list_with_http_info(from, to, opts)

```ruby
begin
  # List Suppressions
  data, status_code, headers = api_instance.get_suppression_list_with_http_info(from, to, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<Suppression>>
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->get_suppression_list_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **from** | **Date** | Start date for the suppression records |  |
| **to** | **Date** | End date for the suppression records (Note: &#x60;from&#x60; should be earlier than &#x60;to&#x60; and the date range should not exceed 60 days)  |  |
| **limit** | **Integer** | Number of records to return per request | [optional][default to 20] |
| **offset** | **Integer** | Number of initial records to skip | [optional][default to 0] |
| **search** | **String** | Case-insensitive search against suppression email | [optional] |
| **type** | **String** | Type of suppression. Valid values: &#x60;hardBounce&#x60;, &#x60;manual&#x60;, &#x60;spamComplaint&#x60;, &#x60;unsubscribe&#x60;  | [optional] |

### Return type

[**Array&lt;Suppression&gt;**](Suppression.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

