# Sendpost::EmailStatsStats

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **processed** | **Integer** | Number of emails accepted by SendPost API | [optional] |
| **sent** | **Integer** | Number of emails sent | [optional] |
| **delivered** | **Integer** | Number of emails successfully delivered to SMTP without errors | [optional] |
| **dropped** | **Integer** | Number of emails dropped without attempting to deliver due to invalid email or suppression list | [optional] |
| **smtp_dropped** | **Integer** | Number of emails dropped by SMTP | [optional] |
| **hard_bounced** | **Integer** | Number of emails that resulted in a hard bounce error | [optional] |
| **soft_bounced** | **Integer** | Number of emails that resulted in a temporary soft bounce error | [optional] |
| **opened** | **Integer** | Number of emails opened by recipients | [optional] |
| **clicked** | **Integer** | Number of email links clicked by recipients | [optional] |
| **unsubscribed** | **Integer** | Number of email recipients who unsubscribed | [optional] |
| **spam** | **Integer** | Number of emails marked as spam by recipients | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EmailStatsStats.new(
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

