# Sendpost::SubAccountApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_sub_account**](SubAccountApi.md#create_sub_account) | **POST** /account/subaccount/ | Create Sub-Account |
| [**delete_sub_account**](SubAccountApi.md#delete_sub_account) | **DELETE** /account/subaccount/{subaccount_id} | Delete Sub-Account |
| [**get_all_sub_accounts**](SubAccountApi.md#get_all_sub_accounts) | **GET** /account/subaccount/ | List Sub-Accounts |
| [**get_sub_account**](SubAccountApi.md#get_sub_account) | **GET** /account/subaccount/{subaccount_id} | Get Sub-Account |
| [**update_sub_account**](SubAccountApi.md#update_sub_account) | **PUT** /account/subaccount/{subaccount_id} | Update Sub-Account |


## create_sub_account

> <SubAccount> create_sub_account(new_sub_account)

Create Sub-Account

Create a new sub-account to segment your email sending. Each sub-account gets its own API key, suppression list, and statistics.  **What You Get:** - Unique `X-SubAccount-ApiKey` for authentication - Isolated email statistics - Separate suppression management - Independent domain configuration - Optional SMTP credentials  **Naming Best Practices:** - Use descriptive names: `Transactional_Orders`, `Marketing_Newsletter` - Include environment: `Production_Alerts`, `Staging_Tests` - For multi-tenant: `Client_CompanyName`  **Use Cases:** - New application or microservice needing email - Onboarding a new client in multi-tenant setup - Creating isolated testing environment - Separating email streams for analytics 

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

api_instance = Sendpost::SubAccountApi.new
new_sub_account = Sendpost::NewSubAccount.new({name: 'Marketing - Production'}) # NewSubAccount | 

begin
  # Create Sub-Account
  result = api_instance.create_sub_account(new_sub_account)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->create_sub_account: #{e}"
end
```

#### Using the create_sub_account_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<SubAccount>, Integer, Hash)> create_sub_account_with_http_info(new_sub_account)

```ruby
begin
  # Create Sub-Account
  data, status_code, headers = api_instance.create_sub_account_with_http_info(new_sub_account)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <SubAccount>
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->create_sub_account_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **new_sub_account** | [**NewSubAccount**](NewSubAccount.md) |  |  |

### Return type

[**SubAccount**](SubAccount.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_sub_account

> <DeleteSubAccountResponse> delete_sub_account(subaccount_id)

Delete Sub-Account

Remove a sub-account from your organization. This action is irreversible.  **⚠️ Before Deleting:** - Export any needed statistics or suppression lists - Update applications using this sub-account's API key - Ensure no active email sending relies on this sub-account  **What Gets Deleted:** - All sub-account configuration - Associated API keys (will stop working) - Statistics are retained for your account records  **Note:** The default sub-account (type `0`) cannot be deleted. 

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

api_instance = Sendpost::SubAccountApi.new
subaccount_id = 12 # Integer | The unique ID of the sub-account to delete.

begin
  # Delete Sub-Account
  result = api_instance.delete_sub_account(subaccount_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->delete_sub_account: #{e}"
end
```

#### Using the delete_sub_account_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<DeleteSubAccountResponse>, Integer, Hash)> delete_sub_account_with_http_info(subaccount_id)

```ruby
begin
  # Delete Sub-Account
  data, status_code, headers = api_instance.delete_sub_account_with_http_info(subaccount_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <DeleteSubAccountResponse>
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->delete_sub_account_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **subaccount_id** | **Integer** | The unique ID of the sub-account to delete. |  |

### Return type

[**DeleteSubAccountResponse**](DeleteSubAccountResponse.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_all_sub_accounts

> <Array<SubAccount>> get_all_sub_accounts(opts)

List Sub-Accounts

Retrieve all sub-accounts under your main account. Sub-accounts allow you to segment email sending for different applications, brands, or use cases.  **Sub-Account Types:** | Type | Value | Description | |------|-------|-------------| | Default | `0` | Primary sub-account created with your account (cannot be deleted) | | Custom | `1` | Additional sub-accounts you create |  **Each Sub-Account Has:** - Unique `X-SubAccount-ApiKey` for API authentication - Independent suppression list - Isolated email statistics - Own domain configurations - SMTP credentials (if enabled)  **Use Cases:** - Separate transactional and marketing emails - Multi-tenant SaaS applications (one sub-account per customer) - Different brands or product lines - Development/staging/production environments  **Note:** `isPlus` indicates SendX Plus customers with premium features. 

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

api_instance = Sendpost::SubAccountApi.new
opts = {
  limit: 10, # Integer | Number of records to return per request. Default 20.
  offset: 0, # Integer | Number of initial records to skip for pagination.
  search: 'Production' # String | Case-insensitive search against sub-account names.
}

begin
  # List Sub-Accounts
  result = api_instance.get_all_sub_accounts(opts)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->get_all_sub_accounts: #{e}"
end
```

#### Using the get_all_sub_accounts_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<SubAccount>>, Integer, Hash)> get_all_sub_accounts_with_http_info(opts)

```ruby
begin
  # List Sub-Accounts
  data, status_code, headers = api_instance.get_all_sub_accounts_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<SubAccount>>
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->get_all_sub_accounts_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **limit** | **Integer** | Number of records to return per request. Default 20. | [optional][default to 20] |
| **offset** | **Integer** | Number of initial records to skip for pagination. | [optional][default to 0] |
| **search** | **String** | Case-insensitive search against sub-account names. | [optional] |

### Return type

[**Array&lt;SubAccount&gt;**](SubAccount.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_sub_account

> <SubAccount> get_sub_account(subaccount_id)

Get Sub-Account

Retrieve detailed information about a specific sub-account, including API keys, SMTP credentials, and configuration.  **Response Includes:** - Sub-account name and ID - API key for sub-account authentication - SMTP credentials (if enabled) - Team members with access - Labels/tags for categorization - Creation timestamp 

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

api_instance = Sendpost::SubAccountApi.new
subaccount_id = 11 # Integer | The unique ID of the sub-account to retrieve.

begin
  # Get Sub-Account
  result = api_instance.get_sub_account(subaccount_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->get_sub_account: #{e}"
end
```

#### Using the get_sub_account_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<SubAccount>, Integer, Hash)> get_sub_account_with_http_info(subaccount_id)

```ruby
begin
  # Get Sub-Account
  data, status_code, headers = api_instance.get_sub_account_with_http_info(subaccount_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <SubAccount>
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->get_sub_account_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **subaccount_id** | **Integer** | The unique ID of the sub-account to retrieve. |  |

### Return type

[**SubAccount**](SubAccount.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## update_sub_account

> <SubAccount> update_sub_account(update_sub_account, subaccount_id)

Update Sub-Account

Modify settings for an existing sub-account. Use this to rename sub-accounts, update labels, or modify configuration.  **What Can Be Updated:** - Sub-account name - Labels/tags for categorization - Other configuration settings  **Use Cases:** - Rename sub-account for clarity - Update labels for organizational changes - Modify settings after initial setup 

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

api_instance = Sendpost::SubAccountApi.new
update_sub_account = Sendpost::UpdateSubAccount.new # UpdateSubAccount | 
subaccount_id = 12 # Integer | The unique ID of the sub-account to update.

begin
  # Update Sub-Account
  result = api_instance.update_sub_account(update_sub_account, subaccount_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->update_sub_account: #{e}"
end
```

#### Using the update_sub_account_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<SubAccount>, Integer, Hash)> update_sub_account_with_http_info(update_sub_account, subaccount_id)

```ruby
begin
  # Update Sub-Account
  data, status_code, headers = api_instance.update_sub_account_with_http_info(update_sub_account, subaccount_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <SubAccount>
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->update_sub_account_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **update_sub_account** | [**UpdateSubAccount**](UpdateSubAccount.md) |  |  |
| **subaccount_id** | **Integer** | The unique ID of the sub-account to update. |  |

### Return type

[**SubAccount**](SubAccount.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

