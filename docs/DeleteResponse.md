# Sendpost::DeleteResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | ID of the deleted resource | [optional] |
| **message** | **String** | Human-readable confirmation message | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DeleteResponse.new(
  id: 117,
  message: Resource has been deleted successfully
)
```

