# Sendpost::GeoLocation

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **city_id** | **Integer** | GeoNames city identifier | [optional] |
| **country_code** | **String** | Two-letter ISO 3166-1 alpha-2 country code | [optional] |
| **continent_code** | **String** | Two-letter continent code: AF (Africa), AN (Antarctica), AS (Asia), EU (Europe), NA (North America), OC (Oceania), SA (South America)  | [optional] |
| **postal_code** | **String** | Postal/ZIP code | [optional] |
| **time_zone** | **String** | IANA timezone identifier | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::GeoLocation.new(
  city_id: 5391959,
  country_code: US,
  continent_code: NA,
  postal_code: 94105,
  time_zone: America/Los_Angeles
)
```

