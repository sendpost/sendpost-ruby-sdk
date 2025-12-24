# Sendpost::Recipient

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **email** | **String** |  | [optional] |
| **name** | **String** |  | [optional] |
| **cc** | [**Array&lt;CopyTo&gt;**](CopyTo.md) |  | [optional] |
| **bcc** | [**Array&lt;CopyTo&gt;**](CopyTo.md) |  | [optional] |
| **custom_fields** | **Hash&lt;String, Object&gt;** | Custom fields for personalization | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Recipient.new(
  email: null,
  name: null,
  cc: null,
  bcc: null,
  custom_fields: null
)
```

