# Sendpost::EmailMessageToInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** |  | [optional] |
| **email** | **String** |  | [optional] |
| **custom_fields** | **Hash&lt;String, String&gt;** |  | [optional] |
| **cc** | [**Array&lt;EmailMessageToInnerCcInner&gt;**](EmailMessageToInnerCcInner.md) |  | [optional] |
| **bcc** | [**Array&lt;EmailMessageToInnerBccInner&gt;**](EmailMessageToInnerBccInner.md) |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EmailMessageToInner.new(
  name: Gavin,
  email: gavin@hooli.com,
  custom_fields: {&quot;Company&quot;:&quot;Hooli&quot;},
  cc: null,
  bcc: null
)
```

