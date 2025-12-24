# Sendpost::EmailApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**send_email**](EmailApi.md#send_email) | **POST** /subaccount/email/ | Send Email |
| [**send_email_with_template**](EmailApi.md#send_email_with_template) | **POST** /subaccount/email/template | Send Email With Template |


## send_email

> <Array<EmailResponse>> send_email(email_message_object)

Send Email

Use this API to send either a single or batch email.

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
email_message_object = Sendpost::EmailMessageObject.new # EmailMessageObject | Email message details

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

Use this API to send an email with a predefined template. This makes it easy to integrate transactional emails with minimal code. 

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
email_message_with_template = Sendpost::EmailMessageWithTemplate.new # EmailMessageWithTemplate | Email message details with template information

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

