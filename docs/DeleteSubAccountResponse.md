# Sendpost::DeleteSubAccountResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique ID for the deleted sub-account. | [optional] |
| **message** | **String** | Message confirming the deletion. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DeleteSubAccountResponse.new(
  id: 12,
  message: Sub-Account (FoxHole V1) has been deleted successfully.
)
```

