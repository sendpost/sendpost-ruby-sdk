# Sendpost::MessageTo

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** | Name of the recipient. | [optional] |
| **email** | **String** | Email address of the recipient. | [optional] |
| **cc** | **Array&lt;String&gt;** | List of CC recipients | [optional] |
| **bcc** | **Array&lt;String&gt;** | List of BCC recipients | [optional] |
| **custom_fields** | **Hash&lt;String, String&gt;** | Key-Value pair of custom fields. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::MessageTo.new(
  name: Test Recipient,
  email: aditya@sendx.io,
  cc: [],
  bcc: [],
  custom_fields: {}
)
```

