# Sendpost::Domain

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique identifier for the domain | [optional] |
| **name** | **String** | The domain name (e.g., \&quot;example.com\&quot;). This is the domain portion of your sending email addresses.  | [optional] |
| **dns_provider** | **String** | Auto-detected DNS provider for this domain (e.g. \&quot;cloudflare\&quot;, \&quot;other\&quot;), used to tailor DNS-setup instructions. Read-only.  | [optional] |
| **dkim** | [**DnsRecord**](DnsRecord.md) | DKIM (DomainKeys Identified Mail) DNS record configuration. DKIM cryptographically signs your emails to verify they haven&#39;t been tampered with. This is REQUIRED for sending emails.  | [optional] |
| **return_path** | [**DnsRecord**](DnsRecord.md) | Return-Path (bounce handling) DNS record configuration. Configuring this allows bounce notifications to be properly routed through SendPost. RECOMMENDED for better deliverability.  | [optional] |
| **track** | [**DnsRecord**](DnsRecord.md) | Tracking domain DNS record configuration. When configured, click tracking links use your domain instead of SendPost&#39;s domain. RECOMMENDED for brand consistency and improved click-through rates.  | [optional] |
| **dmarc** | [**DnsRecord**](DnsRecord.md) | DMARC (Domain-based Message Authentication, Reporting &amp; Conformance) DNS record. DMARC builds on DKIM and SPF to provide email authentication and reporting. RECOMMENDED for enterprise senders.  | [optional] |
| **dkim_verified** | **Boolean** | Whether the DKIM DNS record has been verified successfully | [optional] |
| **dmarc_verified** | **Boolean** | Whether the DMARC DNS record has been verified successfully | [optional] |
| **return_path_verified** | **Boolean** | Whether the Return-Path DNS record has been verified successfully | [optional] |
| **track_verified** | **Boolean** | Whether the tracking domain DNS record has been verified successfully | [optional] |
| **verified** | **Boolean** | Overall verification status. True only if DKIM is verified (minimum requirement). For full verification, configure all DNS records.  | [optional] |
| **domain_registered_date** | **Date** | Date when this domain was originally registered (from WHOIS). Newer domains may have lower sender reputation initially.  | [optional] |
| **created** | **Integer** | UNIX epoch timestamp in nanoseconds when the domain was added to SendPost | [optional] |
| **dkim_failure_reason** | **String** | Detailed reason if DKIM verification failed (empty if verified or not attempted) | [optional] |
| **dmarc_failure_reason** | **String** | Detailed reason if DMARC verification failed | [optional] |
| **track_failure_reason** | **String** | Detailed reason if tracking domain verification failed | [optional] |
| **return_path_failure_reason** | **String** | Detailed reason if Return-Path verification failed | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Domain.new(
  id: 117,
  name: piedpiper.com,
  dns_provider: cloudflare,
  dkim: null,
  return_path: null,
  track: null,
  dmarc: null,
  dkim_verified: true,
  dmarc_verified: false,
  return_path_verified: true,
  track_verified: true,
  verified: true,
  domain_registered_date: 1995-08-14,
  created: 1704067200000000000,
  dkim_failure_reason: DNS record not found. Please add the TXT record to your DNS provider.,
  dmarc_failure_reason: ,
  track_failure_reason: ,
  return_path_failure_reason: 
)
```

