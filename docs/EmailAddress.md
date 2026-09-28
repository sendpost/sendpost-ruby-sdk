# Sendpost::EmailAddress

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **email** | **String** | The email address (must be a valid email format) |  |
| **name** | **String** | Display name shown in email clients. Will appear as \&quot;Name &lt;email@example.com&gt;\&quot; in the From/To fields.  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EmailAddress.new(
  email: sender@example.com,
  name: John Doe
)
```

