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

> <Webhook> create_webhook(new_webhook)

Create Webhook

Create a new webhook to receive real-time notifications for email events. Your endpoint will receive HTTP POST requests with event data as they occur.  **Endpoint Requirements:** - Must be publicly accessible HTTPS URL - Should return 2xx status within 30 seconds - Handle potential duplicate events (use event ID for deduplication) - Implement retry/queue logic for reliability  **Choosing Events:** - **Engagement Tracking:** `uniqueOpened`, `uniqueClicked` for metrics - **Full History:** `opened`, `clicked` for complete event logs - **Delivery Monitoring:** `delivered`, `hardBounced`, `softBounced` - **Compliance:** `unsubscribed`, `spam`  **Best Practices:** - Only enable events you actually need - Store events before processing (async processing) - Implement idempotency using event IDs - Set up monitoring for webhook failures  **Webhook Payload Example:** ```json {   \"eventId\": \"evt_123\",   \"event\": \"delivered\",   \"messageId\": \"msg_456\",   \"recipient\": \"user@example.com\",   \"timestamp\": \"2024-01-15T10:30:00Z\" } ``` 

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
new_webhook = Sendpost::NewWebhook.new({url: 'https://app.hooli.com/api/webhooks/sendpost'}) # NewWebhook | 

begin
  # Create Webhook
  result = api_instance.create_webhook(new_webhook)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->create_webhook: #{e}"
end
```

#### Using the create_webhook_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Webhook>, Integer, Hash)> create_webhook_with_http_info(new_webhook)

```ruby
begin
  # Create Webhook
  data, status_code, headers = api_instance.create_webhook_with_http_info(new_webhook)
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
| **new_webhook** | [**NewWebhook**](NewWebhook.md) |  |  |

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

Remove a webhook from your account. After deletion, no further events will be sent to that endpoint.  **Before Deleting:** - Ensure your application doesn't rely on these events - Consider updating to a new webhook instead if you're migrating  **Note:** Events that occurred before deletion are not affected. Historical data remains intact. 

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
webhook_id = 117 # Integer | The unique ID of the webhook to delete.

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
| **webhook_id** | **Integer** | The unique ID of the webhook to delete. |  |

### Return type

[**DeleteWebhookResponse**](DeleteWebhookResponse.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_all_webhooks

> <Array<AccountWebhookWithStats>> get_all_webhooks(opts)

List Webhooks

Retrieve all configured webhooks for your account. Webhooks enable real-time notifications when email events occur, allowing you to build reactive applications.  **Supported Events:** | Event | Description | |-------|-------------| | `processed` | Email accepted and queued for delivery | | `dropped` | Email blocked (suppressed, invalid, policy) | | `delivered` | Email successfully delivered to recipient | | `hardBounced` | Permanent delivery failure | | `softBounced` | Temporary delivery failure | | `opened` | Recipient opened the email (all opens) | | `uniqueOpened` | First open per recipient only | | `clicked` | Recipient clicked a link (all clicks) | | `uniqueClicked` | First click per recipient only | | `unsubscribed` | Recipient unsubscribed | | `spam` | Recipient marked email as spam |  **Use Cases:** - Audit configured webhook endpoints - Verify webhook URLs are correct - Review enabled events per webhook - Debug webhook delivery issues 

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
  limit: 10, # Integer | Number of records to return per request. Default 20.
  offset: 0, # Integer | Number of initial records to skip for pagination.
  search: 'api.yoursite.com' # String | Case insensitive search against webhook URLs.
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

> <Array(<Array<AccountWebhookWithStats>>, Integer, Hash)> get_all_webhooks_with_http_info(opts)

```ruby
begin
  # List Webhooks
  data, status_code, headers = api_instance.get_all_webhooks_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<AccountWebhookWithStats>>
rescue Sendpost::ApiError => e
  puts "Error when calling WebhookApi->get_all_webhooks_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **limit** | **Integer** | Number of records to return per request. Default 20. | [optional][default to 20] |
| **offset** | **Integer** | Number of initial records to skip for pagination. | [optional][default to 0] |
| **search** | **String** | Case insensitive search against webhook URLs. | [optional] |

### Return type

[**Array&lt;AccountWebhookWithStats&gt;**](AccountWebhookWithStats.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_webhook

> <Webhook> get_webhook(webhook_id)

Get Webhook

Retrieve detailed information about a specific webhook, including its endpoint URL and enabled events.  **Use Cases:** - Verify webhook configuration - Debug event delivery issues - Check enabled events for a webhook - Audit webhook settings 

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
webhook_id = 117 # Integer | The unique ID of the webhook to retrieve.

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
| **webhook_id** | **Integer** | The unique ID of the webhook to retrieve. |  |

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

Modify an existing webhook's configuration. Use this to change the endpoint URL or update which events trigger notifications.  **What Can Be Updated:** - Webhook endpoint URL - Enabled/disabled events - Event-specific settings  **Use Cases:** - Migrate to a new endpoint URL - Enable additional events as needs grow - Disable events to reduce traffic - Update after infrastructure changes 

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
update_webhook = Sendpost::UpdateWebhook.new({url: 'https://app.hooli.com/api/webhooks/sendpost'}) # UpdateWebhook | 
webhook_id = 117 # Integer | The unique ID of the webhook to update.

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
| **webhook_id** | **Integer** | The unique ID of the webhook to update. |  |

### Return type

[**Webhook**](Webhook.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

