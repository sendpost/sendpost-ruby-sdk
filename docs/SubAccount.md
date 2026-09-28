# Sendpost::SubAccount

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique identifier for the sub-account | [optional] |
| **account_id** | **Integer** | Identifier of the parent account this sub-account belongs to | [optional] |
| **name** | **String** | Display name for the sub-account. Must be unique within your account. Use descriptive names.  | [optional] |
| **api_key** | **String** | API key for this sub-account. Use this as the &#x60;X-SubAccount-ApiKey&#x60; header when making API calls for this sub-account (sending emails, managing domains, etc.).  **Security:** Treat this like a password. Rotate if compromised.  | [optional] |
| **type** | **Integer** | Type of sub-account: - &#x60;0&#x60; &#x3D; Default (the primary sub-account created with your account) - &#x60;1&#x60; &#x3D; Custom (additional sub-accounts you create)  Note: The default sub-account cannot be deleted.  | [optional] |
| **is_plus** | **Boolean** | Whether this sub-account belongs to a SendX Plus customer. SendX Plus is a premium tier that provides enhanced features and support.  | [optional] |
| **labels** | [**Array&lt;Label&gt;**](Label.md) | Custom labels for organizing and filtering sub-accounts | [optional] |
| **blocked** | **Boolean** | Whether the sub-account is blocked from sending. A blocked sub-account cannot send emails. Common reasons: - High bounce/spam rates - Billing issues - Policy violations - Manual suspension by administrator  | [optional] |
| **created** | **Integer** | UNIX epoch timestamp in nanoseconds when the sub-account was created | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::SubAccount.new(
  id: 50441,
  account_id: 4021,
  name: Transactional - Production,
  api_key: pR0YIuxYSbVwmQi2Y8Qs,
  type: 1,
  is_plus: false,
  labels: null,
  blocked: false,
  created: 1704067200000000000
)
```

