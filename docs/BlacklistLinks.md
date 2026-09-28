# Sendpost::BlacklistLinks

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **report_link** | **String** | Link to the full blacklist report for this resource. | [optional] |
| **whitelabel_report_link** | **String** | White-labelled variant of the blacklist report link. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::BlacklistLinks.new(
  report_link: https://app.sendpost.io/reports/blacklist/abc123,
  whitelabel_report_link: https://reports.hooli.com/blacklist/abc123
)
```

