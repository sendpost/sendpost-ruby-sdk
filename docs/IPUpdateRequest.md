# Sendpost::IPUpdateRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **auto_warmup_enabled** | **Boolean** | Toggle automatic IP warmup on or off. - &#x60;true&#x60;: SendPost automatically manages daily sending limits - &#x60;false&#x60;: You manage sending volume manually (advanced users)  Warning: Disabling warmup and sending high volume on a new IP can damage sender reputation.  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPUpdateRequest.new(
  auto_warmup_enabled: true
)
```

