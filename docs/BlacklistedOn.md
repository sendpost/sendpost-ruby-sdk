# Sendpost::BlacklistedOn

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **rbl** | **String** | Name/host of the real-time blacklist (RBL) the target is listed on. | [optional] |
| **delist** | **String** | URL or instructions for requesting delisting from this RBL. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::BlacklistedOn.new(
  rbl: b.barracudacentral.org,
  delist: https://www.barracudacentral.org/rbl/removal-request
)
```

