# Sendpost::DomainDkim

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **host** | **String** |  | [optional] |
| **type** | **String** |  | [optional] |
| **text_value** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::DomainDkim.new(
  host: sp-dkim._domainkey.example.com,
  type: TXT,
  text_value: v&#x3D;DKIM1;k&#x3D;rsa;s&#x3D;email;h&#x3D;sha256;p&#x3D;MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDU9T3mqruDth2rHXCqNiPzr4oRbHqcUMkqCA4sTZgK7WrhjzerHVyqNAfq4Tyx9s4Tqj0CVfAuENp9mHFKt9Kow5csxqTeVkBoi5UaonafsDstm39ggxFQhKTlRpRoV+VNE5jU9WYlv3wywv28DY2woKYG6QBM6JPSKN1dYQpR4QIDAQAB
)
```

