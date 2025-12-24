# Sendpost::CreateWebhookRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **enabled** | **Boolean** | Is the webhook active or in a paused state? | [optional] |
| **url** | **String** | URL endpoint to which webhook calls are sent. | [optional] |
| **processed** | **Boolean** | Trigger webhook on email message being processed. | [optional] |
| **delivered** | **Boolean** | Trigger webhook on email message being delivered. | [optional] |
| **dropped** | **Boolean** | Trigger webhook on email message being dropped. | [optional] |
| **soft_bounced** | **Boolean** | Trigger webhook on email message being soft bounced. | [optional] |
| **hard_bounced** | **Boolean** | Trigger webhook on email message being hard bounced. | [optional] |
| **opened** | **Boolean** | Trigger webhook on email message being opened. | [optional] |
| **clicked** | **Boolean** | Trigger webhook on email message link being clicked. | [optional] |
| **unsubscribed** | **Boolean** | Trigger webhook on email message being unsubscribed. | [optional] |
| **spam** | **Boolean** | Trigger webhook on email message being marked as spam. | [optional] |
| **sent** | **Boolean** | Trigger webhook on email message being sent. | [optional] |
| **smtp_dropped** | **Boolean** | Trigger webhook on email message being dropped by SMTP. | [optional] |
| **unique_open** | **Boolean** | Trigger webhook on unique email opens. | [optional] |
| **unique_click** | **Boolean** | Trigger webhook on unique email clicks. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::CreateWebhookRequest.new(
  enabled: true,
  url: https://app.hooli.com/email/webhook,
  processed: true,
  delivered: true,
  dropped: false,
  soft_bounced: false,
  hard_bounced: true,
  opened: true,
  clicked: true,
  unsubscribed: true,
  spam: true,
  sent: true,
  smtp_dropped: false,
  unique_open: true,
  unique_click: true
)
```

