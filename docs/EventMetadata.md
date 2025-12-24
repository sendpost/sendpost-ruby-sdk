# Sendpost::EventMetadata

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **smtp_code** | **Integer** |  | [optional] |
| **smtp_description** | **String** |  | [optional] |
| **user_agent** | [**UserAgent**](UserAgent.md) |  | [optional] |
| **os** | [**OperatingSystem**](OperatingSystem.md) |  | [optional] |
| **device** | [**Device**](Device.md) |  | [optional] |
| **geo** | [**GeoLocation**](GeoLocation.md) |  | [optional] |
| **clicked_url** | **String** |  | [optional] |
| **tracked_ip** | **String** |  | [optional] |
| **raw_user_agent** | **String** |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EventMetadata.new(
  smtp_code: 200,
  smtp_description: email delivered successfully,
  user_agent: null,
  os: null,
  device: null,
  geo: null,
  clicked_url: https://hooli.com,
  tracked_ip: 52.34.11.12,
  raw_user_agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.116 Safari/537.36
)
```

