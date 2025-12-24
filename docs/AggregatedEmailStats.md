# Sendpost::AggregatedEmailStats

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **processed** | **Integer** | Total number of emails accepted by SendPost API | [optional] |
| **sent** | **Integer** | Total number of emails sent | [optional] |
| **delivered** | **Integer** | Total number of emails successfully delivered to SMTP | [optional] |
| **dropped** | **Integer** | Total number of emails dropped without delivery | [optional] |
| **smtp_dropped** | **Integer** | Total number of emails dropped by SMTP | [optional] |
| **hard_bounced** | **Integer** | Total number of hard bounce errors | [optional] |
| **soft_bounced** | **Integer** | Total number of soft bounce errors | [optional] |
| **opened** | **Integer** | Total number of emails opened by recipients | [optional] |
| **clicked** | **Integer** | Total number of links clicked by recipients | [optional] |
| **unsubscribed** | **Integer** | Total number of unsubscribed recipients | [optional] |
| **spam** | **Integer** | Total number of spams reported by recipients | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::AggregatedEmailStats.new(
  processed: null,
  sent: null,
  delivered: null,
  dropped: null,
  smtp_dropped: null,
  hard_bounced: null,
  soft_bounced: null,
  opened: null,
  clicked: null,
  unsubscribed: null,
  spam: null
)
```

