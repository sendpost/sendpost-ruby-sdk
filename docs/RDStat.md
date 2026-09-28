# Sendpost::RDStat

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **date** | **Date** | The date these domain statistics apply to (YYYY-MM-DD, UTC). | [optional] |
| **stat** | [**Stat**](Stat.md) |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::RDStat.new(
  date: 2024-01-15,
  stat: null
)
```

