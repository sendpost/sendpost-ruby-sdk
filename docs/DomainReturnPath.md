# Sendpost::DomainReturnPath

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **host** | **String** |  | [optional] |
| **type** | **String** |  | [optional] |
| **text_value** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DomainReturnPath.new(
  host: sp-bounces.hooli.com,
  type: CNAME,
  text_value: sp.sendpost.email
)
```

