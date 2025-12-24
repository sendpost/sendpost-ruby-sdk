# Sendpost::Member

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique ID for the member | [optional] |
| **is_verified** | **Boolean** | Indicates whether the member is verified | [optional] |
| **is_forbidden** | **Boolean** | Indicates whether the member is forbidden | [optional] |
| **firebase_uid** | **String** | Firebase UID for the member | [optional] |
| **email** | **String** | Email for the member | [optional] |
| **name** | **String** | Name for the member | [optional] |
| **url** | **String** | Logo URL for the member | [optional] |
| **company_name** | **String** | Company name for the member | [optional] |
| **onboard_q_answered** | **Boolean** | Indicates whether the member has answered onboarding question | [optional] |
| **phone_number** | **String** | Phone number for the member | [optional] |
| **notes_color** | **String** | Color for the member&#39;s notes | [optional] |
| **created** | **Integer** | UNIX epoch nano timestamp when the member was created | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Member.new(
  id: 117,
  is_verified: true,
  is_forbidden: false,
  firebase_uid: 1234567890,
  email: raj@piedpiper.com,
  name: Raj,
  url: https://www.sendpost.io/logo.png,
  company_name: SendPost,
  onboard_q_answered: true,
  phone_number: +919876543210,
  notes_color: #000000,
  created: 1567512491588004044
)
```

