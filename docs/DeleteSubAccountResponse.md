# Sendpost::DeleteSubAccountResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | ID of the deleted sub-account | [optional] |
| **message** | **String** | Confirmation message | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DeleteSubAccountResponse.new(
  id: 50442,
  message: Sub-Account (Marketing - Production) has been deleted successfully
)
```

