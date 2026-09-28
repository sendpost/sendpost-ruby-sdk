# Sendpost::RIPStat

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **date** | **Date** | The date these IP statistics apply to (YYYY-MM-DD, UTC). | [optional] |
| **stat** | [**IPStat**](IPStat.md) |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::RIPStat.new(
  date: 2024-01-15,
  stat: null
)
```

