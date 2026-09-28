# Sendpost::DailyStatistics

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **processed** | **Integer** | Total emails accepted by the API | [optional] |
| **sent** | **Integer** | Total emails sent to recipient mail servers | [optional] |
| **dropped** | **Integer** | Total emails dropped before sending | [optional] |
| **smtp_dropped** | **Integer** | Total emails dropped at the SMTP level before delivery | [optional] |
| **delivered** | **Integer** | Total emails delivered successfully | [optional] |
| **soft_bounced** | **Integer** | Total temporary delivery failures | [optional] |
| **hard_bounced** | **Integer** | Total permanent delivery failures | [optional] |
| **opened** | **Integer** | Total email opens | [optional] |
| **clicked** | **Integer** | Total link clicks | [optional] |
| **unsubscribed** | **Integer** | Total unsubscribes | [optional] |
| **spam** | **Integer** | Total spam complaints | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DailyStatistics.new(
  processed: 1225,
  sent: 1210,
  dropped: 10,
  smtp_dropped: 5,
  delivered: 1200,
  soft_bounced: 5,
  hard_bounced: 10,
  opened: 150,
  clicked: 130,
  unsubscribed: 15,
  spam: 12
)
```

