# Sendpost::EIP

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **public_ip** | **String** | list of IP resources which are a part of the IP Pool containing public IP information. Note that the IPs specified in the IPPool should have been allocated in advance for your account |  |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EIP.new(
  public_ip: 52.13.11.14
)
```

