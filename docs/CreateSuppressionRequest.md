# Sendpost::CreateSuppressionRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **hard_bounce** | [**Array&lt;CreateSuppressionRequestHardBounceInner&gt;**](CreateSuppressionRequestHardBounceInner.md) | Email addresses with known permanent delivery issues (invalid, non-existent domains). | [optional] |
| **manual** | [**Array&lt;CreateSuppressionRequestManualInner&gt;**](CreateSuppressionRequestManualInner.md) | Email addresses to suppress without specific categorization (do-not-contact requests, etc.). | [optional] |
| **unsubscribe** | [**Array&lt;CreateSuppressionRequestUnsubscribeInner&gt;**](CreateSuppressionRequestUnsubscribeInner.md) | Email addresses of users who opted out via external unsubscribe mechanisms. | [optional] |
| **spam_complaint** | [**Array&lt;CreateSuppressionRequestSpamComplaintInner&gt;**](CreateSuppressionRequestSpamComplaintInner.md) | Email addresses that reported spam via external feedback loops. | [optional] |

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

