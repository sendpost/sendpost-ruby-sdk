# Sendpost::EmailResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **to** | **String** | The recipient email address this response corresponds to | [optional] |
| **submitted_at** | **Integer** | UNIX epoch timestamp in nanoseconds when the email was accepted for processing. Use this for precise timing and correlation with webhook events.  | [optional] |
| **message_id** | **String** | Unique identifier (UUID) for this email message. Use this ID to track the email through webhooks and the message lookup API.  | [optional] |
| **error_code** | **Integer** | Error code if the email submission failed. Common codes: - 0: Success (no error) - 1: Invalid recipient email - 2: Recipient in suppression list - 3: Domain not verified - 4: Rate limit exceeded - 5: Invalid sender email  | [optional] |
| **message** | **String** | Human-readable message describing the result. On success: \&quot;Email submitted successfully\&quot; On error: Description of what went wrong  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EmailResponse.new(
  to: customer@example.com,
  submitted_at: 1704067200000000000,
  message_id: 550e8400-e29b-41d4-a716-446655440000,
  error_code: 0,
  message: Email submitted successfully
)
```

