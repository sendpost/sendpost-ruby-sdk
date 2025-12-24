# Sendpost::EmailMessage

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **message_id** | **String** |  | [optional] |
| **account_id** | **Integer** |  | [optional] |
| **sub_account_id** | **Integer** |  | [optional] |
| **ip_id** | **Integer** |  | [optional] |
| **public_ip** | **String** |  | [optional] |
| **local_ip** | **String** |  | [optional] |
| **email_type** | **String** |  | [optional] |
| **submitted_at** | **Integer** |  | [optional] |
| **from** | [**EmailMessageFrom**](EmailMessageFrom.md) |  | [optional] |
| **reply_to** | [**EmailMessageReplyTo**](EmailMessageReplyTo.md) |  | [optional] |
| **to** | [**Array&lt;EmailMessageToInner&gt;**](EmailMessageToInner.md) |  | [optional] |
| **groups** | **Array&lt;String&gt;** |  | [optional] |
| **ip_pool** | **String** |  | [optional] |
| **headers** | **Hash&lt;String, String&gt;** |  | [optional] |
| **custom_fields** | **Hash&lt;String, String&gt;** |  | [optional] |
| **track_opens** | **Boolean** |  | [optional] |
| **track_clicks** | **Boolean** |  | [optional] |
| **webhook_endpoint** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EmailMessage.new(
  message_id: mjhl-1401-sasdf-129324,
  account_id: 117,
  sub_account_id: 117,
  ip_id: 123,
  public_ip: 52.34.11.12,
  local_ip: 127.0.0.1,
  email_type: default,
  submitted_at: 1567512491587205024,
  from: null,
  reply_to: null,
  to: null,
  groups: [&quot;welcome&quot;,&quot;user-onboarding&quot;],
  ip_pool: transactional-piedpiper,
  headers: {&quot;X-Campaign-Id&quot;:&quot;12345&quot;},
  custom_fields: {&quot;Company&quot;:&quot;Company Name&quot;,&quot;Email&quot;:&quot;user@example.com&quot;},
  track_opens: true,
  track_clicks: true,
  webhook_endpoint: https://webhook.example.com/webhook
)
```

