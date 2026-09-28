# Sendpost::EmailApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**send_email**](EmailApi.md#send_email) | **POST** /subaccount/email/ | Send Email |
| [**send_email_with_template**](EmailApi.md#send_email_with_template) | **POST** /subaccount/email/template | Send Email With Template |


## send_email

> <Array<EmailResponse>> send_email(email_message_object)

Send Email

Send transactional or marketing emails to one or multiple recipients. This is the primary endpoint for all email sending through SendPost.  **Capabilities:** - **Single Email**: Send to one recipient with full personalization - **Batch Sending**: Send to up to 500 recipients in a single API call - **Personalization**: Use Handlebars templating (`{{variableName}}`) in subject, HTML body, and text body - **Attachments**: Include base64-encoded files (max 25MB total per request) - **Tracking**: Enable/disable open and click tracking per email - **IP Pool Routing**: Route emails through specific IP pools  **Common Use Cases:**  | Use Case | Example | |----------|---------| | Order Confirmation | Send receipt with order details after purchase | | Password Reset | Time-sensitive security email with reset link | | Welcome Email | Onboard new users with personalized greeting | | Shipping Notification | Update customers when orders ship | | Invoice/Receipt | Attach PDF invoices to billing emails |  **Personalization Example:** ```json {   \"to\": [{     \"email\": \"john@example.com\",     \"customFields\": {       \"firstName\": \"John\",       \"orderTotal\": \"$99.99\"     }   }],   \"subject\": \"Hi {{firstName}}, your order is confirmed!\",   \"htmlBody\": \"<p>Thanks {{firstName}}! Your total: {{orderTotal}}</p>\" } ```  **Test Email Addresses:**  SendPost provides special test email addresses for testing webhooks and events without sending real emails:  | Test Email | Behavior | |------------|----------| | `test@playwithsendpost.io` | Generates delivered event, then simulates opens and clicks after a few seconds | | `deliver@playwithsendpost.io` | Generates delivered event only (no opens/clicks) | | `hardbounce@playwithsendpost.io` | Always generates a hard bounce event | | `softbounce@playwithsendpost.io` | Always generates a soft bounce event | | `dropped@playwithsendpost.io` | Always generates a dropped event (SMTPDropped) |  **Self-Test Email (Send to Yourself):**  Use `hello@playwithsendpost.io` as the **from** address to send emails to yourself for testing:  - **Sender**: Must be `hello@playwithsendpost.io` - **Recipient**: Must be your account owner email (the email you used to sign up) - **Behavior**: Real email delivery to your inbox (no domain verification required, no mock mode) - **Use Case**: Test your API integration by sending real emails to yourself without domain setup  **Example:** ```json {   \"from\": {\"email\": \"hello@playwithsendpost.io\"},   \"to\": [{\"email\": \"your-account-email@example.com\"}],   \"subject\": \"Test Email to Myself\",   \"htmlBody\": \"<p>This is a test email to myself</p>\" } ``` This will send a real email to your inbox that you can actually receive and open.  **Note**: If you send to any email other than your account email, the request will be rejected with an error.  **Using Test Emails:** - Simply send to any test email address like a normal recipient - Mock mode is automatically enabled for test emails - All events trigger webhooks normally - Events are marked as mock messages but follow the same structure as real events - Perfect for testing webhook integrations without using real email addresses  **Example:** ```json {   \"to\": [{\"email\": \"test@playwithsendpost.io\"}],   \"from\": {\"email\": \"sender@example.com\"},   \"subject\": \"Test Email\",   \"htmlBody\": \"<p>This is a test</p>\" } ``` This will generate: Sent → Delivered → Opened (after 2-5s) → Clicked (after 1-3s more)  **Response:** Returns an array of responses, one per recipient, each containing: - `messageId` - Unique ID for tracking - `submittedAt` - Timestamp of acceptance - `errorCode` and `message` - Status information 

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: subAccountAuth
  config.api_key['X-SubAccount-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-SubAccount-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::EmailApi.new
email_message_object = Sendpost::EmailMessageObject.new({from: Sendpost::EmailAddress.new({email: 'sender@example.com'}), to: [Sendpost::Recipient.new({email: 'recipient@example.com'})]}) # EmailMessageObject | Email message details

begin
  # Send Email
  result = api_instance.send_email(email_message_object)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling EmailApi->send_email: #{e}"
end
```

#### Using the send_email_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<EmailResponse>>, Integer, Hash)> send_email_with_http_info(email_message_object)

```ruby
begin
  # Send Email
  data, status_code, headers = api_instance.send_email_with_http_info(email_message_object)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<EmailResponse>>
rescue Sendpost::ApiError => e
  puts "Error when calling EmailApi->send_email_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **email_message_object** | [**EmailMessageObject**](EmailMessageObject.md) | Email message details |  |

### Return type

[**Array&lt;EmailResponse&gt;**](EmailResponse.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## send_email_with_template

> <Array<EmailResponse>> send_email_with_template(email_message_with_template)

Send Email With Template

Send emails using pre-configured templates stored in SendPost. Templates separate email content from code, enabling:  **Benefits:** - Update email content without code deployments - Marketing teams can manage templates independently - Consistent branding across all applications - A/B test different template versions  **How It Works:** 1. Create templates in the SendPost dashboard with Handlebars variables 2. Reference the template by name or ID in this API call 3. Pass dynamic data through recipient `customFields` 4. SendPost merges data with template and sends  **Common Use Cases:**  | Template Type | Dynamic Data | |---------------|--------------| | Welcome Email | `firstName`, `accountType`, `loginUrl` | | Order Receipt | `orderNumber`, `items`, `total`, `shippingAddress` | | Password Reset | `resetLink`, `expiryTime`, `userName` | | Weekly Digest | `articleList`, `unreadCount`, `userName` |  **Example Request:** ```json {   \"from\": { \"email\": \"orders@yourstore.com\" },   \"to\": [{     \"email\": \"customer@example.com\",     \"customFields\": {       \"firstName\": \"Sarah\",       \"orderNumber\": \"ORD-2024-001\",       \"totalAmount\": \"$149.99\"     }   }],   \"template\": \"order-confirmation-v2\" } ```  **Note:** Template variables not provided in `customFields` will render as empty strings. 

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: subAccountAuth
  config.api_key['X-SubAccount-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-SubAccount-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::EmailApi.new
email_message_with_template = Sendpost::EmailMessageWithTemplate.new({from: Sendpost::EmailAddress.new({email: 'sender@example.com'}), to: [Sendpost::Recipient.new({email: 'recipient@example.com'})]}) # EmailMessageWithTemplate | Email message details with template information

begin
  # Send Email With Template
  result = api_instance.send_email_with_template(email_message_with_template)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling EmailApi->send_email_with_template: #{e}"
end
```

#### Using the send_email_with_template_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<EmailResponse>>, Integer, Hash)> send_email_with_template_with_http_info(email_message_with_template)

```ruby
begin
  # Send Email With Template
  data, status_code, headers = api_instance.send_email_with_template_with_http_info(email_message_with_template)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<EmailResponse>>
rescue Sendpost::ApiError => e
  puts "Error when calling EmailApi->send_email_with_template_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **email_message_with_template** | [**EmailMessageWithTemplate**](EmailMessageWithTemplate.md) | Email message details with template information |  |

### Return type

[**Array&lt;EmailResponse&gt;**](EmailResponse.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

