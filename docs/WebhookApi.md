# Sendpost::WebhookApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_webhook**](WebhookApi.md#create_webhook) | **POST** /account/webhook | Create Webhook |
| [**delete_webhook**](WebhookApi.md#delete_webhook) | **DELETE** /account/webhook/{webhook_id} | Delete Webhook |
| [**get_all_webhooks**](WebhookApi.md#get_all_webhooks) | **GET** /account/webhook | List Webhooks |
| [**get_webhook**](WebhookApi.md#get_webhook) | **GET** /account/webhook/{webhook_id} | Get Webhook |
| [**update_webhook**](WebhookApi.md#update_webhook) | **PUT** /account/webhook/{webhook_id} | Update Webhook |


## create_webhook

> <Webhook> create_webhook(create_webhook_request)

Create Webhook

Create a new webhook by specifying its properties.

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

api_instance = Sendpost::WebhookApi.new
create_webhook_request = Sendpost::CreateWebhookRequest.new # CreateWebhookRequest | 

begin
  # Create Webhook
  result = api_instance.create_webhook(create_webhook_request)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->create_webhook: #{e}"
end
```

#### Using the create_webhook_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Webhook>, Integer, Hash)> create_webhook_with_http_info(create_webhook_request)

```ruby
begin
  # Create Webhook
  data, status_code, headers = api_instance.create_webhook_with_http_info(create_webhook_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Webhook>
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->create_webhook_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **create_webhook_request** | [**CreateWebhookRequest**](CreateWebhookRequest.md) |  |  |

### Return type

[**Webhook**](Webhook.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_webhook

> <DeleteWebhookResponse> delete_webhook(webhook_id)

Delete Webhook

Delete a webhook by its ID.

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

api_instance = Sendpost::WebhookApi.new
webhook_id = 117 # Integer | ID of the webhook to delete.

begin
  # Delete Webhook
  result = api_instance.delete_webhook(webhook_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->delete_webhook: #{e}"
end
```

#### Using the delete_webhook_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<DeleteWebhookResponse>, Integer, Hash)> delete_webhook_with_http_info(webhook_id)

```ruby
begin
  # Delete Webhook
  data, status_code, headers = api_instance.delete_webhook_with_http_info(webhook_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <DeleteWebhookResponse>
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->delete_webhook_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **webhook_id** | **Integer** | ID of the webhook to delete. |  |

### Return type

[**DeleteWebhookResponse**](DeleteWebhookResponse.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_all_webhooks

> <Array<Webhook>> get_all_webhooks(opts)

List Webhooks

Retrieves a list of all webhooks, their endpoints, and the events for which they are active.

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

api_instance = Sendpost::WebhookApi.new
opts = {
  limit: 10, # Integer | Number of records to return per request.
  offset: 0, # Integer | Number of initial records to skip.
  search: 'hooli' # String | Case insensitive search against webhook URL.
}

begin
  # List Webhooks
  result = api_instance.get_all_webhooks(opts)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->get_all_webhooks: #{e}"
end
```

#### Using the get_all_webhooks_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<Webhook>>, Integer, Hash)> get_all_webhooks_with_http_info(opts)

```ruby
begin
  # List Webhooks
  data, status_code, headers = api_instance.get_all_webhooks_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<Webhook>>
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->get_all_webhooks_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **limit** | **Integer** | Number of records to return per request. | [optional] |
| **offset** | **Integer** | Number of initial records to skip. | [optional] |
| **search** | **String** | Case insensitive search against webhook URL. | [optional] |

### Return type

[**Array&lt;Webhook&gt;**](Webhook.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_webhook

> <Webhook> get_webhook(webhook_id)

Get Webhook

Retrieves a specific webhook based on its ID.

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

api_instance = Sendpost::WebhookApi.new
webhook_id = 117 # Integer | The ID of the webhook to retrieve.

begin
  # Get Webhook
  result = api_instance.get_webhook(webhook_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->get_webhook: #{e}"
end
```

#### Using the get_webhook_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Webhook>, Integer, Hash)> get_webhook_with_http_info(webhook_id)

```ruby
begin
  # Get Webhook
  data, status_code, headers = api_instance.get_webhook_with_http_info(webhook_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Webhook>
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->get_webhook_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **webhook_id** | **Integer** | The ID of the webhook to retrieve. |  |

### Return type

[**Webhook**](Webhook.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## update_webhook

> <Webhook> update_webhook(update_webhook, webhook_id)

Update Webhook

Update the properties of an existing webhook.

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

api_instance = Sendpost::WebhookApi.new
update_webhook = Sendpost::UpdateWebhook.new # UpdateWebhook | 
webhook_id = 117 # Integer | ID of the webhook to update.

begin
  # Update Webhook
  result = api_instance.update_webhook(update_webhook, webhook_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->update_webhook: #{e}"
end
```

#### Using the update_webhook_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Webhook>, Integer, Hash)> update_webhook_with_http_info(update_webhook, webhook_id)

```ruby
begin
  # Update Webhook
  data, status_code, headers = api_instance.update_webhook_with_http_info(update_webhook, webhook_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Webhook>
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->update_webhook_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **update_webhook** | [**UpdateWebhook**](UpdateWebhook.md) |  |  |
| **webhook_id** | **Integer** | ID of the webhook to update. |  |

### Return type

[**Webhook**](Webhook.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

