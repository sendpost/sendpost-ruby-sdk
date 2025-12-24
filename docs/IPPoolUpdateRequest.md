# Sendpost::IPPoolUpdateRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** |  | [optional] |
| **ips** | [**Array&lt;IP&gt;**](IP.md) |  | [optional] |
| **routing_strategy** | **Integer** |  | [optional] |
| **routing_meta_data** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPPoolUpdateRequest.new(
  name: Marketing Promotional,
  ips: [{publicIP&#x3D;52.12.10.12}, {publicIP&#x3D;52.10.12.17}, {publicIP&#x3D;35.11.10.5}],
  routing_strategy: 0,
  routing_meta_data: {}
)
```

