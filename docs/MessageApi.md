# Sendpost::MessageApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_all_messages**](MessageApi.md#get_all_messages) | **GET** /account/message | List Messages |
| [**get_message_by_id**](MessageApi.md#get_message_by_id) | **GET** /account/message/{message_id} | Get Message |


## get_all_messages

> <Array<Message>> get_all_messages(from, to, opts)

List Messages

Retrieve a paginated list of all email messages sent through your account. Each message includes delivery status, timestamps, and metadata.  **Message Information Includes:** - Sender and recipient details - Subject line and message ID - Delivery status (delivered, bounced, opened, etc.) - Timestamps for each event - IP address and pool used for sending  **Use Cases:** - Search for specific emails sent to customers - Debug delivery issues for specific recipients - Audit email delivery for compliance - Export message logs for analysis - Customer support - lookup specific email by recipient  **Example:** Find all emails to a specific domain in the last week: ``` GET /account/message?from=2024-01-01T00:00:00Z&to=2024-01-07T23:59:59Z ```  **Note:** Maximum date range is 60 days. 

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: accountAuth
  config.api_key['X-Account-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-Account-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::MessageApi.new
from = Time.parse('2024-01-01T00:00:00Z') # Time | Start timestamp for message retrieval. ISO 8601 format.
to = Time.parse('2024-01-31T23:59:59Z') # Time | End timestamp for message retrieval. Max 60 days from `from`.
opts = {
  limit: 50, # Integer | Number of records to return per request. Default 50, max 100.
  offset: 0 # Integer | Number of initial records to skip for pagination.
}

begin
  # List Messages
  result = api_instance.get_all_messages(from, to, opts)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling MessageApi->get_all_messages: #{e}"
end
```

#### Using the get_all_messages_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<Message>>, Integer, Hash)> get_all_messages_with_http_info(from, to, opts)

```ruby
begin
  # List Messages
  data, status_code, headers = api_instance.get_all_messages_with_http_info(from, to, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<Message>>
rescue Sendpost::ApiError => e
  puts "Error when calling MessageApi->get_all_messages_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **from** | **Time** | Start timestamp for message retrieval. ISO 8601 format. |  |
| **to** | **Time** | End timestamp for message retrieval. Max 60 days from &#x60;from&#x60;. |  |
| **limit** | **Integer** | Number of records to return per request. Default 50, max 100. | [optional][default to 50] |
| **offset** | **Integer** | Number of initial records to skip for pagination. | [optional][default to 0] |

### Return type

[**Array&lt;Message&gt;**](Message.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_message_by_id

> <Message> get_message_by_id(message_id)

Get Message

Retrieve complete details about a specific email message, including full event timeline and metadata.  **Response Includes:** - Full message details (sender, recipients, subject) - Complete event timeline (submitted, sent, delivered, opened, clicked) - Bounce/drop information with reasons - IP and pool used for sending - Click and open tracking data  **Use Cases:** - Debug why a specific email wasn't delivered - Customer support - provide delivery proof - Audit trail for compliance requirements - Analyze engagement for specific messages 

### Examples

```ruby
require 'time'
require 'sendpost_ruby_sdk'
# setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: accountAuth
  config.api_key['X-Account-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-Account-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::MessageApi.new
message_id = 'msg_01H2X3Y4Z5A6B7C8D9E0F1G2H3' # String | The unique message ID returned when the email was sent.

begin
  # Get Message
  result = api_instance.get_message_by_id(message_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling MessageApi->get_message_by_id: #{e}"
end
```

#### Using the get_message_by_id_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Message>, Integer, Hash)> get_message_by_id_with_http_info(message_id)

```ruby
begin
  # Get Message
  data, status_code, headers = api_instance.get_message_by_id_with_http_info(message_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Message>
rescue Sendpost::ApiError => e
  puts "Error when calling MessageApi->get_message_by_id_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **message_id** | **String** | The unique message ID returned when the email was sent. |  |

### Return type

[**Message**](Message.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

