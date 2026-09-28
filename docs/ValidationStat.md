# Sendpost::ValidationStat

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **initiated** | **Integer** | Number of validation requests initiated. | [optional] |
| **processed** | **Integer** | Number of validation requests fully processed. | [optional] |
| **valid** | **Integer** | Number of addresses determined to be valid/deliverable. | [optional] |
| **invalid** | **Integer** | Number of addresses determined to be invalid/undeliverable. | [optional] |
| **soft_bounced** | **Integer** | Number of addresses that soft-bounced during validation. | [optional] |
| **hard_bounced** | **Integer** | Number of addresses that hard-bounced during validation. | [optional] |
| **catch_all** | **Integer** | Number of addresses on catch-all (accept-all) domains. | [optional] |
| **unknown** | **Integer** | Number of addresses whose deliverability could not be determined. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::ValidationStat.new(
  initiated: 1000,
  processed: 980,
  valid: 820,
  invalid: 90,
  soft_bounced: 20,
  hard_bounced: 15,
  catch_all: 25,
  unknown: 10
)
```

