# Sendpost::GeoLocation

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **city_id** | **String** |  | [optional] |
| **continent_code** | **String** |  | [optional] |
| **country_code** | **String** |  | [optional] |
| **postal_code** | **String** |  | [optional] |
| **time_zone** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::GeoLocation.new(
  city_id: 123,
  continent_code: EU,
  country_code: US,
  postal_code: 12345,
  time_zone: America/Los_Angeles
)
```

