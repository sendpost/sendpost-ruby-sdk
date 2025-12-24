# Sendpost::Suppression

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | The ID of the suppression | [optional] |
| **reason** | **Integer** | The reason for the suppression (0 &#x3D; manual, 1 &#x3D; unsubscribe, 2 &#x3D; hard bounce, 3 &#x3D; spam complaint) | [optional] |
| **smtp_error** | **String** | SMTP error code in case of hard bounce suppression | [optional] |
| **email** | **String** | The email address for the suppression | [optional] |
| **created** | **Integer** | UNIX epoch nano timestamp when the suppression was created | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Suppression.new(
  id: null,
  reason: null,
  smtp_error: null,
  email: null,
  created: null
)
```

