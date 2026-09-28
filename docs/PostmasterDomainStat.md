# Sendpost::PostmasterDomainStat

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** | The domain these Postmaster statistics belong to. | [optional] |
| **date** | **String** | The date these statistics apply to (YYYY-MM-DD, UTC). | [optional] |
| **domain_reputation** | **String** | Google&#39;s reputation rating for the domain (e.g. &#x60;HIGH&#x60;, &#x60;MEDIUM&#x60;, &#x60;LOW&#x60;, &#x60;BAD&#x60;).  | [optional] |
| **spam** | **String** | User-reported spam rate for the domain (fraction, string-encoded). | [optional] |
| **dkim_success** | **String** | Fraction of mail that passed DKIM authentication (string-encoded). | [optional] |
| **spf_success** | **String** | Fraction of mail that passed SPF authentication (string-encoded). | [optional] |
| **dmarc_success** | **String** | Fraction of mail that passed DMARC authentication (string-encoded). | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::PostmasterDomainStat.new(
  name: mail.hooli.com,
  date: 2024-01-15,
  domain_reputation: HIGH,
  spam: 0.01,
  dkim_success: 0.99,
  spf_success: 0.98,
  dmarc_success: 0.97
)
```

