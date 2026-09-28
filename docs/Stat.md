# Sendpost::Stat

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **processed** | **Integer** | Total number of emails accepted by SendPost API for processing. This is the starting point - all emails submitted through the API.  | [optional] |
| **sent** | **Integer** | Number of emails sent to recipient mail servers. sent &#x3D; processed - dropped - smtpDropped  | [optional] |
| **dropped** | **Integer** | Number of emails dropped before sending. Common reasons: - Recipient email in suppression list (hard bounce, spam complaint, unsubscribe) - Invalid recipient email format - Sender domain not verified  | [optional] |
| **smtp_dropped** | **Integer** | Number of emails dropped at SMTP level due to policy violations or rate limiting by the receiving server before delivery attempt completed.  | [optional] |
| **delivered** | **Integer** | Number of emails successfully delivered to recipient mail servers. Note: Delivered means accepted by the server, not necessarily in inbox.  | [optional] |
| **soft_bounced** | **Integer** | Number of temporary delivery failures (soft bounces). Common causes: - Recipient mailbox full - Server temporarily unavailable - Message too large SendPost automatically retries soft bounces.  | [optional] |
| **hard_bounced** | **Integer** | Number of permanent delivery failures (hard bounces). Common causes: - Recipient email doesn&#39;t exist - Domain doesn&#39;t exist - Recipient has blocked sender Hard bounced addresses are automatically added to suppression list.  | [optional] |
| **opened** | **Integer** | Number of emails opened (tracking pixel loaded). Requires trackOpens&#x3D;true. Note: Some email clients block tracking pixels.  | [optional] |
| **clicked** | **Integer** | Number of emails with at least one link clicked. Requires trackClicks&#x3D;true.  | [optional] |
| **unsubscribed** | **Integer** | Number of recipients who clicked the unsubscribe link. Unsubscribed addresses are automatically added to suppression list.  | [optional] |
| **spam** | **Integer** | Number of spam complaints (recipient marked email as spam). High spam rates can severely impact your sender reputation. Target: Keep spam rate below 0.1%.  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Stat.new(
  processed: 225,
  sent: 220,
  dropped: 10,
  smtp_dropped: 5,
  delivered: 200,
  soft_bounced: 5,
  hard_bounced: 10,
  opened: 150,
  clicked: 50,
  unsubscribed: 6,
  spam: 2
)
```

