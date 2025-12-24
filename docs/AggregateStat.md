# Sendpost::AggregateStat

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **processed** | **Integer** | Number of emails accepted by SendPost API. | [optional] |
| **sent** | **Integer** | Number of emails sent. | [optional] |
| **delivered** | **Integer** | Number of emails we were able to successfully deliver at SMTP without encountering any error | [optional] |
| **dropped** | **Integer** | Number of emails drop without attempting to deliver either because the email is invalid or email in in existing suppression list | [optional] |
| **smtp_dropped** | **Integer** | Number of emails dropped by SMTP. | [optional] |
| **hard_bounced** | **Integer** | Number of emails where we got SMTP hard bounce error code by the recipient mail provider | [optional] |
| **soft_bounced** | **Integer** | Number of emails where we got temporary soft bounce error by the recipent mail provider. Soft bounced emails are retried upto 5 times over 24 hour period before marking them as hardBounced. | [optional] |
| **opened** | **Integer** | Number of emails opened by recipients | [optional] |
| **clicked** | **Integer** | Number of email links clicked by recipients | [optional] |
| **unsubscribed** | **Integer** | Number of email recipients who unsubscribed from receiving further emails | [optional] |
| **spam** | **Integer** | Number of email recipients who marked emails as spam | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::AggregateStat.new(
  processed: 225,
  sent: 220,
  delivered: 200,
  dropped: 10,
  smtp_dropped: 5,
  hard_bounced: 10,
  soft_bounced: 5,
  opened: 150,
  clicked: 130,
  unsubscribed: 6,
  spam: 2
)
```

