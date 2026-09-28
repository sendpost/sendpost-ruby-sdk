# Sendpost::EmailMessageWithTemplate

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **from** | [**EmailAddress**](EmailAddress.md) | The sender&#39;s email address and optional display name |  |
| **reply_to** | [**EmailAddress**](EmailAddress.md) | The reply-to email address. If not specified, replies will go to the &#x60;from&#x60; address | [optional] |
| **to** | [**Array&lt;Recipient&gt;**](Recipient.md) | List of recipients. Each recipient can have their own CC, BCC, and custom fields for personalization. Maximum 1000 recipients per API call.  |  |
| **subject** | **String** | Email subject line. Supports Handlebars templating for personalization. Example: \&quot;Hello, {{firstName}}! Your order is ready\&quot;  | [optional] |
| **pre_text** | **String** | Preview text (preheader) shown in email clients before opening the email. This text appears after the subject line in most email clients&#39; inbox view.  | [optional] |
| **html_body** | **String** | HTML content of the email. Supports Handlebars templating for personalization. Use {{customFieldName}} to insert recipient-specific values.  | [optional] |
| **text_body** | **String** | Plain text content of the email. Used as fallback when HTML cannot be rendered. Also improves deliverability as some spam filters prefer multipart emails.  | [optional] |
| **amp_body** | **String** | AMP HTML content for supported email clients (Gmail, Yahoo). Enables interactive email experiences like carousels, forms, and real-time content. See https://amp.dev/about/email/ for more details.  | [optional] |
| **template** | **String** |  | [optional] |
| **ippool** | **String** | Name of the IP pool to use for sending this email. If not specified, the default IP pool for the sub-account will be used.  | [optional] |
| **headers** | **Hash&lt;String, String&gt;** | Custom email headers to include in the message. Common uses: adding List-Unsubscribe headers, custom tracking IDs, or priority flags. Note: Some headers like From, To, Subject are set automatically and cannot be overridden.  | [optional] |
| **track_opens** | **Boolean** | Whether to track email opens using a tracking pixel. When enabled, a 1x1 transparent image is inserted into the HTML body. Default: true (if not specified)  | [optional][default to true] |
| **track_clicks** | **Boolean** | Whether to track link clicks by rewriting URLs through SendPost&#39;s tracking domain. When enabled, all links in htmlBody are replaced with tracking URLs. Default: true (if not specified)  | [optional][default to true] |
| **groups** | **Array&lt;String&gt;** | Tags/groups to categorize this email for analytics and reporting. Use groups to segment your email statistics (e.g., by campaign, email type, or customer segment).  | [optional] |
| **attachments** | [**Array&lt;Attachment&gt;**](Attachment.md) | File attachments to include with the email. Maximum total attachment size: 25MB. Supported formats: PDF, images, documents, etc.  | [optional] |
| **webhook_endpoint** | **String** | Custom webhook URL to receive events for this specific email. Overrides the default webhook configured at the account level. Useful for per-email or per-customer webhook routing.  | [optional] |
| **template_id** | **String** | Template ID for the email template | [optional] |
| **template_variables** | **Hash&lt;String, String&gt;** | Key-Value pair of template variables | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EmailMessageWithTemplate.new(
  from: null,
  reply_to: null,
  to: null,
  subject: Welcome to SendPost, {{firstName}}!,
  pre_text: Your weekly digest is here with 5 new updates...,
  html_body: &lt;html&gt;&lt;body&gt;&lt;h1&gt;Hello {{firstName}}&lt;/h1&gt;&lt;p&gt;Welcome to our platform!&lt;/p&gt;&lt;/body&gt;&lt;/html&gt;,
  text_body: Hello {{firstName}},

Welcome to our platform!

Best regards,
The Team,
  amp_body: &lt;!doctype html&gt;&lt;html ⚡4email&gt;&lt;head&gt;...&lt;/head&gt;&lt;body&gt;...&lt;/body&gt;&lt;/html&gt;,
  template: null,
  ippool: transactional,
  headers: {X-Custom-Header&#x3D;custom-value, X-Campaign-ID&#x3D;summer-sale-2024, List-Unsubscribe&#x3D;&lt;mailto:unsubscribe@example.com&gt;},
  track_opens: true,
  track_clicks: true,
  groups: [transactional, order-confirmation, premium-customers],
  attachments: null,
  webhook_endpoint: https://your-app.com/webhooks/email-events,
  template_id: null,
  template_variables: null
)
```

