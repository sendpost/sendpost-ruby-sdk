# Sendpost::Webhook

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique ID for the webhook. | [optional] |
| **enabled** | **Boolean** | Indicates if the webhook is active or paused. | [optional] |
| **url** | **String** | URL endpoint to which webhook calls need to be made. | [optional] |
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
| **created** | **Integer** | UNIX epoch nano timestamp when the webhook was created. | [optional] |
| **created_by** | **Hash&lt;String, Object&gt;** | Member who created the webhook | [optional] |
| **updated_by** | **Hash&lt;String, Object&gt;** | Member who updated the webhook | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Webhook.new(
  id: 117,
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
  unique_click: true,
  created: 1567512491588004044,
  created_by: null,
  updated_by: null
)
```

