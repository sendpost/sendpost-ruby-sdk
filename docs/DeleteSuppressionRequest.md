# Sendpost::DeleteSuppressionRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **suppressions** | [**Array&lt;DeleteSuppressionRequestSuppressionsInner&gt;**](DeleteSuppressionRequestSuppressionsInner.md) | List of email addresses to remove from suppression. Each email will be removed regardless of suppression type. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DeleteSuppressionRequest.new(
  suppressions: null
)
```

