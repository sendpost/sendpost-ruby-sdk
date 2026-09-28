# Sendpost::Event

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **event_id** | **String** | Unique identifier for this specific event. Use this for idempotency - the same event may be delivered multiple times.  | [optional] |
| **message_id** | **String** | Unique identifier of the email message this event belongs to. Use this to correlate events with the original send request.  | [optional] |
| **type** | **Integer** | Numeric event type code: - &#x60;0&#x60; &#x3D; processed (email accepted by API) - &#x60;1&#x60; &#x3D; dropped (not sent - suppression, invalid, etc.) - &#x60;2&#x60; &#x3D; delivered (accepted by recipient&#39;s mail server) - &#x60;3&#x60; &#x3D; softBounced (temporary failure, will retry) - &#x60;4&#x60; &#x3D; hardBounced (permanent failure) - &#x60;5&#x60; &#x3D; opened (tracking pixel loaded) - &#x60;6&#x60; &#x3D; clicked (link clicked) - &#x60;7&#x60; &#x3D; unsubscribed (clicked unsubscribe link) - &#x60;8&#x60; &#x3D; spam (marked as spam by recipient) - &#x60;9&#x60; &#x3D; sent (sent to mail server) - &#x60;10&#x60; &#x3D; smtpDropped (dropped at SMTP level)  | [optional] |
| **type_name** | **String** | Human-readable event type name | [optional] |
| **from** | **String** | Sender email address | [optional] |
| **to** | **String** | Recipient email address | [optional] |
| **subject** | **String** | Email subject line (useful for identifying the email) | [optional] |
| **groups** | **Array&lt;String&gt;** | Tags/groups that were associated with the email | [optional] |
| **submitted_at** | **Integer** | UNIX epoch timestamp in nanoseconds when the email was originally submitted | [optional] |
| **timestamp** | **Integer** | UNIX epoch timestamp in nanoseconds when this event occurred | [optional] |
| **event_metadata** | [**EventMetadata**](EventMetadata.md) |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Event.new(
  event_id: edhg-123gh-afasdf-124egh,
  message_id: 550e8400-e29b-41d4-a716-446655440000,
  type: 2,
  type_name: delivered,
  from: notifications@piedpiper.com,
  to: customer@example.com,
  subject: Your order has been shipped!,
  groups: [transactional, order-shipped],
  submitted_at: 1704067200000000000,
  timestamp: 1704067205000000000,
  event_metadata: null
)
```

