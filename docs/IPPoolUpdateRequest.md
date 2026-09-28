# Sendpost::IPPoolUpdateRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** | New display name for the IP pool | [optional] |
| **ips** | [**Array&lt;EIP&gt;**](EIP.md) | Updated list of IP addresses for this pool. This replaces the current IP list - include all IPs you want in the pool.  | [optional] |
| **tpsps** | **Array&lt;Integer&gt;** | Updated list of third-party sending provider IDs | [optional] |
| **routing_strategy** | **Integer** | Updated routing strategy (see IPPoolCreateRequest for values) | [optional] |
| **routing_meta_data** | **String** | Updated routing configuration (JSON) | [optional] |
| **should_overflow** | **Boolean** | Whether to enable overflow to backup pool | [optional] |
| **overflow_pool_name** | **String** | Name of the overflow pool | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPPoolUpdateRequest.new(
  name: Marketing Promotional v2,
  ips: null,
  tpsps: null,
  routing_strategy: 0,
  routing_meta_data: {},
  should_overflow: true,
  overflow_pool_name: shared-backup
)
```

