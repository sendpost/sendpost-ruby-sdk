# Sendpost::IPDeletionResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | ID of the deleted IP |  |
| **message** | **String** | Confirmation message |  |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPDeletionResponse.new(
  id: 11322,
  message: IP (34.21.14.11) has been deleted successfully
)
```

