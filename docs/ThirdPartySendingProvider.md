# Sendpost::ThirdPartySendingProvider

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **name** | **String** |  | [optional] |
| **type** | **Integer** |  | [optional] |
| **domain** | **String** |  | [optional] |
| **endpoint** | **String** |  | [optional] |
| **key** | **String** |  | [optional] |
| **secret** | **String** |  | [optional] |
| **port** | **Integer** |  | [optional] |
| **oauth_token** | **String** |  | [optional] |
| **retry_time** | **Integer** |  | [optional] |
| **created** | **Integer** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::ThirdPartySendingProvider.new(
  id: 1,
  name: sendgrid,
  type: 1,
  domain: ,
  endpoint: ,
  key: ,
  secret: your_api_key,
  port: 0,
  oauth_token: ,
  retry_time: 0,
  created: 1597511124701000
)
```

