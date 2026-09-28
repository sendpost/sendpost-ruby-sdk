# Sendpost::AccountStats

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **date** | **Date** | The date for these statistics (UTC) | [optional] |
| **stat** | [**DailyStatistics**](DailyStatistics.md) |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::AccountStats.new(
  date: 2024-01-15,
  stat: null
)
```

