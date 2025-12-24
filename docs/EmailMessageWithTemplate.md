# Sendpost::EmailMessageWithTemplate

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **from** | [**EmailAddress**](EmailAddress.md) |  | [optional] |
| **reply_to** | [**EmailAddress**](EmailAddress.md) |  | [optional] |
| **to** | [**Array&lt;Recipient&gt;**](Recipient.md) |  | [optional] |
| **subject** | **String** |  | [optional] |
| **pre_text** | **String** |  | [optional] |
| **html_body** | **String** |  | [optional] |
| **text_body** | **String** |  | [optional] |
| **amp_body** | **String** |  | [optional] |
| **ippool** | **String** |  | [optional] |
| **headers** | **Hash&lt;String, String&gt;** |  | [optional] |
| **track_opens** | **Boolean** |  | [optional] |
| **track_clicks** | **Boolean** |  | [optional] |
| **groups** | **Array&lt;String&gt;** |  | [optional] |
| **attachments** | [**Array&lt;Attachment&gt;**](Attachment.md) |  | [optional] |
| **webhook_endpoint** | **String** |  | [optional] |
| **template** | **String** |  | [optional] |
| **template_id** | **String** | Template ID for the email template | [optional] |
| **template_variables** | **Hash&lt;String, String&gt;** | Key-Value pair of template variables | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EmailMessageWithTemplate.new(
  from: null,
  reply_to: null,
  to: null,
  subject: null,
  pre_text: null,
  html_body: null,
  text_body: null,
  amp_body: null,
  ippool: null,
  headers: null,
  track_opens: null,
  track_clicks: null,
  groups: null,
  attachments: null,
  webhook_endpoint: null,
  template: null,
  template_id: null,
  template_variables: null
)
```

