# Sendpost::AggregateStats

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **processed** | **Integer** |  | [optional] |
| **sent** | **Integer** |  | [optional] |
| **delivered** | **Integer** |  | [optional] |
| **dropped** | **Integer** |  | [optional] |
| **smtp_dropped** | **Integer** |  | [optional] |
| **hard_bounced** | **Integer** |  | [optional] |
| **soft_bounced** | **Integer** |  | [optional] |
| **opened** | **Integer** |  | [optional] |
| **clicked** | **Integer** |  | [optional] |
| **unsubscribed** | **Integer** |  | [optional] |
| **spams** | **Integer** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::AggregateStats.new(
  processed: 22500,
  sent: 22400,
  delivered: 20000,
  dropped: 1000,
  smtp_dropped: 400,
  hard_bounced: 1000,
  soft_bounced: 500,
  opened: 5000,
  clicked: 3000,
  unsubscribed: 500,
  spams: 200
)
```

