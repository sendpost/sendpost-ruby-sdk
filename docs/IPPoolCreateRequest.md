# Sendpost::IPPoolCreateRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** |  | [optional] |
| **ips** | [**Array&lt;EIP&gt;**](EIP.md) |  | [optional] |
| **tpsps** | **Array&lt;Integer&gt;** |  | [optional] |
| **routing_strategy** | **Integer** |  | [optional] |
| **routing_meta_data** | **String** |  | [optional] |
| **overflow_pool** | **Boolean** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPPoolCreateRequest.new(
  name: Marketing Promotional,
  ips: null,
  tpsps: [1],
  routing_strategy: 0,
  routing_meta_data: {},
  overflow_pool: false
)
```

