# Sendpost::IP

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique ID for the IP |  |
| **public_ip** | **String** | The public IP address associated with the resource |  |
| **system_domain** | [**Domain**](Domain.md) |  | [optional] |
| **reverse_dns_hostname** | **String** | The reverse DNS hostname for the IP | [optional] |
| **type** | **Integer** | Type of the IP | [optional] |
| **gmail_settings** | **String** | Configuration for Gmail delivery settings in JSON format | [optional] |
| **yahoo_settings** | **String** | Configuration for Yahoo delivery settings in JSON format | [optional] |
| **aol_settings** | **String** | Configuration for AOL delivery settings in JSON format | [optional] |
| **microsoft_settings** | **String** | Configuration for Microsoft delivery settings in JSON format | [optional] |
| **comcast_settings** | **String** | Configuration for Comcast delivery settings in JSON format | [optional] |
| **yandex_settings** | **String** | Configuration for Yandex delivery settings in JSON format | [optional] |
| **gmx_settings** | **String** | Configuration for GMX delivery settings in JSON format | [optional] |
| **mailru_settings** | **String** | Configuration for Mail.ru delivery settings in JSON format | [optional] |
| **icloud_settings** | **String** | Configuration for iCloud delivery settings in JSON format | [optional] |
| **zoho_settings** | **String** | Configuration for Zoho delivery settings in JSON format | [optional] |
| **qq_settings** | **String** | Configuration for QQ delivery settings in JSON format | [optional] |
| **default_settings** | **String** | Default delivery settings in JSON format | [optional] |
| **att_settings** | **String** | Configuration for AT&amp;T delivery settings in JSON format | [optional] |
| **created** | **Integer** | The timestamp (UNIX epoch) when the IP was created |  |
| **infra_classification** | **String** | Classification of the infrastructure | [optional] |
| **infra_monitor** | **Boolean** | Indicates whether infrastructure monitoring is enabled | [optional] |
| **state** | **Integer** | The state of the IP | [optional] |
| **auto_warmup_plan** | [**AutoWarmupPlan**](AutoWarmupPlan.md) | The auto-warmup plan associated with the IP. Can be null if no warmup plan is assigned. | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::IP.new(
  id: 11321,
  public_ip: 52.34.11.12,
  system_domain: null,
  reverse_dns_hostname: example.mtaspg.email,
  type: 0,
  gmail_settings: {&quot;name&quot;:&quot;gmail&quot;,&quot;maxConcurrentConnections&quot;:100,...},
  yahoo_settings: {&quot;name&quot;:&quot;yahoo&quot;,&quot;maxConcurrentConnections&quot;:16,...},
  aol_settings: {&quot;name&quot;:&quot;aol&quot;,&quot;maxConcurrentConnections&quot;:20,...},
  microsoft_settings: {&quot;name&quot;:&quot;microsoft&quot;,&quot;maxConcurrentConnections&quot;:16,...},
  comcast_settings: {&quot;name&quot;:&quot;comcast&quot;,&quot;maxConcurrentConnections&quot;:20,...},
  yandex_settings: {&quot;name&quot;:&quot;yandex&quot;,&quot;maxConcurrentConnections&quot;:2,...},
  gmx_settings: {&quot;name&quot;:&quot;gmx&quot;,&quot;maxConcurrentConnections&quot;:2,...},
  mailru_settings: {&quot;name&quot;:&quot;mailru&quot;,&quot;maxConcurrentConnections&quot;:1,...},
  icloud_settings: {&quot;name&quot;:&quot;icloud&quot;,&quot;maxConcurrentConnections&quot;:20,...},
  zoho_settings: {&quot;name&quot;:&quot;zoho&quot;,&quot;maxConcurrentConnections&quot;:1,...},
  qq_settings: {&quot;name&quot;:&quot;qq&quot;,&quot;maxConcurrentConnections&quot;:1,...},
  default_settings: {&quot;name&quot;:&quot;default&quot;,&quot;maxConcurrentConnections&quot;:14,...},
  att_settings: {&quot;name&quot;:&quot;att&quot;,&quot;maxConcurrentConnections&quot;:1,...},
  created: 1703224038766344700,
  infra_classification: ,
  infra_monitor: true,
  state: 1,
  auto_warmup_plan: null
)
```

