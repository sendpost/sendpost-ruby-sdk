# Sendpost::Person

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** | Name of the person. | [optional] |
| **email** | **String** | Email address of the person. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Person.new(
  name: PiedPipers,
  email: team@piedpiper.com
)
```

