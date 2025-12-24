# Sendpost::Event

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **event_id** | **String** |  | [optional] |
| **groups** | **Array&lt;String&gt;** |  | [optional] |
| **ip_id** | **Integer** |  | [optional] |
| **ip_pool_id** | **Integer** |  | [optional] |
| **domain_id** | **Integer** |  | [optional] |
| **tpsp_id** | **Integer** |  | [optional] |
| **message_type** | **String** |  | [optional] |
| **message_subject** | **String** |  | [optional] |
| **account_id** | **Integer** |  | [optional] |
| **sub_account_id** | **Integer** |  | [optional] |
| **message_id** | **String** |  | [optional] |
| **type** | **Integer** |  | [optional] |
| **from** | **String** |  | [optional] |
| **from_name** | **String** |  | [optional] |
| **to** | **String** |  | [optional] |
| **to_name** | **String** |  | [optional] |
| **submitted_at** | **Integer** |  | [optional] |
| **smtp_code** | **Integer** |  | [optional] |
| **smtp_description** | **String** |  | [optional] |
| **event_metadata** | [**EventMetadata**](EventMetadata.md) |  | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Event.new(
  event_id: edhg-123gh-afasdf-124egh,
  groups: [&quot;transactional&quot;,&quot;user-onboarding&quot;],
  ip_id: 123,
  ip_pool_id: 123,
  domain_id: 123,
  tpsp_id: 1,
  message_type: default,
  message_subject: Welcome to Pied Piper :) + 1 quick question,
  account_id: 117,
  sub_account_id: 117,
  message_id: mjhl-1401-sasdf-129324,
  type: 2,
  from: richard@piedpiper.com,
  from_name: Richard,
  to: gavin@hooli.com,
  to_name: Gavin,
  submitted_at: 1567512491587205024,
  smtp_code: 200,
  smtp_description: email delivered successfully,
  event_metadata: null
)
```

