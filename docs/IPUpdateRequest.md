# Sendpost::IPUpdateRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **auto_warmup_enabled** | **Boolean** | Whether the IP warmup should happen automatically or be managed manually |  |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPUpdateRequest.new(
  auto_warmup_enabled: false
)
```

