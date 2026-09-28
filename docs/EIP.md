# Sendpost::EIP

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **public_ip** | **String** | Public IPv4 address to include in the IP pool. The IP must already be allocated to your account.  |  |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EIP.new(
  public_ip: 52.13.11.14
)
```

