# Sendpost::ErrorResponseErrorDetailsInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **field** | **String** | Field path that failed validation | [optional] |
| **message** | **String** | Validation error message for this field | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::ErrorResponseErrorDetailsInner.new(
  field: to[0].email,
  message: must be a valid email address
)
```

