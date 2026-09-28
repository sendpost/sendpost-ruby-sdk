# Sendpost::Attachment

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **content** | **String** | Base64 encoded content of the attachment file. Ensure proper encoding to avoid corruption.  |  |
| **filename** | **String** | Name of the attachment file as it will appear to recipients. Include the file extension (e.g., \&quot;report.pdf\&quot;, \&quot;image.png\&quot;).  |  |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Attachment.new(
  content: SGVsbG8gV29ybGQh,
  filename: invoice-12345.pdf
)
```

