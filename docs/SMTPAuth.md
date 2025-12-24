# Sendpost::SMTPAuth

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique ID for the SMTP Auth | [optional] |
| **username** | **String** | Username for the SMTP Auth | [optional] |
| **password** | **String** | Password for the SMTP Auth | [optional] |
| **created** | **Integer** | UNIX epoch nano timestamp when the SMTP Auth was created | [optional] |
| **updated** | **Integer** | UNIX epoch nano timestamp when the SMTP Auth was updated | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::SMTPAuth.new(
  id: 117,
  username: default@117.sendpost.io,
  password: default@117.sendpost.io,
  created: 1567512491588004044,
  updated: 1567512491588004044
)
```

