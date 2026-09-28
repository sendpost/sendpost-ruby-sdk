# Sendpost::DomainApi

All URIs are relative to *https://api.sendpost.io/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_sub_account_domain**](DomainApi.md#create_sub_account_domain) | **POST** /subaccount/domain | Create Domain |
| [**delete_sub_account_domain**](DomainApi.md#delete_sub_account_domain) | **DELETE** /subaccount/domain/{domain_id} | Delete Domain |
| [**get_all_domains**](DomainApi.md#get_all_domains) | **GET** /subaccount/domain | List Domains |
| [**get_sub_account_domain**](DomainApi.md#get_sub_account_domain) | **GET** /subaccount/domain/{domain_id} | Get Domain |


## create_sub_account_domain

> <Domain> create_sub_account_domain(create_domain_request)

Create Domain

Register a new sending domain with SendPost. After creation, you'll receive DNS records that must be configured with your DNS provider before you can send emails.  **Domain Setup Process:** 1. Call this endpoint with your domain name 2. Copy the returned DNS records (DKIM, Return-Path, Track, DMARC) 3. Add records to your DNS provider (GoDaddy, Cloudflare, Route53, etc.) 4. Wait for DNS propagation (typically 15 minutes to 48 hours) 5. Verification happens automatically, or trigger manual verification  **DNS Records Explained:** | Record | Purpose | Required | |--------|---------|----------| | DKIM | Cryptographically signs emails to prove authenticity | Yes | | Return-Path | Routes bounce notifications through SendPost | Recommended | | Track | Enables click tracking with your domain | Optional | | DMARC | Adds additional authentication layer | Recommended |  **Best Practices:** - Use a subdomain like `mail.yourdomain.com` for sending - Keep your root domain for your website - Configure all records for best deliverability 

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

api_instance = Sendpost::DomainApi.new
create_domain_request = Sendpost::CreateDomainRequest.new({name: 'piedpiper.com'}) # CreateDomainRequest | 

begin
  # Create Domain
  result = api_instance.create_sub_account_domain(create_domain_request)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->create_sub_account_domain: #{e}"
end
```

#### Using the create_sub_account_domain_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Domain>, Integer, Hash)> create_sub_account_domain_with_http_info(create_domain_request)

```ruby
begin
  # Create Domain
  data, status_code, headers = api_instance.create_sub_account_domain_with_http_info(create_domain_request)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Domain>
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->create_sub_account_domain_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **create_domain_request** | [**CreateDomainRequest**](CreateDomainRequest.md) |  |  |

### Return type

[**Domain**](Domain.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_sub_account_domain

> <DeleteResponse> delete_sub_account_domain(domain_id)

Delete Domain

Remove a sending domain from your sub-account. Once deleted, you can no longer send emails from addresses on this domain.  **Before Deleting:** - Ensure no active email campaigns use this domain - Update sender addresses in your applications - Consider impact on email deliverability  **Note:** DNS records for the domain will become orphaned. You may want to remove them from your DNS provider. 

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

api_instance = Sendpost::DomainApi.new
domain_id = 'domain_id_example' # String | The unique ID of the domain to delete.

begin
  # Delete Domain
  result = api_instance.delete_sub_account_domain(domain_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->delete_sub_account_domain: #{e}"
end
```

#### Using the delete_sub_account_domain_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<DeleteResponse>, Integer, Hash)> delete_sub_account_domain_with_http_info(domain_id)

```ruby
begin
  # Delete Domain
  data, status_code, headers = api_instance.delete_sub_account_domain_with_http_info(domain_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <DeleteResponse>
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->delete_sub_account_domain_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **domain_id** | **String** | The unique ID of the domain to delete. |  |

### Return type

[**DeleteResponse**](DeleteResponse.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_all_domains

> <Array<Domain>> get_all_domains(opts)

List Domains

Retrieve all sending domains configured for this sub-account. Use this endpoint to audit your domain setup, check verification status, or retrieve DNS records for configuration.  **Each domain record includes:** - Domain name and unique ID - DNS records to configure (DKIM, Return-Path, Track, DMARC) - Verification status for each record type - Failure messages for troubleshooting - Creation timestamp  **Verification Status Values:** - `true` - Record verified and active - `false` - Record not verified (check DNS configuration)  **Use Cases:** - Audit all configured sending domains - Export DNS records for documentation - Identify domains pending verification - Monitor domain health across multiple domains  **Pagination:** Use `limit` and `offset` for large domain lists. 

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

api_instance = Sendpost::DomainApi.new
opts = {
  limit: 20, # Integer | Number of records to return per request. Default is 20.
  offset: 0, # Integer | Number of initial records to skip for pagination.
  search: 'mycompany' # String | Case insensitive search against domain names. Useful for finding specific domains in large lists.
}

begin
  # List Domains
  result = api_instance.get_all_domains(opts)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->get_all_domains: #{e}"
end
```

#### Using the get_all_domains_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Array<Domain>>, Integer, Hash)> get_all_domains_with_http_info(opts)

```ruby
begin
  # List Domains
  data, status_code, headers = api_instance.get_all_domains_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Array<Domain>>
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->get_all_domains_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **limit** | **Integer** | Number of records to return per request. Default is 20. | [optional][default to 20] |
| **offset** | **Integer** | Number of initial records to skip for pagination. | [optional][default to 0] |
| **search** | **String** | Case insensitive search against domain names. Useful for finding specific domains in large lists. | [optional] |

### Return type

[**Array&lt;Domain&gt;**](Domain.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_sub_account_domain

> <Domain> get_sub_account_domain(domain_id)

Get Domain

Retrieve detailed information about a specific sending domain, including DNS record configuration and verification status.  **Response includes:** - Domain name and ID - DKIM, Return-Path, Track, and DMARC DNS records to configure - Verification status for each record type - Failure reasons if verification failed - Domain registration date  **Use Cases:** - Check verification status before sending emails - Retrieve DNS records during domain setup - Debug DNS configuration issues - Audit domain settings for compliance 

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

api_instance = Sendpost::DomainApi.new
domain_id = 'domain_id_example' # String | The unique ID of the domain to retrieve.

begin
  # Get Domain
  result = api_instance.get_sub_account_domain(domain_id)
  p result
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->get_sub_account_domain: #{e}"
end
```

#### Using the get_sub_account_domain_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Domain>, Integer, Hash)> get_sub_account_domain_with_http_info(domain_id)

```ruby
begin
  # Get Domain
  data, status_code, headers = api_instance.get_sub_account_domain_with_http_info(domain_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Domain>
rescue Sendpost::ApiError => e
  puts "Error when calling DomainApi->get_sub_account_domain_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **domain_id** | **String** | The unique ID of the domain to retrieve. |  |

### Return type

[**Domain**](Domain.md)

### Authorization

[subAccountAuth](../README.md#subAccountAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

