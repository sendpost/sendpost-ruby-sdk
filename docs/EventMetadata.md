# Sendpost::EventMetadata

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **smtp_code** | **Integer** | SMTP response code from the receiving mail server. - 250: Success - 4xx: Temporary failure (soft bounce) - 5xx: Permanent failure (hard bounce)  | [optional] |
| **smtp_description** | **String** | Full SMTP response message from the receiving server. Useful for diagnosing delivery issues.  | [optional] |
| **user_agent** | [**UserAgent**](UserAgent.md) | Parsed browser/email client information (for open/click events) | [optional] |
| **os** | [**Os**](Os.md) | Parsed operating system information (for open/click events) | [optional] |
| **device** | [**Device**](Device.md) | Device type information (for open/click events) | [optional] |
| **geo** | [**GeoLocation**](GeoLocation.md) | Geographic location based on IP address (for open/click events) | [optional] |
| **clicked_url** | **String** | The original URL that was clicked (only for click events) | [optional] |
| **tracked_ip** | **String** | IP address of the user who triggered the event (open/click) | [optional] |
| **raw_user_agent** | **String** | Raw User-Agent header string from the HTTP request | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::EventMetadata.new(
  smtp_code: 250,
  smtp_description: 250 2.0.0 OK 1704067205 - Message accepted for delivery,
  user_agent: null,
  os: null,
  device: null,
  geo: null,
  clicked_url: https://piedpiper.com/track-order?id&#x3D;12345,
  tracked_ip: 73.162.45.123,
  raw_user_agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36
)
```

