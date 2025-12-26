# SendPost Ruby SDK

A Ruby gem for sending emails and managing your SendPost account programmatically.

## What is SendPost?

SendPost is an email delivery service that helps you send transactional and marketing emails reliably. With SendPost, you can:

- Send personalized emails to multiple recipients
- Track email opens and link clicks
- Monitor email statistics (deliveries, bounces, spam complaints)
- Manage multiple sending domains and IP addresses
- Set up webhooks to receive real-time email event notifications

## Installation

### Install from RubyGems (Recommended)

```bash
gem install sendpost_ruby_sdk
```

### Install from Source

If you're installing from the source code:

```bash
gem build sendpost_ruby_sdk.gemspec
gem install ./sendpost_ruby_sdk-2.0.0.gem
```

### Add to Your Gemfile

Add this line to your application's `Gemfile`:

```ruby
gem 'sendpost_ruby_sdk', '~> 2.0.0'
```

Then run:

```bash
bundle install
```

## Quick Start

### 1. Get Your API Keys

Before you can use the SDK, you need API keys from SendPost:

1. Sign up at [https://app.sendpost.io/register](https://app.sendpost.io/register)
2. Log in to your SendPost dashboard
3. Navigate to API Keys section
4. Copy your **Sub-Account API Key** (for sending emails)
5. Copy your **Account API Key** (for managing sub-accounts, IPs, etc.)

### 2. Configure the SDK

```ruby
require 'sendpost_ruby_sdk'

# Create configuration
config = Sendpost::Configuration.new
config.host = 'https://api.sendpost.io/api/v1'

# Set your Sub-Account API Key (for sending emails)
config.api_key['X-SubAccount-ApiKey'] = 'your_sub_account_api_key_here'
```

### 3. Send Your First Email

```ruby
# Create API client
api_client = Sendpost::ApiClient.new(config)
email_api = Sendpost::EmailApi.new(api_client)

# Create email message
email_message = Sendpost::EmailMessageObject.new

# Set sender
from_addr = Sendpost::EmailMessageFrom.new
from_addr.email = 'sender@yourdomain.com'
from_addr.name = 'Your Name'
email_message.from = from_addr

# Set recipient
recipient = Sendpost::EmailMessageToInner.new
recipient.email = 'recipient@example.com'
recipient.name = 'Recipient Name'
email_message.to = [recipient]

# Set email content
email_message.subject = 'Hello from SendPost!'
email_message.html_body = '<h1>Welcome!</h1><p>This is your first email sent with SendPost Ruby SDK.</p>'
email_message.text_body = 'Welcome! This is your first email sent with SendPost Ruby SDK.'

# Enable tracking
email_message.track_opens = true
email_message.track_clicks = true

# Send the email
begin
  responses = email_api.send_email(email_message)
  if responses && !responses.empty?
    puts "Email sent successfully! Message ID: #{responses[0].message_id}"
  end
rescue Sendpost::ApiError => e
  puts "Error sending email: #{e.code} - #{e.response_body}"
end
```

## Detailed Usage Guide

### Understanding API Keys

SendPost uses two types of API keys:

**Sub-Account API Key (`X-SubAccount-ApiKey`)**
- Used for: Sending emails, managing domains, viewing sub-account statistics
- Where to find: SendPost Dashboard → Sub-Accounts → API Keys

**Account API Key (`X-Account-ApiKey`)**
- Used for: Creating sub-accounts, managing IPs, creating webhooks, account-level statistics
- Where to find: SendPost Dashboard → Account Settings → API Keys

### Sending Emails

#### Basic Email

```ruby
require 'sendpost_ruby_sdk'

# Setup
config = Sendpost::Configuration.new
config.host = 'https://api.sendpost.io/api/v1'
config.api_key['X-SubAccount-ApiKey'] = 'your_sub_account_api_key'

api_client = Sendpost::ApiClient.new(config)
email_api = Sendpost::EmailApi.new(api_client)

# Create message
email_message = Sendpost::EmailMessageObject.new

# From address
from = Sendpost::EmailMessageFrom.new
from.email = 'noreply@yourdomain.com'
from.name = 'Your Company'
email_message.from = from

# To address
to = Sendpost::EmailMessageToInner.new
to.email = 'customer@example.com'
to.name = 'Customer Name'
email_message.to = [to]

# Email content
email_message.subject = 'Order Confirmation'
email_message.html_body = '<h1>Thank you for your order!</h1>'
email_message.text_body = 'Thank you for your order!'

# Send
responses = email_api.send_email(email_message)
puts "Sent! Message ID: #{responses[0].message_id}"
```

#### Email with Multiple Recipients

```ruby
# Create multiple recipients
recipient1 = Sendpost::EmailMessageToInner.new
recipient1.email = 'user1@example.com'
recipient1.name = 'User One'

recipient2 = Sendpost::EmailMessageToInner.new
recipient2.email = 'user2@example.com'
recipient2.name = 'User Two'

# Add CC recipients
cc_recipient = Sendpost::EmailMessageToInnerCcInner.new
cc_recipient.email = 'cc@example.com'
recipient1.cc = [cc_recipient]

# Add BCC recipients
bcc_recipient = Sendpost::EmailMessageToInnerBccInner.new
bcc_recipient.email = 'bcc@example.com'
recipient1.bcc = [bcc_recipient]

# Set all recipients
email_message.to = [recipient1, recipient2]
```

#### Email with Attachments

```ruby
# Create attachment
attachment = Sendpost::Attachment.new
attachment.name = 'invoice.pdf'
attachment.content = Base64.encode64(File.read('path/to/invoice.pdf'))
attachment.content_type = 'application/pdf'

email_message.attachments = [attachment]
```

#### Email with Custom Fields and Headers

```ruby
# Add custom fields to recipient (for personalization)
recipient = Sendpost::EmailMessageToInner.new
recipient.email = 'customer@example.com'
recipient.custom_fields = {
  'customer_id' => '12345',
  'order_number' => 'ORD-67890',
  'total_amount' => '99.99'
}

# Add custom headers
email_message.headers = {
  'X-Order-ID' => '12345',
  'X-Email-Type' => 'transactional'
}

# Add groups for analytics
email_message.groups = ['transactional', 'order-confirmation']
```

#### Email with Reply-To

```ruby
reply_to = Sendpost::EmailMessageReplyTo.new
reply_to.email = 'support@yourdomain.com'
reply_to.name = 'Support Team'
email_message.reply_to = reply_to
```

### Managing Domains

Before sending emails, you need to add and verify your sending domain.

#### Add a Domain

```ruby
# Use Sub-Account API Key
config = Sendpost::Configuration.new
config.host = 'https://api.sendpost.io/api/v1'
config.api_key['X-SubAccount-ApiKey'] = 'your_sub_account_api_key'

api_client = Sendpost::ApiClient.new(config)
domain_api = Sendpost::DomainApi.new(api_client)

# Create domain request
domain_request = Sendpost::CreateDomainRequest.new
domain_request.name = 'yourdomain.com'

# Add domain
domain = domain_api.subaccount_domain_post(domain_request)

puts "Domain added! ID: #{domain.id}"
puts "DKIM Record: #{domain.dkim.text_value}" if domain.dkim

# IMPORTANT: Add the DNS records shown to your domain's DNS settings
```

#### List All Domains

```ruby
domains = domain_api.get_all_domains

domains.each do |domain|
  puts "Domain: #{domain.name}"
  puts "Verified: #{domain.verified ? 'Yes' : 'No'}"
  puts "---"
end
```

#### Get Domain Details

```ruby
domain_id = 'your_domain_id'
domain = domain_api.subaccount_domain_domain_id_get(domain_id)

puts "Domain: #{domain.name}"
puts "Verified: #{domain.verified}"
puts "DKIM: #{domain.dkim.text_value}" if domain.dkim
```

### Viewing Statistics

#### Get Sub-Account Statistics

```ruby
require 'date'

# Use Account API Key for statistics
config = Sendpost::Configuration.new
config.host = 'https://api.sendpost.io/api/v1'
config.api_key['X-Account-ApiKey'] = 'your_account_api_key'

api_client = Sendpost::ApiClient.new(config)
stats_api = Sendpost::StatsApi.new(api_client)

# Get stats for last 7 days
sub_account_id = 'your_sub_account_id'
to_date = Date.today
from_date = to_date - 7

stats = stats_api.account_subaccount_stat_subaccount_id_get(
  from_date, 
  to_date, 
  sub_account_id
)

stats.each do |stat|
  puts "Date: #{stat.date}"
  if stat.stats
    puts "  Processed: #{stat.stats.processed || 0}"
    puts "  Delivered: #{stat.stats.delivered || 0}"
    puts "  Opened: #{stat.stats.opened || 0}"
    puts "  Clicked: #{stat.stats.clicked || 0}"
    puts "  Bounced: #{stat.stats.hard_bounced || 0}"
    puts "  Spam: #{stat.stats.spam || 0}"
  end
  puts "---"
end
```

#### Get Aggregate Statistics

```ruby
# Get overall stats for a sub-account
aggregate_stat = stats_api.account_subaccount_stat_subaccount_id_aggregate_get(
  from_date,
  to_date,
  sub_account_id
)

puts "Total Processed: #{aggregate_stat.processed || 0}"
puts "Total Delivered: #{aggregate_stat.delivered || 0}"
puts "Total Opened: #{aggregate_stat.opened || 0}"
puts "Total Clicked: #{aggregate_stat.clicked || 0}"
```

#### Get Account-Level Statistics

```ruby
# Use StatsAApi for account-level stats
stats_a_api = Sendpost::StatsAApi.new(api_client)

account_stats = stats_a_api.get_all_account_stats(from_date, to_date)

account_stats.each do |stat|
  puts "Date: #{stat.date}"
  if stat.stat
    puts "  Processed: #{stat.stat.processed || 0}"
    puts "  Delivered: #{stat.stat.delivered || 0}"
  end
end
```

### Managing Sub-Accounts

#### List All Sub-Accounts

```ruby
# Use Account API Key
config = Sendpost::Configuration.new
config.host = 'https://api.sendpost.io/api/v1'
config.api_key['X-Account-ApiKey'] = 'your_account_api_key'

api_client = Sendpost::ApiClient.new(config)
sub_account_api = Sendpost::SubAccountApi.new(api_client)

sub_accounts = sub_account_api.get_all_sub_accounts

sub_accounts.each do |sub_account|
  puts "ID: #{sub_account.id}"
  puts "Name: #{sub_account.name}"
  puts "API Key: #{sub_account.api_key}"
  puts "---"
end
```

#### Create a Sub-Account

```ruby
new_sub_account = Sendpost::CreateSubAccountRequest.new
new_sub_account.name = "Client Account - #{Time.now.to_i}"

sub_account = sub_account_api.create_sub_account(new_sub_account)

puts "Created! ID: #{sub_account.id}"
puts "API Key: #{sub_account.api_key}"
```

#### Get Sub-Account Details

```ruby
sub_account_id = 'your_sub_account_id'
sub_account = sub_account_api.get_sub_account(sub_account_id)

puts "Name: #{sub_account.name}"
puts "Type: #{sub_account.type}"
puts "Blocked: #{sub_account.blocked}"
```

### Managing Webhooks

Webhooks allow you to receive real-time notifications when email events occur.

#### Create a Webhook

```ruby
# Use Account API Key
config = Sendpost::Configuration.new
config.host = 'https://api.sendpost.io/api/v1'
config.api_key['X-Account-ApiKey'] = 'your_account_api_key'

api_client = Sendpost::ApiClient.new(config)
webhook_api = Sendpost::WebhookApi.new(api_client)

# Create webhook request
webhook_request = Sendpost::CreateWebhookRequest.new
webhook_request.url = 'https://your-app.com/webhooks/sendpost'
webhook_request.enabled = true

# Configure which events to receive
webhook_request.processed = true      # Email processed
webhook_request.delivered = true      # Email delivered
webhook_request.dropped = true       # Email dropped
webhook_request.soft_bounced = true  # Soft bounce
webhook_request.hard_bounced = true  # Hard bounce
webhook_request.opened = true        # Email opened
webhook_request.clicked = true       # Link clicked
webhook_request.unsubscribed = true  # Unsubscribed
webhook_request.spam = true          # Marked as spam

webhook = webhook_api.create_webhook(webhook_request)

puts "Webhook created! ID: #{webhook.id}"
```

#### List All Webhooks

```ruby
webhooks = webhook_api.get_all_webhooks

webhooks.each do |webhook|
  puts "ID: #{webhook.id}"
  puts "URL: #{webhook.url}"
  puts "Enabled: #{webhook.enabled}"
  puts "---"
end
```

### Retrieving Message Details

```ruby
# Use Account API Key
config = Sendpost::Configuration.new
config.host = 'https://api.sendpost.io/api/v1'
config.api_key['X-Account-ApiKey'] = 'your_account_api_key'

api_client = Sendpost::ApiClient.new(config)
message_api = Sendpost::MessageApi.new(api_client)

# Get message by ID (from email send response)
message_id = 'your_message_id'
message = message_api.get_message_by_id(message_id)

puts "Message ID: #{message.message_id}"
puts "From: #{message.from.email}" if message.from
puts "To: #{message.to.email}" if message.to
puts "Subject: #{message.subject}"
puts "Submitted At: #{message.submitted_at}"
puts "IP Used: #{message.public_ip}"
```

### Managing Suppressions

Suppressions are email addresses that should not receive emails (unsubscribed, bounced, etc.).

#### Add Suppressions

```ruby
# Use Sub-Account API Key
config = Sendpost::Configuration.new
config.host = 'https://api.sendpost.io/api/v1'
config.api_key['X-SubAccount-ApiKey'] = 'your_sub_account_api_key'

api_client = Sendpost::ApiClient.new(config)
suppression_api = Sendpost::SuppressionApi.new(api_client)

# Create suppression request
suppression_request = Sendpost::CreateSuppressionRequest.new

# Add hard bounces
hard_bounce = Sendpost::CreateSuppressionRequestHardBounceInner.new
hard_bounce.email = 'bounced@example.com'
suppression_request.hard_bounce = [hard_bounce]

# Add unsubscribes
unsubscribe = Sendpost::CreateSuppressionRequestUnsubscribeInner.new
unsubscribe.email = 'unsubscribed@example.com'
suppression_request.unsubscribe = [unsubscribe]

# Add spam complaints
spam = Sendpost::CreateSuppressionRequestSpamComplaintInner.new
spam.email = 'spam@example.com'
suppression_request.spam_complaint = [spam]

# Add manual suppressions
manual = Sendpost::CreateSuppressionRequestManualInner.new
manual.email = 'manual@example.com'
suppression_request.manual = [manual]

suppression_api.create_suppression(suppression_request)
puts "Suppressions added successfully"
```

#### List Suppressions

```ruby
to_date = Date.today
from_date = to_date - 7

suppressions = suppression_api.get_suppression_list(from_date, to_date)

suppressions.each do |suppression|
  puts "Email: #{suppression.email}"
  puts "Type: #{suppression.type}"
  puts "---"
end
```

## Error Handling

The SDK raises `Sendpost::ApiError` when API calls fail. Always wrap API calls in begin/rescue blocks:

```ruby
begin
  responses = email_api.send_email(email_message)
  puts "Success!"
rescue Sendpost::ApiError => e
  puts "API Error:"
  puts "  Status Code: #{e.code}"
  puts "  Response: #{e.response_body}"
  
  case e.code
  when 401
    puts "  Issue: Invalid or missing API key"
  when 403
    puts "  Issue: Resource already exists or insufficient permissions"
  when 404
    puts "  Issue: Resource not found"
  when 422
    puts "  Issue: Invalid request data"
  when 500
    puts "  Issue: SendPost server error"
  end
rescue StandardError => e
  puts "Unexpected error: #{e.message}"
end
```

### Common HTTP Status Codes

| Code | Meaning | What to Do |
|------|---------|------------|
| 200 | Success | Everything worked |
| 401 | Unauthorized | Check your API key |
| 403 | Forbidden | Resource exists or no permission |
| 404 | Not Found | Resource ID doesn't exist |
| 422 | Invalid Data | Check your request body |
| 500 | Server Error | Try again later |
| 503 | Service Unavailable | SendPost is down for maintenance |

## Complete Example

Here's a complete example that demonstrates common operations:

```ruby
#!/usr/bin/env ruby
require 'sendpost_ruby_sdk'
require 'date'

# Configuration
SUB_ACCOUNT_API_KEY = ENV['SENDPOST_SUB_ACCOUNT_API_KEY'] || 'your_key_here'
ACCOUNT_API_KEY = ENV['SENDPOST_ACCOUNT_API_KEY'] || 'your_key_here'

# Setup Sub-Account API (for sending emails)
sub_config = Sendpost::Configuration.new
sub_config.host = 'https://api.sendpost.io/api/v1'
sub_config.api_key['X-SubAccount-ApiKey'] = SUB_ACCOUNT_API_KEY

sub_api_client = Sendpost::ApiClient.new(sub_config)
email_api = Sendpost::EmailApi.new(sub_api_client)

# Setup Account API (for managing resources)
account_config = Sendpost::Configuration.new
account_config.host = 'https://api.sendpost.io/api/v1'
account_config.api_key['X-Account-ApiKey'] = ACCOUNT_API_KEY

account_api_client = Sendpost::ApiClient.new(account_config)

# Send an email
email_message = Sendpost::EmailMessageObject.new

from = Sendpost::EmailMessageFrom.new
from.email = 'sender@yourdomain.com'
from.name = 'Your Company'
email_message.from = from

to = Sendpost::EmailMessageToInner.new
to.email = 'recipient@example.com'
to.name = 'Recipient'
email_message.to = [to]

email_message.subject = 'Test Email'
email_message.html_body = '<h1>Hello!</h1><p>This is a test email.</p>'
email_message.text_body = 'Hello! This is a test email.'
email_message.track_opens = true
email_message.track_clicks = true

begin
  responses = email_api.send_email(email_message)
  message_id = responses[0].message_id
  puts "Email sent! Message ID: #{message_id}"
  
  # Get message details
  message_api = Sendpost::MessageApi.new(account_api_client)
  message = message_api.get_message_by_id(message_id)
  puts "Message details retrieved successfully"
  
rescue Sendpost::ApiError => e
  puts "Error: #{e.code} - #{e.response_body}"
end
```

## API Reference

For complete API documentation, see the [API Reference](docs/) directory. Key API classes:

- `Sendpost::EmailApi` - Send emails
- `Sendpost::DomainApi` - Manage domains
- `Sendpost::SubAccountApi` - Manage sub-accounts
- `Sendpost::StatsApi` - View statistics
- `Sendpost::WebhookApi` - Manage webhooks
- `Sendpost::SuppressionApi` - Manage suppressions
- `Sendpost::MessageApi` - Retrieve message details

## Requirements

- Ruby 2.7 or higher
- Internet connection

## Getting Help

- **Documentation**: [https://docs.sendpost.io](https://docs.sendpost.io)
- **Email Support**: hello@sendpost.io
- **Website**: [https://sendpost.io](https://sendpost.io)
- **Developer Portal**: [https://app.sendpost.io](https://app.sendpost.io)

## License

This SDK is provided under the Unlicense. See LICENSE file for details.

## Version

Current version: 2.0.0

Generated by [OpenAPI Generator](https://openapi-generator.tech)
