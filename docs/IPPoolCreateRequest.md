# Sendpost::IPPoolCreateRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** | Display name for the IP pool. Must be unique within your account. Use descriptive names like \&quot;transactional\&quot;, \&quot;marketing-bulk\&quot;, \&quot;high-priority\&quot;  |  |
| **ips** | [**Array&lt;EIP&gt;**](EIP.md) | List of dedicated IP addresses to include in this pool. IPs must already be allocated to your account.  | [optional] |
| **tpsps** | **Array&lt;Integer&gt;** | List of third-party sending provider IDs to include in this pool. TPSPs must be pre-configured in your account.  | [optional] |
| **routing_strategy** | **Integer** | Email routing strategy: - &#x60;0&#x60; &#x3D; Round Robin (equal distribution) - &#x60;1&#x60; &#x3D; Email Provider Strategy (route by recipient domain) - &#x60;2&#x60; &#x3D; Volume Percentage Strategy (weighted distribution) - &#x60;3&#x60; &#x3D; Sending Domain Strategy (route by sender domain)  | [optional][default to ROUTING_STRATEGY::N0] |
| **routing_meta_data** | **String** | JSON-encoded routing configuration. See IPPools documentation for format. Use &#x60;{}&#x60; for round-robin strategy.  | [optional][default to &#39;{}&#39;] |
| **should_overflow** | **Boolean** | Whether to overflow to shared pool when this pool is unavailable | [optional][default to false] |
| **overflow_pool_name** | **String** | Name of the IP pool to overflow to (if shouldOverflow is true) | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPPoolCreateRequest.new(
  name: Marketing Promotional,
  ips: null,
  tpsps: [101, 102],
  routing_strategy: 0,
  routing_meta_data: {},
  should_overflow: true,
  overflow_pool_name: shared-backup
)
```

