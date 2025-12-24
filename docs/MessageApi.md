# Sendpost::MessageApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_message_by_id**](MessageApi.md#get_message_by_id) | **GET** /account/message/{message_id} | Get Message |


## get_message_by_id

> <Message> get_message_by_id(message_id)

Get Message

Retrieve detailed information about a specific message by its ID.

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

api_instance = Sendpost::MessageApi.new
message_id = 'message_id_example' # String | The ID of the message to retrieve.

begin
  # Get Message
  result = api_instance.get_message_by_id(message_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling MessageApi->get_message_by_id: #{e}"
end
```

#### Using the get_message_by_id_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Message>, Integer, Hash)> get_message_by_id_with_http_info(message_id)

```ruby
begin
  # Get Message
  data, status_code, headers = api_instance.get_message_by_id_with_http_info(message_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Message>
rescue Sendpost::ApiError => e
  puts "Error when calling MessageApi->get_message_by_id_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **message_id** | **String** | The ID of the message to retrieve. |  |

### Return type

[**Message**](Message.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

