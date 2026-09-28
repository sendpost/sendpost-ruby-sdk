# Sendpost::IPPool

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique identifier for the IP pool | [optional] |
| **name** | **String** | Display name for the IP pool. Must be unique within your account. Use descriptive names like \&quot;transactional\&quot;, \&quot;marketing\&quot;, \&quot;high-priority\&quot;.  | [optional] |
| **type** | **Integer** | Type of IP pool: - &#x60;0&#x60; &#x3D; Shared (uses shared IPs with pooled reputation) - &#x60;1&#x60; &#x3D; Dedicated (uses dedicated IPs exclusive to your account)  | [optional] |
| **routing_strategy** | **Integer** | How emails are distributed across IPs/providers in this pool: - &#x60;0&#x60; &#x3D; Round Robin (equal distribution) - &#x60;1&#x60; &#x3D; Email Provider Strategy (route by recipient domain like Gmail, Yahoo) - &#x60;2&#x60; &#x3D; Volume Percentage Strategy (weighted distribution) - &#x60;3&#x60; &#x3D; Sending Domain Strategy (route by sender domain)  See the IPPools tag description for detailed routing configuration examples.  | [optional] |
| **routing_meta_data** | **String** | JSON-encoded configuration for the selected routing strategy. Format depends on routingStrategy value. See IPPools documentation for examples.  For Round Robin (strategy 0): Use empty object &#x60;{}&#x60;  | [optional] |
| **should_overflow** | **Boolean** | Whether to automatically overflow to a backup pool when this pool is unavailable (all IPs down) or at capacity (warmup limits reached).  | [optional] |
| **overflow_pool_name** | **String** | Name of the IP pool to overflow to when shouldOverflow is enabled. The overflow pool must exist. Common pattern: overflow to shared IP pool.  | [optional] |
| **ips** | [**Array&lt;IP&gt;**](IP.md) | List of dedicated IPs assigned to this pool | [optional] |
| **created** | **Integer** | UNIX epoch timestamp in nanoseconds when the IP pool was created | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPPool.new(
  id: 746,
  name: Transactional,
  type: 1,
  routing_strategy: 0,
  routing_meta_data: {},
  should_overflow: true,
  overflow_pool_name: shared-backup,
  ips: null,
  created: 1704067200000000000
)
```

