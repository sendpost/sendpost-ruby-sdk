# Sendpost::AccountStatsStat

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

instance = Sendpost::AccountStatsStat.new(
  processed: 1225,
  sent: 1220,
  delivered: 1200,
  dropped: 10,
  smtp_dropped: 5,
  hard_bounced: 10,
  soft_bounced: 5,
  opened: 150,
  clicked: 130,
  unsubscribed: 15,
  spams: 12
)
```

