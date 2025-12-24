# Sendpost::Message

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **message_id** | **String** | Unique ID for the message. | [optional] |
| **account_id** | **Integer** | Account ID associated with the message. | [optional] |
| **sub_account_id** | **Integer** | Sub-account ID associated with the message. | [optional] |
| **ip_id** | **Integer** | IP ID used for sending the message. | [optional] |
| **account_ip_pool_id** | **Integer** | Account IP Pool ID associated with the message. | [optional] |
| **public_ip** | **String** | Public IP address used for sending the message. | [optional] |
| **local_ip** | **String** | Local IP address used for sending the message. | [optional] |
| **email_type** | **String** | Type of email service used. | [optional] |
| **submitted_at** | **Integer** | UNIX epoch nano timestamp when message was submitted. | [optional] |
| **from** | [**Person**](.md) | Object comprising name and email address of the sender | [optional] |
| **reply_to** | [**Person**](.md) | Object comprising name and email addresses to which email replies will go to | [optional] |
| **to** | [**MessageTo**](MessageTo.md) |  | [optional] |
| **header_to** | [**MessageHeaderTo**](MessageHeaderTo.md) |  | [optional] |
| **header_cc** | **Array&lt;String&gt;** | List of CC recipients from email headers | [optional] |
| **header_bcc** | **Array&lt;String&gt;** | List of BCC recipients from email headers | [optional] |
| **attachments** | **Array&lt;String&gt;** | List of attachments | [optional] |
| **groups** | **Array&lt;String&gt;** | List of groups associated with the message | [optional] |
| **ip_pool** | **String** | IP Pool from which emails will go out. Relevant only for customers on dedicated IP plans. | [optional] |
| **headers** | **Hash&lt;String, String&gt;** | Key-Value pair which are added to every email message being sent and also with webhooks triggered on events such as email delivered, open, click etc. They are useful to identify email, recipient etc. in your internal system | [optional] |
| **custom_fields** | **Hash&lt;String, String&gt;** | Key-Value pair of custom fields at message level | [optional] |
| **subject** | **String** | Email subject line. | [optional] |
| **pre_text** | **String** | Text which appears on mobile right after email subject line. | [optional] |
| **html_body** | **String** | HTML email content. | [optional] |
| **text_body** | **String** | Text email content. | [optional] |
| **amp_body** | **String** | AMP email content. | [optional] |
| **track_opens** | **Boolean** | Indicates if email opens need to be tracked. | [optional] |
| **track_clicks** | **Boolean** | Indicates if email clicks need to be tracked. | [optional] |
| **attempt** | **Integer** | Number of delivery attempts made for the message. | [optional] |
| **webhook_endpoint** | **String** | Webhook endpoint URL for the message. | [optional] |
| **mx_records** | **Array&lt;String&gt;** | List of MX records for the recipient domain | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Message.new(
  message_id: c486c7e5-4b0b-4ce5-b392-6ac2a453dcb6,
  account_id: 1837,
  sub_account_id: 46499,
  ip_id: 46,
  account_ip_pool_id: 0,
  public_ip: 34.196.37.102,
  local_ip: 10.1.0.195,
  email_type: googleworkspace,
  submitted_at: 1766396394503841392,
  from: null,
  reply_to: null,
  to: null,
  header_to: null,
  header_cc: [],
  header_bcc: null,
  attachments: [],
  groups: [],
  ip_pool: ,
  headers: {X-SendPost-Mock-Email&#x3D;, X-SendPost-Mock-Time-Shift&#x3D;},
  custom_fields: {},
  subject: Test Email from SendPost Java SDK,
  pre_text: ,
  html_body: &lt;h1&gt;Hello from SendPost!&lt;/h1&gt;&lt;p&gt;This is a test email sent using the SendPost Java SDK from Maven Central.&lt;/p&gt;,
  text_body: Hello from SendPost! This is a test email sent using the SendPost Java SDK from Maven Central.,
  amp_body: ,
  track_opens: true,
  track_clicks: true,
  attempt: 0,
  webhook_endpoint: ,
  mx_records: [alt3.aspmx.l.google.com, alt4.aspmx.l.google.com, alt1.aspmx.l.google.com, alt2.aspmx.l.google.com, aspmx.l.google.com]
)
```

