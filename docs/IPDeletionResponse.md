# Sendpost::IPDeletionResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | The unique ID of the IP |  |
| **message** | **String** | The confirmation message after deletion |  |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IPDeletionResponse.new(
  id: 11322,
  message: IP (34.21.14.11) has been deleted successfully
)
```

