# Sendpost::SMTPAuth

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique identifier for the SMTP credentials | [optional] |
| **username** | **String** | SMTP username for authentication. Format: {identifier}@{subaccount_id}.sendpost.io  | [optional] |
| **created** | **Integer** | UNIX epoch timestamp in nanoseconds when credentials were created | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::SMTPAuth.new(
  id: 117,
  username: default@50441.sendpost.io,
  created: 1704067200000000000
)
```

