# Sendpost::IP

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique identifier for the IP resource | [optional] |
| **public_ip** | **String** | The public IPv4 address used for sending emails. This is the IP that receiving mail servers will see.  | [optional] |
| **reverse_dns_hostname** | **String** | The reverse DNS (PTR record) hostname for this IP. Properly configured rDNS is important for deliverability. Format: sp{id}.{region}.sendpost.email  | [optional] |
| **type** | **Integer** | Type of IP allocation: - &#x60;0&#x60; &#x3D; Shared IP (shared with other SendPost senders, pooled reputation) - &#x60;1&#x60; &#x3D; Dedicated IP (exclusive to your account, your own reputation)  | [optional] |
| **auto_warmup_enabled** | **Boolean** | Whether automatic IP warmup is enabled. When enabled, SendPost automatically manages sending volume to gradually build reputation on this IP.  | [optional] |
| **labels** | [**Array&lt;Label&gt;**](Label.md) | Custom labels/tags for organizing IPs | [optional] |
| **state** | **Integer** | Current state of the IP: - &#x60;0&#x60; &#x3D; Warmup (IP is in warmup phase, gradually building reputation) - &#x60;1&#x60; &#x3D; Normal (IP is fully warmed and ready for full sending volume)  | [optional] |
| **created** | **Integer** | UNIX epoch timestamp in nanoseconds when the IP was allocated | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IP.new(
  id: 11321,
  public_ip: 52.34.11.12,
  reverse_dns_hostname: sp11321.mtaspg.email,
  type: 1,
  auto_warmup_enabled: true,
  labels: null,
  state: 1,
  created: 1704067200000000000
)
```

