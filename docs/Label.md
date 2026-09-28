# Sendpost::Label

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique identifier for the label | [optional] |
| **name** | **String** | Display name for the label (max 50 characters) | [optional] |
| **color** | **String** | Hex color code for visual identification in the dashboard. Format: 6-character hex without # prefix.  | [optional] |
| **type** | **Integer** | Resource type this label applies to: - &#x60;0&#x60; &#x3D; IP label - &#x60;1&#x60; &#x3D; Sub-account label - &#x60;2&#x60; &#x3D; IP Pool label  | [optional] |
| **created** | **Integer** | UNIX epoch timestamp in nanoseconds when the label was created | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Label.new(
  id: 42,
  name: production,
  color: 4CAF50,
  type: 0,
  created: 1704067200000000000
)
```

