# Sendpost::WebhookReferenceApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**send_post_webhooks_post**](WebhookReferenceApi.md#send_post_webhooks_post) | **POST** /SendPostWebhooks | SendPost Webhook Object |


## send_post_webhooks_post

> send_post_webhooks_post(opts)

SendPost Webhook Object

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'

api_instance = Sendpost::WebhookReferenceApi.new
opts = {
  webhook_object:  # WebhookObject | 
}

begin
  # SendPost Webhook Object
  api_instance.send_post_webhooks_post(opts)
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookReferenceApi->send_post_webhooks_post: #{e}"
end
```

#### Using the send_post_webhooks_post_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> send_post_webhooks_post_with_http_info(opts)

```ruby
begin
  # SendPost Webhook Object
  data, status_code, headers = api_instance.send_post_webhooks_post_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookReferenceApi->send_post_webhooks_post_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **webhook_object** | [**WebhookObject**](WebhookObject.md) |  | [optional] |

### Return type

nil (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: Not defined

