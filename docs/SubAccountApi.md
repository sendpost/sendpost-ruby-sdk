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

> <SubAccount> create_sub_account(create_sub_account_request)

Create Sub-Account

Creates a new sub-account under the current account.

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
create_sub_account_request = Sendpost::CreateSubAccountRequest.new # CreateSubAccountRequest | 

begin
  # Create Sub-Account
  result = api_instance.create_sub_account(create_sub_account_request)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling SubAccountApi->create_sub_account: #{e}"
end
```

#### Using the create_sub_account_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<SubAccount>, Integer, Hash)> create_sub_account_with_http_info(create_sub_account_request)

```ruby
begin
  # Create Sub-Account
  data, status_code, headers = api_instance.create_sub_account_with_http_info(create_sub_account_request)
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
| **create_sub_account_request** | [**CreateSubAccountRequest**](CreateSubAccountRequest.md) |  |  |

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

Deletes a specific sub-account by its ID.

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
subaccount_id = 12 # Integer | The ID of the sub-account to delete.

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
| **subaccount_id** | **Integer** | The ID of the sub-account to delete. |  |

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

Retrieves a list of all sub-accounts associated with a specific account.

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
  limit: 10, # Integer | Number of records to return per request.
  offset: 0, # Integer | Number of initial records to skip.
  search: 'Hooli' # String | Case-insensitive search against the sub-account name.
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
| **limit** | **Integer** | Number of records to return per request. | [optional] |
| **offset** | **Integer** | Number of initial records to skip. | [optional] |
| **search** | **String** | Case-insensitive search against the sub-account name. | [optional] |

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

Retrieves a specific sub-account by its ID.

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
subaccount_id = 11 # Integer | The ID of the sub-account to retrieve.

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
| **subaccount_id** | **Integer** | The ID of the sub-account to retrieve. |  |

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

Updates the details of an existing sub-account.

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
subaccount_id = 12 # Integer | The ID of the sub-account to update.

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
| **subaccount_id** | **Integer** | The ID of the sub-account to update. |  |

### Return type

[**SubAccount**](SubAccount.md)

### Authorization

[accountAuth](../README.md#accountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

