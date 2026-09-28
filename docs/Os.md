# Sendpost::Os

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **family** | **String** | Operating system family name. Common values: Windows, macOS, iOS, Android, Linux  | [optional] |
| **major** | **String** | Major version number | [optional] |
| **minor** | **String** | Minor version number | [optional] |
| **patch** | **String** | Patch version number | [optional] |
| **patch_minor** | **String** | Additional patch version component | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Os.new(
  family: macOS,
  major: 14,
  minor: 2,
  patch: 1,
  patch_minor: 0
)
```

