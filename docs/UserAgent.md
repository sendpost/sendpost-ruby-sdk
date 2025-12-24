# Sendpost::UserAgent

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **family** | **String** |  | [optional] |
| **major** | **String** |  | [optional] |
| **minor** | **String** |  | [optional] |
| **patch** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::UserAgent.new(
  family: Mozilla,
  major: 5.0,
  minor: 0,
  patch: 0
)
```

