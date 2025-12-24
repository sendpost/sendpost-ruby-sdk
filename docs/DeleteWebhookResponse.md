# Sendpost::DeleteWebhookResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique ID of the deleted webhook. | [optional] |
| **message** | **String** | Success message. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DeleteWebhookResponse.new(
  id: 117,
  message: Webhook (https://app.hooli.com/email/webhook) has been deleted successfully.
)
```

