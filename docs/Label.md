# Sendpost::Label

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique ID for the label | [optional] |
| **name** | **String** | Name of the label | [optional] |
| **created** | **Integer** | UNIX epoch nano timestamp when the label was created | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Label.new(
  id: 325,
  name: Free Tier,
  created: 1685427871489941179
)
```

