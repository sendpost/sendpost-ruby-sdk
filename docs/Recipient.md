# Sendpost::Recipient

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **email** | **String** | The recipient&#39;s email address |  |
| **name** | **String** | The recipient&#39;s display name | [optional] |
| **cc** | [**Array&lt;CopyTo&gt;**](CopyTo.md) | Carbon copy recipients for this specific recipient&#39;s email. CC addresses will be visible to all recipients of this email copy.  | [optional] |
| **bcc** | [**Array&lt;CopyTo&gt;**](CopyTo.md) | Blind carbon copy recipients for this specific recipient&#39;s email. BCC addresses are hidden from all other recipients.  | [optional] |
| **custom_fields** | **Hash&lt;String, Object&gt;** | Custom fields for personalizing the email content for this recipient. Use Handlebars syntax ({{fieldName}}) in subject, htmlBody, or textBody to insert values. Reserved field names: &#x60;unsubscribe&#x60; (auto-generated unsubscribe link).  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Recipient.new(
  email: recipient@example.com,
  name: Jane Smith,
  cc: null,
  bcc: null,
  custom_fields: {firstName&#x3D;Jane, lastName&#x3D;Smith, accountId&#x3D;ACC-12345, planName&#x3D;Premium}
)
```

