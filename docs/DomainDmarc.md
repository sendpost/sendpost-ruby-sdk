# Sendpost::DomainDmarc

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **host** | **String** |  | [optional] |
| **type** | **String** |  | [optional] |
| **text_value** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DomainDmarc.new(
  host: _dmarc.hooli.com,
  type: TXT,
  text_value: v&#x3D;DMARC1; p&#x3D;none;
)
```

