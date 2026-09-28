# Sendpost::WebhookObject

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **event** | [**Event**](Event.md) | Details about the email event that triggered this webhook | [optional] |
| **email_message** | [**EmailMessage**](EmailMessage.md) | The original email message associated with this event | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::WebhookObject.new(
  event: null,
  email_message: null
)
```

