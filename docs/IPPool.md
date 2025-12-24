# Sendpost::IPPool

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **name** | **String** |  | [optional] |
| **created** | **Integer** |  | [optional] |
| **ips** | [**Array&lt;IP&gt;**](IP.md) |  | [optional] |
| **third_party_sending_providers** | [**Array&lt;ThirdPartySendingProvider&gt;**](ThirdPartySendingProvider.md) |  | [optional] |
| **routing_strategy** | **Integer** |  | [optional] |
| **routing_meta_data** | **String** |  | [optional] |
| **auto_warmup_enabled** | **Boolean** |  | [optional] |
| **infra_monitor** | **Boolean** |  | [optional] |
| **ip_domain_warmup_status** | **String** |  | [optional] |
| **should_overflow** | **Boolean** | Indicates whether the IP should overflow, once email capacity of the IP Pool has been reached, should we send remaining emails over shared IP or not | [optional] |
| **overflow_pool_name** | **String** | The name of the overflow pool | [optional] |
| **warmup_interval** | **Integer** | The interval for the warmup | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPPool.new(
  id: 746,
  name: Transactional,
  created: 1597511124804000,
  ips: null,
  third_party_sending_providers: null,
  routing_strategy: 0,
  routing_meta_data: {},
  auto_warmup_enabled: false,
  infra_monitor: true,
  ip_domain_warmup_status: null,
  should_overflow: true,
  overflow_pool_name: Transactional,
  warmup_interval: 60
)
```

