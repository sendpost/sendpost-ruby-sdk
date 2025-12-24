# Sendpost::SubAccount

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique ID for the sub-account. | [optional] |
| **api_key** | **String** | API key for the sub-account. | [optional] |
| **name** | **String** | Name of the sub-account. | [optional] |
| **labels** | [**Array&lt;Label&gt;**](Label.md) | Labels associated with the sub-account | [optional] |
| **smtp_auths** | [**Array&lt;SMTPAuth&gt;**](SMTPAuth.md) | SMTP Auths associated with the sub-account | [optional] |
| **type** | **Integer** | Type of the sub-account | [optional] |
| **is_plus** | **Boolean** | Indicates whether the sub-account is a Plus sub-account | [optional] |
| **created** | **Integer** | UNIX epoch nano timestamp when the sub-account was created. | [optional] |
| **created_by** | **Hash&lt;String, Object&gt;** | Member who created the sub-account | [optional] |
| **updated_by** | **Hash&lt;String, Object&gt;** | Member who updated the sub-account | [optional] |
| **blocked** | **Boolean** | Indicates whether the sub-account is blocked | [optional] |
| **blocked_at** | **Integer** | UNIX epoch nano timestamp when the sub-account was blocked (0 if not blocked) | [optional] |
| **block_reason** | **String** | Reason for blocking the sub-account | [optional] |
| **hb_exempt** | **Boolean** | Indicates whether the sub-account is exempt from hard bounce tracking | [optional] |
| **generate_weekly_report** | **Boolean** | Indicates whether weekly reports are generated for this sub-account | [optional] |
| **handlers** | **Array&lt;String&gt;** | Handlers associated with the sub-account | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::SubAccount.new(
  id: 50441,
  api_key: pR0YIuxYSbVwmQi2Y8Qs,
  name: API,
  labels: [],
  smtp_auths: null,
  type: 1,
  is_plus: false,
  created: 1733844681120384500,
  created_by: null,
  updated_by: null,
  blocked: false,
  blocked_at: 0,
  block_reason: ,
  hb_exempt: false,
  generate_weekly_report: false,
  handlers: []
)
```

