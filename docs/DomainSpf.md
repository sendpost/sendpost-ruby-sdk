# Sendpost::DomainSpf

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **host** | **String** |  | [optional] |
| **type** | **String** |  | [optional] |
| **text_value** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DomainSpf.new(
  host: sp-bounce.example.com,
  type: CNAME,
  text_value: sp.sendpost.info
)
```

