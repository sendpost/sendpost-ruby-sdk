# Sendpost::AccountCycleUsage

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **processed** | **Integer** | Total emails processed by the account since the last billing cycle reset. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::AccountCycleUsage.new(
  processed: 15230
)
```

