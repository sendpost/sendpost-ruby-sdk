# Sendpost::IPAllocationRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **overflow_pool** | **Boolean** | Determines whether emails should be sent over shared IP when the IP pool is full |  |
| **ips** | **Array&lt;String&gt;** |  |  |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPAllocationRequest.new(
  overflow_pool: true,
  ips: null
)
```

