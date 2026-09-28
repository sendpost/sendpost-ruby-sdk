# Sendpost::RAIPPoolStat

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **date** | **Date** | The date these IP-pool statistics apply to (YYYY-MM-DD, UTC). | [optional] |
| **stat** | [**Stat**](Stat.md) |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::RAIPPoolStat.new(
  date: 2024-01-15,
  stat: null
)
```

