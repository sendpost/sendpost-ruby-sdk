# Sendpost::SuppressionApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_suppression**](SuppressionApi.md#create_suppression) | **POST** /subaccount/suppression | Create Suppressions |
| [**delete_suppression**](SuppressionApi.md#delete_suppression) | **DELETE** /subaccount/suppression | Delete Suppressions |
| [**get_suppression_list**](SuppressionApi.md#get_suppression_list) | **GET** /subaccount/suppression | List Suppressions |


## create_suppression

> <Array<Suppression>> create_suppression(create_suppression_request)

Create Suppressions

Add email addresses to your suppression list to prevent future emails from being sent. This is essential for maintaining sender reputation and compliance.  **When to Use Each Type:** | Type | Use When | |------|----------| | `hardBounce` | You know an address is permanently invalid | | `manual` | Processing do-not-contact requests from support | | `unsubscribe` | Syncing unsubscribes from external systems | | `spamComplaint` | Importing complaints from other providers |  **Common Use Cases:** - **Migration:** Import suppression list from previous email provider - **CRM Sync:** Add unsubscribes from your marketing platform - **Bulk Cleanup:** Add known invalid addresses from data cleaning - **Support Tickets:** Honor do-not-contact requests  **Best Practices:** - Import historical bounce data when migrating providers - Sync unsubscribes immediately when received from external sources - Process support-requested suppressions within 24 hours - Use `manual` for addresses you want to suppress without categorization 

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

api_instance = Sendpost::SuppressionApi.new
create_suppression_request = Sendpost::CreateSuppressionRequest.new # CreateSuppressionRequest | 

begin
  # Create Suppressions
  result = api_instance.create_suppression(create_suppression_request)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->create_suppression: #{e}"
end
```

#### Using the create_suppression_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<Suppression>>, Integer, Hash)> create_suppression_with_http_info(create_suppression_request)

```ruby
begin
  # Create Suppressions
  data, status_code, headers = api_instance.create_suppression_with_http_info(create_suppression_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<Suppression>>
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->create_suppression_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **create_suppression_request** | [**CreateSuppressionRequest**](CreateSuppressionRequest.md) |  |  |

### Return type

[**Array&lt;Suppression&gt;**](Suppression.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_suppression

> <DeleteSuppression200Response> delete_suppression(delete_suppression_request)

Delete Suppressions

Remove email addresses from your suppression list, allowing them to receive emails again.  **⚠️ Important: Use with caution!** Re-enabling sending to previously suppressed addresses can harm your sender reputation if used incorrectly.  **Valid Use Cases:** - User confirms their valid email was incorrectly bounced - Manual suppression was added by mistake - User explicitly requests re-subscription after unsubscribing - Testing/development addresses that were suppressed  **Not Recommended:** - Bulk removing hard bounces without individual verification - Removing spam complaints (users rarely want to receive emails again) - Attempting to re-engage addresses that bounced  **Best Practice:** Before removing a suppression, verify with the recipient that they want to receive emails and that their address is valid. 

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

api_instance = Sendpost::SuppressionApi.new
delete_suppression_request = Sendpost::DeleteSuppressionRequest.new # DeleteSuppressionRequest | 

begin
  # Delete Suppressions
  result = api_instance.delete_suppression(delete_suppression_request)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->delete_suppression: #{e}"
end
```

#### Using the delete_suppression_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<DeleteSuppression200Response>, Integer, Hash)> delete_suppression_with_http_info(delete_suppression_request)

```ruby
begin
  # Delete Suppressions
  data, status_code, headers = api_instance.delete_suppression_with_http_info(delete_suppression_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <DeleteSuppression200Response>
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->delete_suppression_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **delete_suppression_request** | [**DeleteSuppressionRequest**](DeleteSuppressionRequest.md) |  |  |

### Return type

[**DeleteSuppression200Response**](DeleteSuppression200Response.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## get_suppression_list

> <Array<Suppression>> get_suppression_list(from, to, opts)

List Suppressions

Retrieve the suppression list for your sub-account. Suppressions are email addresses that should not receive emails to protect your sender reputation and ensure compliance.  **Suppression Types:** | Type | Reason Code | Description | |------|-------------|-------------| | `manual` | 0 | Manually added by your team | | `unsubscribe` | 1 | User clicked unsubscribe link | | `hardBounce` | 2 | Permanent delivery failure (invalid address) | | `spamComplaint` | 3 | User marked email as spam |  **Why Suppressions Matter:** - **Reputation Protection:** Repeatedly sending to bounced addresses damages sender reputation - **Compliance:** Required for CAN-SPAM, GDPR, and other regulations - **Cost Savings:** Avoid paying to send undeliverable emails - **Deliverability:** ISPs penalize senders with high bounce/complaint rates  **Use Cases:** - Export suppression list for compliance audits - Sync suppressions with your CRM or marketing platform - Review recent bounces to identify data quality issues - Monitor spam complaints for content/targeting problems  **Pagination:** Use `limit` and `offset` for large suppression lists.  **Note:** Maximum date range is 60 days. 

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

api_instance = Sendpost::SuppressionApi.new
from = Date.parse('2024-01-01') # Date | Start date for suppression records (inclusive). Format YYYY-MM-DD.
to = Date.parse('2024-01-31') # Date | End date for suppression records (inclusive). Max 60 days from `from` date.
opts = {
  limit: 50, # Integer | Number of records to return per request. Default 20, max 100.
  offset: 0, # Integer | Number of initial records to skip for pagination.
  search: '@example.com', # String | Case-insensitive search against suppression email addresses.
  type: 'hardBounce' # String | Filter by suppression type. Omit to return all types.
}

begin
  # List Suppressions
  result = api_instance.get_suppression_list(from, to, opts)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->get_suppression_list: #{e}"
end
```

#### Using the get_suppression_list_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<Suppression>>, Integer, Hash)> get_suppression_list_with_http_info(from, to, opts)

```ruby
begin
  # List Suppressions
  data, status_code, headers = api_instance.get_suppression_list_with_http_info(from, to, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<Suppression>>
rescue Sendpost::ApiError => e
  puts "Error when calling SuppressionApi->get_suppression_list_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **from** | **Date** | Start date for suppression records (inclusive). Format YYYY-MM-DD. |  |
| **to** | **Date** | End date for suppression records (inclusive). Max 60 days from &#x60;from&#x60; date. |  |
| **limit** | **Integer** | Number of records to return per request. Default 20, max 100. | [optional][default to 20] |
| **offset** | **Integer** | Number of initial records to skip for pagination. | [optional][default to 0] |
| **search** | **String** | Case-insensitive search against suppression email addresses. | [optional] |
| **type** | **String** | Filter by suppression type. Omit to return all types. | [optional] |

### Return type

[**Array&lt;Suppression&gt;**](Suppression.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

