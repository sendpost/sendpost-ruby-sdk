# Sendpost::OperatingSystem

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **family** | **String** |  | [optional] |
| **major** | **String** |  | [optional] |
| **minor** | **String** |  | [optional] |
| **patch** | **String** |  | [optional] |
| **patch_minor** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::OperatingSystem.new(
  family: Windows,
  major: 10,
  minor: 0,
  patch: 0,
  patch_minor: 0
)
```

