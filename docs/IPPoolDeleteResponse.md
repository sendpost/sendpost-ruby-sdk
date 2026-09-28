# Sendpost::IPPoolDeleteResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | ID of the deleted IP pool | [optional] |
| **message** | **String** | Confirmation message | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPPoolDeleteResponse.new(
  id: 756,
  message: IPPool (Marketing Promotional) has been deleted successfully
)
```

