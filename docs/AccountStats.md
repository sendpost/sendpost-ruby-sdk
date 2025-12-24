# Sendpost::AccountStats

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **date** | **Date** |  | [optional] |
| **stat** | [**AccountStatsStat**](AccountStatsStat.md) |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::AccountStats.new(
  date: 2020-03-12,
  stat: null
)
```

