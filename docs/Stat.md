# Sendpost::Stat

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **date** | **Date** | Date for which stats are retrieved (UTC). | [optional] |
| **stats** | [**StatStats**](StatStats.md) |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Stat.new(
  date: 2020-03-12,
  stats: null
)
```

