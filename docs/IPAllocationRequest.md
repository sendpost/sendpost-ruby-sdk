# Sendpost::IPAllocationRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ips** | **Array&lt;String&gt;** | List of IP addresses to allocate. These must be available IPs from SendPost&#39;s IP pool. Contact support to request IP allocation.  |  |
| **auto_warmup_enabled** | **Boolean** | Enable automatic IP warmup for newly allocated IPs. Recommended: true for new IPs to gradually build sender reputation.  | [optional][default to true] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPAllocationRequest.new(
  ips: [34.21.14.11, 34.21.14.12],
  auto_warmup_enabled: true
)
```

