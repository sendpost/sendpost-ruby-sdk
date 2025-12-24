# Sendpost::EmailMessageToInnerBccInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** |  | [optional] |
| **email** | **String** |  | [optional] |
| **custom_fields** | **Hash&lt;String, String&gt;** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EmailMessageToInnerBccInner.new(
  name: Jian,
  email: jian@bachmanity.com,
  custom_fields: {Company&#x3D;Hooli}
)
```

