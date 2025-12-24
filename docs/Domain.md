# Sendpost::Domain

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique ID for the domain. | [optional] |
| **name** | **String** | Name of the domain. | [optional] |
| **dkim** | [**DomainDkim**](DomainDkim.md) |  | [optional] |
| **return_path** | [**DomainReturnPath**](DomainReturnPath.md) |  | [optional] |
| **track** | [**DomainTrack**](DomainTrack.md) |  | [optional] |
| **dmarc** | [**DomainDmarc**](DomainDmarc.md) |  | [optional] |
| **dkim_config** | **String** | DKIM configuration | [optional] |
| **dkim_verified** | **Boolean** | Status of DKIM verification ( true or false ) | [optional] |
| **dmarc_verified** | **Boolean** | Status of DMARC verification ( true or false) | [optional] |
| **return_path_verified** | **Boolean** | Status of ReturnPath verification ( true or false ) | [optional] |
| **track_verified** | **Boolean** | Status of Track verification ( true or false ) | [optional] |
| **verified** | **Boolean** | Overall verification status of the domain | [optional] |
| **domain_registered_date** | **String** | Date when the domain was registered | [optional] |
| **created** | **Integer** | UNIX epoch timestamp in nanoseconds. | [optional] |
| **gpt_verified** | **Boolean** | Status of GPT verification ( true or false ) | [optional] |
| **gpt** | [**DomainGpt**](DomainGpt.md) |  | [optional] |
| **dmarc_failure_reason** | **String** | Reason for DMARC verification failure | [optional] |
| **dkim_failure_reason** | **String** | Reason for DKIM verification failure | [optional] |
| **track_failure_reason** | **String** | Reason for Track verification failure | [optional] |
| **return_path_failure_reason** | **String** | Reason for ReturnPath verification failure | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Domain.new(
  id: 117,
  name: piedpiper.com,
  dkim: null,
  return_path: null,
  track: null,
  dmarc: null,
  dkim_config: null,
  dkim_verified: false,
  dmarc_verified: false,
  return_path_verified: false,
  track_verified: true,
  verified: false,
  domain_registered_date: 1995-08-14,
  created: 1766394250613907000,
  gpt_verified: false,
  gpt: null,
  dmarc_failure_reason: ,
  dkim_failure_reason: ,
  track_failure_reason: ,
  return_path_failure_reason: 
)
```

