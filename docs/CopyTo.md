# Sendpost::CopyTo

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **email** | **String** | The CC/BCC recipient&#39;s email address |  |
| **name** | **String** | The CC/BCC recipient&#39;s display name | [optional] |
| **custom_fields** | **Hash&lt;String, Object&gt;** | Custom fields specific to this CC/BCC recipient. Allows personalization in CC/BCC copies of the email.  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::CopyTo.new(
  email: cc@example.com,
  name: Copy Recipient,
  custom_fields: {role&#x3D;Manager}
)
```

