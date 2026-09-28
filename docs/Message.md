# Sendpost::Message

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **message_id** | **String** | Unique identifier (UUID) for this email message | [optional] |
| **sub_account_id** | **Integer** | ID of the sub-account that sent this email | [optional] |
| **public_ip** | **String** | The public IP address used to send this email | [optional] |
| **email_type** | **String** | Classification of the email, e.g. \&quot;transactional\&quot; or \&quot;marketing\&quot;.  | [optional] |
| **submitted_at** | **Integer** | UNIX epoch timestamp in nanoseconds when the email was submitted | [optional] |
| **from** | [**EmailAddress**](EmailAddress.md) | The sender&#39;s email address and display name | [optional] |
| **reply_to** | [**EmailAddress**](EmailAddress.md) | The Reply-To email address and display name | [optional] |
| **to** | [**Recipient**](Recipient.md) | The primary recipient, including any per-recipient CC/BCC and custom fields | [optional] |
| **header_to** | [**Recipient**](Recipient.md) | The address rendered in the visible To header (may differ from the envelope recipient) | [optional] |
| **header_cc** | [**Array&lt;CopyTo&gt;**](CopyTo.md) | Addresses rendered in the visible Cc header | [optional] |
| **header_bcc** | [**Array&lt;CopyTo&gt;**](CopyTo.md) | Addresses rendered in the visible Bcc header | [optional] |
| **attachments** | [**Array&lt;Attachment&gt;**](Attachment.md) | File attachments included with the email | [optional] |
| **groups** | **Array&lt;String&gt;** | Tags/groups associated with this email | [optional] |
| **ip_pool** | **String** | Name of the IP pool used for sending | [optional] |
| **headers** | **Hash&lt;String, String&gt;** | Custom SMTP headers set on the message | [optional] |
| **subject** | **String** | The email subject line | [optional] |
| **pre_text** | **String** | Preheader/preview text shown by many email clients after the subject | [optional] |
| **html_body** | **String** | The HTML body of the email | [optional] |
| **text_body** | **String** | The plain-text body of the email | [optional] |
| **amp_body** | **String** | The AMP for Email body, if provided | [optional] |
| **track_opens** | **Boolean** | Whether open tracking was enabled for this email | [optional] |
| **track_clicks** | **Boolean** | Whether click tracking was enabled for this email | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Message.new(
  message_id: 550e8400-e29b-41d4-a716-446655440000,
  sub_account_id: 117,
  public_ip: 52.34.11.12,
  email_type: transactional,
  submitted_at: 1704067200000000000,
  from: null,
  reply_to: null,
  to: null,
  header_to: null,
  header_cc: null,
  header_bcc: null,
  attachments: null,
  groups: [order-confirmation, transactional],
  ip_pool: transactional,
  headers: {X-Campaign-Id&#x3D;12345},
  subject: Your order has been shipped!,
  pre_text: Your order is on its way,
  html_body: &lt;h1&gt;Your order has shipped!&lt;/h1&gt;,
  text_body: Your order has shipped!,
  amp_body: ,
  track_opens: true,
  track_clicks: true
)
```

