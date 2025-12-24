# Sendpost::EmailResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **to** | **String** |  | [optional] |
| **submitted_at** | **Integer** | UNIX epoch nano timestamp | [optional] |
| **message_id** | **String** | Message UUID | [optional] |
| **error_code** | **Integer** |  | [optional] |
| **message** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EmailResponse.new(
  to: null,
  submitted_at: null,
  message_id: null,
  error_code: null,
  message: null
)
```

