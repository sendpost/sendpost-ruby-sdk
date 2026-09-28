# Sendpost::Member

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Unique identifier for the team member | [optional] |
| **email** | **String** | Email address of the team member (used for login) | [optional] |
| **name** | **String** | Display name of the team member | [optional] |
| **is_verified** | **Boolean** | Whether the member has verified their email address. Unverified members have limited access until verification is complete.  | [optional] |
| **logo_url** | **String** | URL of the member&#39;s profile picture/avatar | [optional] |
| **company_name** | **String** | Company or organization name | [optional] |
| **onboard_q_answered** | **Boolean** | Whether the member has completed the onboarding questionnaire | [optional] |
| **phone_number** | **String** | Contact phone number in E.164 format. Used for account recovery and important notifications.  | [optional] |
| **created** | **Integer** | UNIX epoch timestamp in nanoseconds when the member was added | [optional] |

## Example

```ruby
require 'sendpost_ruby_sdk'

instance = Sendpost::Member.new(
  id: 117,
  email: raj@piedpiper.com,
  name: Raj Koothrappali,
  is_verified: true,
  logo_url: https://avatars.example.com/raj.png,
  company_name: Pied Piper,
  onboard_q_answered: true,
  phone_number: +14155551234,
  created: 1704067200000000000
)
```

