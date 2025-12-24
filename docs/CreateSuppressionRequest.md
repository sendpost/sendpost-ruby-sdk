# Sendpost::CreateSuppressionRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **hard_bounce** | [**Array&lt;CreateSuppressionRequestHardBounceInner&gt;**](CreateSuppressionRequestHardBounceInner.md) | list of email addresses which you want to mark in hardBounce suppression list | [optional] |
| **manual** | [**Array&lt;CreateSuppressionRequestManualInner&gt;**](CreateSuppressionRequestManualInner.md) | list of email addresses which you want to mark in manual suppression list | [optional] |
| **unsubscribe** | [**Array&lt;CreateSuppressionRequestUnsubscribeInner&gt;**](CreateSuppressionRequestUnsubscribeInner.md) | list of email addresses which you want to mark in unsubscribe suppression list | [optional] |
| **spam_complaint** | [**Array&lt;CreateSuppressionRequestSpamComplaintInner&gt;**](CreateSuppressionRequestSpamComplaintInner.md) | list of email addresses which you want to mark in spamComplaint suppression list | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::CreateSuppressionRequest.new(
  hard_bounce: null,
  manual: null,
  unsubscribe: null,
  spam_complaint: null
)
```

