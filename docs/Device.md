# Sendpost::Device

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **family** | **String** | Device type or model family. Common values: Mac, iPhone, iPad, Windows Desktop, Android, Other  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Device.new(
  family: Mac
)
```

