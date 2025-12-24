# Sendpost::DomainTrack

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **host** | **String** |  | [optional] |
| **type** | **String** |  | [optional] |
| **text_value** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DomainTrack.new(
  host: track.hooli.com,
  type: CNAME,
  text_value: api.sendpost.io
)
```

