# Sendpost::BlacklistResource

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** | Unique identifier of the blacklist resource entry. | [optional] |
| **type** | **String** | The kind of target being monitored (e.g. &#x60;domain&#x60; or &#x60;ip&#x60;). | [optional] |
| **target** | **String** | The domain or IP address being monitored for blacklisting. | [optional] |
| **add_date** | **Integer** | UNIX epoch timestamp when the resource was added to monitoring. | [optional] |
| **last_check** | **Integer** | UNIX epoch timestamp of the most recent blacklist check. | [optional] |
| **status** | **String** | Current blacklist status of the target (e.g. &#x60;clean&#x60;, &#x60;listed&#x60;). | [optional] |
| **label** | **String** | User-assigned label for the monitored resource. | [optional] |
| **contact_list_id** | **String** | Identifier of the contact list associated with this resource, if any. | [optional] |
| **blacklisted_count** | **String** | Number of RBLs the target is currently listed on (string-encoded). | [optional] |
| **blacklisted_on** | [**Array&lt;BlacklistedOn&gt;**](BlacklistedOn.md) | The specific RBLs this target is currently listed on. | [optional] |
| **links** | [**BlacklistLinks**](BlacklistLinks.md) |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::BlacklistResource.new(
  id: abc123,
  type: ip,
  target: 192.0.2.10,
  add_date: 1704067200,
  last_check: 1704153600,
  status: listed,
  label: Primary sending IP,
  contact_list_id: ,
  blacklisted_count: 2,
  blacklisted_on: null,
  links: null
)
```

