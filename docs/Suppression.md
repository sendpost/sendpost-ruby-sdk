# Sendpost::Suppression

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique identifier for the suppression record | [optional] |
| **email** | **String** | The suppressed email address | [optional] |
| **reason** | **Integer** | Reason code for the suppression: - &#x60;0&#x60; &#x3D; Manual (added via API or dashboard) - &#x60;1&#x60; &#x3D; Unsubscribe (recipient clicked unsubscribe link) - &#x60;2&#x60; &#x3D; Hard Bounce (permanent delivery failure) - &#x60;3&#x60; &#x3D; Spam Complaint (recipient marked as spam) - &#x60;4&#x60; &#x3D; Hard Bounce (detected by post-send validation)  | [optional] |
| **reason_text** | **String** | Human-readable suppression reason | [optional] |
| **smtp_error** | **String** | SMTP error message from the receiving server (only for hard bounce suppressions). Useful for diagnosing delivery issues.  | [optional] |
| **message_uuid** | **String** | UUID of the message whose bounce/complaint caused this suppression. Empty for manually added suppressions. Useful for tracing the origin.  | [optional] |
| **created** | **Integer** | UNIX epoch timestamp in nanoseconds when the suppression was added | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Suppression.new(
  id: 35,
  email: bounced@example.com,
  reason: 2,
  reason_text: hardBounce,
  smtp_error: 550 5.1.1 The email account that you tried to reach does not exist,
  message_uuid: 3f2504e0-4f89-41d3-9a0c-0305e82c3301,
  created: 1704067200000000000
)
```

