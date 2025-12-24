# Sendpost::AutoWarmupPlan

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique ID for the auto-warmup plan | [optional] |
| **name** | **String** | Name of the auto-warmup plan | [optional] |
| **gmail_warmup_plan** | **String** | Gmail warmup plan configuration in JSON format | [optional] |
| **yahoo_warmup_plan** | **String** | Yahoo warmup plan configuration in JSON format | [optional] |
| **aol_warmup_plan** | **String** | AOL warmup plan configuration in JSON format | [optional] |
| **microsoft_warmup_plan** | **String** | Microsoft warmup plan configuration in JSON format | [optional] |
| **comcast_warmup_plan** | **String** | Comcast warmup plan configuration in JSON format | [optional] |
| **yandex_warmup_plan** | **String** | Yandex warmup plan configuration in JSON format | [optional] |
| **gmx_warmup_plan** | **String** | GMX warmup plan configuration in JSON format | [optional] |
| **mailru_warmup_plan** | **String** | Mail.ru warmup plan configuration in JSON format | [optional] |
| **icloud_warmup_plan** | **String** | iCloud warmup plan configuration in JSON format | [optional] |
| **zoho_warmup_plan** | **String** | Zoho warmup plan configuration in JSON format | [optional] |
| **qq_warmup_plan** | **String** | QQ warmup plan configuration in JSON format | [optional] |
| **default_warmup_plan** | **String** | Default warmup plan configuration in JSON format | [optional] |
| **att_warmup_plan** | **String** | AT&amp;T warmup plan configuration in JSON format | [optional] |
| **office365_warmup_plan** | **String** | Office365 warmup plan configuration in JSON format | [optional] |
| **googleworkspace_warmup_plan** | **String** | Google Workspace warmup plan configuration in JSON format | [optional] |
| **proofpoint_warmup_plan** | **String** | Proofpoint warmup plan configuration in JSON format | [optional] |
| **mimecast_warmup_plan** | **String** | Mimecast warmup plan configuration in JSON format | [optional] |
| **barracuda_warmup_plan** | **String** | Barracuda warmup plan configuration in JSON format | [optional] |
| **ciscoironport_warmup_plan** | **String** | Cisco IronPort warmup plan configuration in JSON format | [optional] |
| **rackspace_warmup_plan** | **String** | Rackspace warmup plan configuration in JSON format | [optional] |
| **zohobusiness_warmup_plan** | **String** | Zoho Business warmup plan configuration in JSON format | [optional] |
| **amazonworkmail_warmup_plan** | **String** | Amazon WorkMail warmup plan configuration in JSON format | [optional] |
| **symantec_warmup_plan** | **String** | Symantec warmup plan configuration in JSON format | [optional] |
| **fortinet_warmup_plan** | **String** | Fortinet warmup plan configuration in JSON format | [optional] |
| **sophos_warmup_plan** | **String** | Sophos warmup plan configuration in JSON format | [optional] |
| **trendmicro_warmup_plan** | **String** | Trend Micro warmup plan configuration in JSON format | [optional] |
| **checkpoint_warmup_plan** | **String** | Checkpoint warmup plan configuration in JSON format | [optional] |
| **created** | **Integer** | UNIX epoch nano timestamp when the warmup plan was created | [optional] |
| **updated** | **Integer** | UNIX epoch nano timestamp when the warmup plan was last updated | [optional] |
| **warmup_interval** | **Integer** | Warmup interval in hours | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::AutoWarmupPlan.new(
  id: 742,
  name: Default Auto Warmup Plan,
  gmail_warmup_plan: null,
  yahoo_warmup_plan: null,
  aol_warmup_plan: null,
  microsoft_warmup_plan: null,
  comcast_warmup_plan: null,
  yandex_warmup_plan: null,
  gmx_warmup_plan: null,
  mailru_warmup_plan: null,
  icloud_warmup_plan: null,
  zoho_warmup_plan: null,
  qq_warmup_plan: null,
  default_warmup_plan: null,
  att_warmup_plan: null,
  office365_warmup_plan: null,
  googleworkspace_warmup_plan: null,
  proofpoint_warmup_plan: null,
  mimecast_warmup_plan: null,
  barracuda_warmup_plan: null,
  ciscoironport_warmup_plan: null,
  rackspace_warmup_plan: null,
  zohobusiness_warmup_plan: null,
  amazonworkmail_warmup_plan: null,
  symantec_warmup_plan: null,
  fortinet_warmup_plan: null,
  sophos_warmup_plan: null,
  trendmicro_warmup_plan: null,
  checkpoint_warmup_plan: null,
  created: 1761234191727534000,
  updated: 1766535064510659800,
  warmup_interval: 24
)
```

