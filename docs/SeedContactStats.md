# Sendpost::SeedContactStats

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **stat** | [**Stat**](Stat.md) |  | [optional] |
| **r_stats** | [**Array&lt;RStat&gt;**](RStat.md) | Per-day statistics for the seed-contact run. | [optional] |
| **group_stats** | [**Array&lt;GroupStat&gt;**](GroupStat.md) | Statistics broken down by group/tag. | [optional] |
| **domain_stats** | [**Array&lt;DomainStat&gt;**](DomainStat.md) | Statistics broken down by sending domain. | [optional] |
| **ip_stats** | [**Array&lt;IPStat&gt;**](IPStat.md) | Statistics broken down by sending IP address. | [optional] |
| **provider_stats** | [**Array&lt;ProviderStat&gt;**](ProviderStat.md) | Statistics broken down by email provider. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::SeedContactStats.new(
  stat: null,
  r_stats: null,
  group_stats: null,
  domain_stats: null,
  ip_stats: null,
  provider_stats: null
)
```

