# Sendpost::DeleteWebhookResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | ID of the deleted webhook | [optional] |
| **message** | **String** | Confirmation message | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DeleteWebhookResponse.new(
  id: 117,
  message: Webhook (https://app.hooli.com/api/webhooks/sendpost) has been deleted successfully
)
```

