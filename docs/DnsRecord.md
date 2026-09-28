# Sendpost::DnsRecord

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **host** | **String** | The DNS hostname where this record should be created | [optional] |
| **type** | **String** | The DNS record type (TXT or CNAME) | [optional] |
| **text_value** | **String** | The value to set for this DNS record | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DnsRecord.new(
  host: sp-dkim._domainkey.example.com,
  type: TXT,
  text_value: v&#x3D;DKIM1;k&#x3D;rsa;p&#x3D;MIGfMA0GCSqGSIb3D...
)
```

