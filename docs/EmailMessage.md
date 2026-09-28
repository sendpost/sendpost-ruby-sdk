# Sendpost::EmailMessage

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **message_id** | **String** | Unique identifier for this email message | [optional] |
| **account_id** | **Integer** | ID of the SendPost account that sent this email | [optional] |
| **sub_account_id** | **Integer** | ID of the sub-account that sent this email | [optional] |
| **ip_id** | **Integer** | ID of the dedicated IP used for sending (0 if a shared IP was used) | [optional] |
| **public_ip** | **String** | The public IP address used to send this email | [optional] |
| **local_ip** | **String** | The internal/local IP address used to send this email | [optional] |
| **email_type** | **String** | Classification of the email based on recipient domain: - &#x60;gmail&#x60; - Gmail recipient - &#x60;yahoo&#x60; - Yahoo recipient - &#x60;microsoft&#x60; - Outlook/Hotmail recipient - &#x60;default&#x60; - Other email providers  | [optional] |
| **submitted_at** | **Integer** | UNIX epoch timestamp in nanoseconds when the email was submitted | [optional] |
| **from** | [**EmailAddress**](EmailAddress.md) | The sender&#39;s email address | [optional] |
| **reply_to** | [**EmailAddress**](EmailAddress.md) | The reply-to address (if different from sender) | [optional] |
| **to** | [**Recipient**](Recipient.md) | The envelope recipient (actual delivery address) | [optional] |
| **groups** | **Array&lt;String&gt;** | Tags/groups for categorization and analytics | [optional] |
| **ip_pool** | **String** | Name of the IP pool used for sending | [optional] |
| **headers** | **Hash&lt;String, String&gt;** | Custom headers included in the email | [optional] |
| **custom_fields** | **Hash&lt;String, Object&gt;** | Custom fields sent with the email, available for personalization | [optional] |
| **track_opens** | **Boolean** | Whether open tracking was enabled | [optional] |
| **track_clicks** | **Boolean** | Whether click tracking was enabled | [optional] |
| **webhook_endpoint** | **String** | Custom webhook endpoint for this email (if specified) | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EmailMessage.new(
  message_id: 550e8400-e29b-41d4-a716-446655440000,
  account_id: 100,
  sub_account_id: 50441,
  ip_id: 11321,
  public_ip: 52.34.11.12,
  local_ip: 10.0.1.5,
  email_type: gmail,
  submitted_at: 1704067200000000000,
  from: null,
  reply_to: null,
  to: null,
  groups: [transactional, order-confirmation],
  ip_pool: transactional,
  headers: {X-Campaign-ID&#x3D;summer-sale-2024, List-Unsubscribe&#x3D;&lt;mailto:unsubscribe@piedpiper.com&gt;},
  custom_fields: {&quot;firstName&quot;:&quot;John&quot;,&quot;orderId&quot;:&quot;12345&quot;},
  track_opens: true,
  track_clicks: true,
  webhook_endpoint: https://piedpiper.com/webhooks/email
)
```

