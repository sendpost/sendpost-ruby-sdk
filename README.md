# sendpost_ruby_sdk

Sendpost - the Ruby gem for the SendPost API

# Introduction

> ### 📌 API versioning & the v1 response contract
>
> This reference documents the **v1 response contract** — the stable, camelCase
> response shape that SendPost commits to. This is the shape you should build against.
>
> **During the current deprecation window**, requests authenticated with an account
> or sub-account API key receive the **legacy** response shape by default, so existing
> integrations keep working unchanged. To receive the documented v1 shape today, send:
>
> ```
> X-SendPost-Public-Contract: v1
> ```
>
> **How to tell which shape you got.** Every public response echoes the applied
> contract in the `X-SendPost-Public-Contract` response header. While the legacy
> shape is being served, responses also carry standard deprecation signals:
> `Deprecation: true`, a `Sunset` header with the exact cut-over date, and a
> `Link: <...>; rel=\"deprecation\"` header pointing at the migration guide. **Read the
> `Sunset` header for the authoritative end date** rather than hardcoding one.
>
> **After the sunset date**, v1 becomes the default and the legacy shape is no longer
> served. New integrations should send `X-SendPost-Public-Contract: v1` now and rely on
> the shapes in this reference.

SendPost provides email API and SMTP relay which can be used not just to send & measure but also alert & optimised email sending.

You can use SendPost to:

* Send personalised emails to multiple recipients using email API 

* Track opens and clicks

* Analyse statistics around open, clicks, bounce, unsubscribe and spam 


At and advanced level you can use it to:

* Manage multiple sub-accounts which may map to your promotional or transactional sending, multiple product lines or multiple customers 

* Classify your emails using groups for better analysis

* Analyse and fix email sending at sub-account level, IP Pool level or group level

* Have automated alerts to notify disruptions regarding email sending

* Manage different dedicated IP Pools so to better control your email sending

* Automatically know when IP or domain is blacklisted or sender score is down

* Leverage pro deliverability tools to get significantly better email deliverability & inboxing


[<img src=\"https://run.pstmn.io/button.svg\" alt=\"Run In Postman\" style=\"width: 128px; height: 32px;\">](https://god.gw.postman.com/run-collection/33476323-e6dbd27f-c4a7-4d49-bcac-94b0611b938b?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D33476323-e6dbd27f-c4a7-4d49-bcac-94b0611b938b%26entityType%3Dcollection%26workspaceId%3D6b1e4f65-96a9-4136-9512-6266c852517e) 

# Overview

## REST API

SendPost API is built on REST API principles. Authenticated users can interact with any of the API endpoints to perform:

* **GET**- to get a resource

* **POST** - to create a resource

* **PUT** - to update an existing resource

* **DELETE** - to delete a resource


The API endpoint for all API calls is:
<code>https://api.sendpost.io/api/v1</code>


Some conventions that have been followed in the API design overall are following:


* All resources have either <code>/api/v1/subaccount</code> or <code>/api/v1/account</code> in their API call resource path based on who is authorised for the resource. All API calls with path <code>/api/v1/subaccount</code> use <code>X-SubAccount-ApiKey</code> in their request header. Likewise all API calls with path <code>/api/v1/account</code> use <code>X-Account-ApiKey</code> in their request header.

* All resource endpoints end with singular name and not plural. So we have <code>domain</code> instead of domains for domain resource endpoint. Likewise we have <code>sender</code> instead of senders for sender resource endpoint.

* Body submitted for POST / PUT API calls as well as JSON response from SendPost API follow camelcase convention

* All timestamps returned in response (created or submittedAt response fields) are UNIX nano epoch timestamp.


<aside class=\"success\">
All resources have either <code>/api/v1/subaccount</code> or <code>/api/v1/account</code> in their API call resource path based on who is authorised for the resource. All API calls with path <code>/api/v1/subaccount</code> use <code>X-SubAccount-ApiKey</code> in their request header. Likewise all API calls with path <code>/api/v1/account</code> use <code>X-Account-ApiKey</code> in their request header.
</aside>


SendPost uses conventional HTTP response codes to indicate the success or failure of an API request. 


* Codes in the <code>2xx</code> range indicate success. 

* Codes in the <code>4xx</code> range indicate an error owing due to unauthorize access, incorrect request parameters or body etc.

* Code in the <code>5xx</code> range indicate an eror with SendPost's servers ( internal service issue or maintenance )


<aside class=\"info\">
SendPost all responses return <code>created</code> in UNIX nano epoch timestamp. 
</aside>


## Authentication

SendPost uses API keys for authentication. You can register a new SendPost API key at our [developer portal](https://app.sendpost.io/register).


SendPost expects the API key to be included in all API requests to the server in a header that looks like the following:


`X-SubAccount-ApiKey: AHEZEP8192SEGH`


This API key is used for all Sub-Account level operations such as:

* Sending emails

* Retrieving stats regarding open, click, bounce, unsubscribe and spam

* Uploading suppressions list

* Verifying sending domains
and more

In addition to <code>X-SubAccount-ApiKey</code> you also have another API Key <code>X-Account-APIKey</code> which is used for Account level operations such as :

* Creating and managing sub-accounts

* Allocating IPs for your account

* Getting overall billing and usage information

* Email List validation

* Creating and managing alerts
and more


<aside class=\"notice\">
You must look at individual API reference page to look at whether <code>X-SubAccount-ApiKey</code> is required or <code>X-Account-ApiKey</code>
</aside>


In case an incorrect API Key header is specified or if it is missed you will get HTTP Response 401 ( Unauthorized ) response from SendPost.


## HTTP Response Headers


Code           | Reason                 | Details
---------------| -----------------------| -----------
200            | Success                | Everything went well
401            | Unauthorized           | Incorrect or missing API header either <code>X-SubAccount-ApiKey</code> or <code>X-Account-ApiKey</code>
403            | Forbidden              | Typically sent when resource with same name or details already exist
406            | Missing resource id    | Resource id specified is either missing or doesn't exist
422            | Unprocessable entity   | Request body is not in proper format
500            | Internal server error  | Some error happened at SendPost while processing API request
503            | Service Unavailable    | SendPost is offline for maintenance. Please try again later

# API SDKs

We have native SendPost SDKs in the following programming languages. You can integrate with them or create your own SDK with our API specification. In case you need any assistance with respect to API then do reachout to our team from website chat or email us at **hello@sendpost.io**


* [PHP](https://github.com/sendpost/sendpost_php_sdk)

* [Javascript](https://github.com/sendpost/sendpost_javascript_sdk)

* [Ruby](https://github.com/sendpost/sendpost_ruby_sdk)

* [Python](https://github.com/sendpost/sendpost_python_sdk)

* [Golang](https://github.com/sendpost/sendpost_go_sdk)


# API Reference

SendX REST API can be broken down into two major sub-sections:


* Sub-Account

* Account 


Sub-Account API operations enable common email sending API use-cases like sending bulk email, adding new domains or senders for email sending programmatically, retrieving stats, adding suppressions etc. All Sub-Account API operations need to pass <code>X-SubAccount-ApiKey</code> header with every API call.


The Account API operations allow users to manage multiple sub-accounts and manage IPs. A single parent SendPost account can have 100's of sub-accounts. You may want to create sub-accounts for different products your company is running or to segregate types of emails or for managing email sending across multiple customers of yours.


# SMTP Reference

Simple Mail Transfer Protocol (SMTP) is a quick and easy way to send email from one server to another. SendPost provides an SMTP service that allows you to deliver your email via our servers instead of your own client or server. 
This means you can count on SendPost's delivery at scale for your SMTP needs. 


## Integrating SMTP 


1. Get the SMTP `username` and `password` from your SendPost account.

2. Set the server host in your email client or application to `smtp.sendpost.io`. This setting is sometimes referred to as the external SMTP server or the SMTP relay.

3. Set the `username` and `password`.

4. Set the port to `587` (or as specified below).

## SMTP Ports


- For an unencrypted or a TLS connection, use port `25`, `2525` or `587`.

- For a SSL connection, use port `465`

- Check your firewall and network to ensure they're not blocking any of our SMTP Endpoints.


SendPost supports STARTTLS for establishing a TLS-encrypted connection. STARTTLS is a means of upgrading an unencrypted connection to an encrypted connection. There are versions of STARTTLS for a variety of protocols; the SMTP version is defined in [RFC 3207](https://www.ietf.org/rfc/rfc3207.txt).


To set up a STARTTLS connection, the SMTP client connects to the SendPost SMTP endpoint `smtp.sendpost.io` on port 25, 587, or 2525, issues an EHLO command, and waits for the server to announce that it supports the STARTTLS SMTP extension. The client then issues the STARTTLS command, initiating TLS negotiation. When negotiation is complete, the client issues an EHLO command over the new encrypted connection, and the SMTP session proceeds normally.


<aside class=\"success\">
If you are unsure which port to use, a TLS connection on port 587 is typically recommended.
</aside>


## Sending email from your application


```javascript
\"use strict\";

const nodemailer = require(\"nodemailer\");

async function main() {
// create reusable transporter object using the default SMTP transport
let transporter = nodemailer.createTransport({
host: \"smtp.sendpost.io\",
port: 587,
secure: false, // true for 465, false for other ports
auth: {
user:  \"<username>\" , // generated ethereal user
pass: \"<password>\", // generated ethereal password
},
requireTLS: true,
debug: true,
logger: true,
});

// send mail with defined transport object
try {
let info = await transporter.sendMail({
from: 'erlich@piedpiper.com',
to: 'gilfoyle@piedpiper.com',
subject: 'Test Email Subject',
html: '<h1>Hello Geeks!!!</h1>',
});
console.log(\"Message sent: %s\", info.messageId);
} catch (e) {
console.log(e)
}
}

main().catch(console.error);
```

For PHP


```php
<?php
// Import PHPMailer classes into the global namespace
use PHPMailer\\PHPMailer\\PHPMailer;
use PHPMailer\\PHPMailer\\SMTP;
use PHPMailer\\PHPMailer\\Exception;

// Load Composer's autoloader
require 'vendor/autoload.php';

$mail = new PHPMailer(true);

// Settings
try {
$mail->SMTPDebug = SMTP::DEBUG_CONNECTION;                  // Enable verbose debug output
$mail->isSMTP();                                            // Send using SMTP
$mail->Host       = 'smtp.sendpost.io';                     // Set the SMTP server to send through
$mail->SMTPAuth   = true;                                   // Enable SMTP authentication
$mail->Username   = '<username>';                           // SMTP username
$mail->Password   = '<password>';                           // SMTP password
$mail->SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS;         // Enable implicit TLS encryption
$mail->Port       = 587;                                    // TCP port to connect to; use 587 if you have set `SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS`

//Recipients
$mail->setFrom('erlich@piedpiper.com', 'Erlich');
$mail->addAddress('gilfoyle@piedpiper.com', 'Gilfoyle');

//Content
$mail->isHTML(true);                                  //Set email format to HTML
$mail->Subject = 'Here is the subject';
$mail->Body    = 'This is the HTML message body <b>in bold!</b>';
$mail->AltBody = 'This is the body in plain text for non-HTML mail clients';

$mail->send();
echo 'Message has been sent';

} catch (Exception $e) {
echo \"Message could not be sent. Mailer Error: {$mail->ErrorInfo}\";
}
```
For Python
```python
#!/usr/bin/python3

import sys
import os
import re

from smtplib import SMTP
import ssl

from email.mime.text import MIMEText

SMTPserver = 'smtp.sendpost.io'
PORT = 587
sender =     'erlich@piedpiper.com'
destination = ['gilfoyle@piedpiper.com']

USERNAME = \"<username>\"
PASSWORD = \"<password>\"

# typical values for text_subtype are plain, html, xml
text_subtype = 'plain'

content=\"\"\"\\
Test message
\"\"\"

subject=\"Sent from Python\"

try:
msg = MIMEText(content, text_subtype)
msg['Subject']= subject
msg['From']   = sender

conn = SMTP(SMTPserver, PORT)
conn.ehlo()
context = ssl.create_default_context()
conn.starttls(context=context)  # upgrade to tls
conn.ehlo()
conn.set_debuglevel(True)
conn.login(USERNAME, PASSWORD)

try:
resp = conn.sendmail(sender, destination, msg.as_string())
print(\"Send Mail Response: \", resp)
except Exception as e:
print(\"Send Email Error: \", e)
finally:
conn.quit()

except Exception as e:
print(\"Error:\", e)
```
For Golang
```go
package main

import (
\"fmt\"
\"net/smtp\"
\"os\"
)

// Sending Email Using Smtp in Golang

func main() {

username := \"<username>\"
password := \"<password>\"

from := \"erlich@piedpiper.com\"
toList := []string{\"gilfoyle@piedpiper.com\"}
host := \"smtp.sendpost.io\"
port := \"587\" // recommended

// This is the message to send in the mail
msg := \"Hello geeks!!!\"

// We can't send strings directly in mail,
// strings need to be converted into slice bytes
body := []byte(msg)

// PlainAuth uses the given username and password to
// authenticate to host and act as identity.
// Usually identity should be the empty string,
// to act as username.
auth := smtp.PlainAuth(\"\", username, password, host)

// SendMail uses TLS connection to send the mail
// The email is sent to all address in the toList,
// the body should be of type bytes, not strings
// This returns error if any occured.
err := smtp.SendMail(host+\":\"+port, auth, from, toList, body)

// handling the errors
if err != nil {
fmt.Println(err)
os.Exit(1)
}

fmt.Println(\"Successfully sent mail to all user in toList\")
}

```
For Java
```java
// implementation 'com.sun.mail:javax.mail:1.6.2'

import java.util.Properties;

import javax.mail.Message;
import javax.mail.Session;
import javax.mail.Transport;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;

public class SMTPConnect {

// This address must be verified.
static final String FROM = \"erlich@piedpiper.com\";
static final String FROMNAME = \"Erlich Bachman\";

// Replace recipient@example.com with a \"To\" address. If your account
// is still in the sandbox, this address must be verified.
static final String TO = \"gilfoyle@piedpiper.com\";

// Replace smtp_username with your SendPost SMTP user name.
static final String SMTP_USERNAME = \"<username>\";

// Replace smtp_password with your SendPost SMTP password.
static final String SMTP_PASSWORD = \"<password>\";

// SMTP Host Name
static final String HOST = \"smtp.sendpost.io\";

// The port you will connect to on SendPost SMTP Endpoint.
static final int PORT = 587;

static final String SUBJECT = \"SendPost SMTP Test (SMTP interface accessed using Java)\";

static final String BODY = String.join(
System.getProperty(\"line.separator\"),
\"<h1>SendPost SMTP Test</h1>\",
\"<p>This email was sent with SendPost using the \",
\"<a href='https://github.com/eclipse-ee4j/mail'>Javamail Package</a>\",
\" for <a href='https://www.java.com'>Java</a>.\"
);

public static void main(String[] args) throws Exception {

// Create a Properties object to contain connection configuration information.
Properties props = System.getProperties();
props.put(\"mail.transport.protocol\", \"smtp\");
props.put(\"mail.smtp.port\", PORT);
props.put(\"mail.smtp.starttls.enable\", \"true\");
props.put(\"mail.smtp.debug\", \"true\");
props.put(\"mail.smtp.auth\", \"true\");

// Create a Session object to represent a mail session with the specified properties.
Session session = Session.getDefaultInstance(props);

// Create a message with the specified information.
MimeMessage msg = new MimeMessage(session);
msg.setFrom(new InternetAddress(FROM,FROMNAME));
msg.setRecipient(Message.RecipientType.TO, new InternetAddress(TO));
msg.setSubject(SUBJECT);
msg.setContent(BODY,\"text/html\");

// Create a transport.
Transport transport = session.getTransport();

// Send the message.
try {
System.out.println(\"Sending...\");

// Connect to SendPost SMTP using the SMTP username and password you specified above.
transport.connect(HOST, SMTP_USERNAME, SMTP_PASSWORD);

// Send the email.
transport.sendMessage(msg, msg.getAllRecipients());
System.out.println(\"Email sent!\");

} catch (Exception ex) {

System.out.println(\"The email was not sent.\");
System.out.println(\"Error message: \" + ex.getMessage());
System.out.println(ex);
}
// Close and terminate the connection.
}
}
```

Many programming languages support sending email using SMTP. This capability might be built into the programming language itself, or it might be available as an add-on, plug-in, or library. You can take advantage of this capability by sending email through SendPost from within application programs that you write.

We have provided examples in Python3, Golang, Java, PHP, JS.

# API Contract Versioning (Public REST)

The public REST API uses a versioned response contract so field changes stay non-breaking:

* Send `X-SendPost-Public-Contract: v1` to opt into the current v1 response shape, or `legacy` for the pre-v1 shape. If the header is omitted, the applied contract is policy-driven — `legacy` before the published sunset date, `v1` after it.
* Every response echoes `X-SendPost-Public-Contract: <applied>`. When the `legacy` contract is served, responses also include `Deprecation: true`, `Sunset: <RFC1123 date>`, and `Link: <doc-url>; rel=\"deprecation\"`.
* Migrate to `v1` before the sunset date. Notable legacy → v1 field changes: Suppression `smtp_error` → `smtpError`, Stat `email_type` → `emailType`.

> `X-SendPost-Private-Api: true` is an internal header used only by the SendPost dashboard to receive richer internal objects. It is not part of the public SDK contract and should not be set by API integrations.


This SDK is automatically generated by the [OpenAPI Generator](https://openapi-generator.tech) project:

- API version: 1.3.0
- Package version: 3.0.0
- Generator version: 7.13.0
- Build package: org.openapitools.codegen.languages.RubyClientCodegen

## Installation

### Build a gem

To build the Ruby code into a gem:

```shell
gem build sendpost_ruby_sdk.gemspec
```

Then either install the gem locally:

```shell
gem install ./sendpost_ruby_sdk-3.0.0.gem
```

(for development, run `gem install --dev ./sendpost_ruby_sdk-3.0.0.gem` to install the development dependencies)

or publish the gem to a gem hosting service, e.g. [RubyGems](https://rubygems.org/).

Finally add this to the Gemfile:

    gem 'sendpost_ruby_sdk', '~> 3.0.0'

### Install from Git

If the Ruby gem is hosted at a git repository: https://github.com/sendpost/sendpost-ruby-sdk, then add the following in the Gemfile:

    gem 'sendpost_ruby_sdk', :git => 'https://github.com/sendpost/sendpost-ruby-sdk.git'

### Include the Ruby code directly

Include the Ruby code directly using `-I` as follows:

```shell
ruby -Ilib script.rb
```

## Getting Started

Please follow the [installation](#installation) procedure and then run the following code:

```ruby
# Load the gem
require 'sendpost_ruby_sdk'

# Setup authorization
Sendpost.configure do |config|
  # Configure API key authorization: subAccountAuth
  config.api_key['X-SubAccount-ApiKey'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-SubAccount-ApiKey'] = 'Bearer'
end

api_instance = Sendpost::DomainApi.new
create_domain_request = Sendpost::CreateDomainRequest.new({name: 'piedpiper.com'}) # CreateDomainRequest | 

begin
  #Create Domain
  result = api_instance.create_sub_account_domain(create_domain_request)
  p result
rescue Sendpost::ApiError => e
  puts "Exception when calling DomainApi->create_sub_account_domain: #{e}"
end

```

## Documentation for API Endpoints

All URIs are relative to *https://api.sendpost.io/api/v1*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*Sendpost::DomainApi* | [**create_sub_account_domain**](docs/DomainApi.md#create_sub_account_domain) | **POST** /subaccount/domain | Create Domain
*Sendpost::DomainApi* | [**delete_sub_account_domain**](docs/DomainApi.md#delete_sub_account_domain) | **DELETE** /subaccount/domain/{domain_id} | Delete Domain
*Sendpost::DomainApi* | [**get_all_domains**](docs/DomainApi.md#get_all_domains) | **GET** /subaccount/domain | List Domains
*Sendpost::DomainApi* | [**get_sub_account_domain**](docs/DomainApi.md#get_sub_account_domain) | **GET** /subaccount/domain/{domain_id} | Get Domain
*Sendpost::EmailApi* | [**send_email**](docs/EmailApi.md#send_email) | **POST** /subaccount/email/ | Send Email
*Sendpost::EmailApi* | [**send_email_with_template**](docs/EmailApi.md#send_email_with_template) | **POST** /subaccount/email/template | Send Email With Template
*Sendpost::IPApi* | [**allocate_new_ip**](docs/IPApi.md#allocate_new_ip) | **PUT** /account/ip/allocate | Allocate IP
*Sendpost::IPApi* | [**delete_ip**](docs/IPApi.md#delete_ip) | **DELETE** /account/ip/{ip_id} | Delete IP
*Sendpost::IPApi* | [**get_all_ips**](docs/IPApi.md#get_all_ips) | **GET** /account/ip/ | List IPs
*Sendpost::IPApi* | [**get_specific_ip**](docs/IPApi.md#get_specific_ip) | **GET** /account/ip/{ip_id} | Get IP
*Sendpost::IPApi* | [**update_ip**](docs/IPApi.md#update_ip) | **PUT** /account/ip/{ip_id} | Update IP
*Sendpost::IPPoolsApi* | [**create_ip_pool**](docs/IPPoolsApi.md#create_ip_pool) | **POST** /account/ippool | Create IPPool
*Sendpost::IPPoolsApi* | [**delete_ip_pool**](docs/IPPoolsApi.md#delete_ip_pool) | **DELETE** /account/ippool/{ippool_id} | Delete IPPool
*Sendpost::IPPoolsApi* | [**get_all_ip_pools**](docs/IPPoolsApi.md#get_all_ip_pools) | **GET** /account/ippool | List IPPools
*Sendpost::IPPoolsApi* | [**get_ip_pool_by_id**](docs/IPPoolsApi.md#get_ip_pool_by_id) | **GET** /account/ippool/{ippool_id} | Get IPPool
*Sendpost::IPPoolsApi* | [**update_ip_pool**](docs/IPPoolsApi.md#update_ip_pool) | **PUT** /account/ippool/{ippool_id} | Update IPPool
*Sendpost::MessageApi* | [**get_all_messages**](docs/MessageApi.md#get_all_messages) | **GET** /account/message | List Messages
*Sendpost::MessageApi* | [**get_message_by_id**](docs/MessageApi.md#get_message_by_id) | **GET** /account/message/{message_id} | Get Message
*Sendpost::StatsApi* | [**account_subaccount_stat_subaccount_id_aggregate_get**](docs/StatsApi.md#account_subaccount_stat_subaccount_id_aggregate_get) | **GET** /account/subaccount/stat/{subaccount_id}/aggregate | Get Aggregate Stats
*Sendpost::StatsApi* | [**account_subaccount_stat_subaccount_id_get**](docs/StatsApi.md#account_subaccount_stat_subaccount_id_get) | **GET** /account/subaccount/stat/{subaccount_id} | List Stats
*Sendpost::StatsApi* | [**get_aggregate_stats_by_group**](docs/StatsApi.md#get_aggregate_stats_by_group) | **GET** /account/subaccount/stat/{subaccount_id}/group | Get Group Aggregate Stats
*Sendpost::StatsAApi* | [**get_account_aggregate_stats**](docs/StatsAApi.md#get_account_aggregate_stats) | **GET** /account/stat/aggregate | Get Account Aggregate Stats
*Sendpost::StatsAApi* | [**get_account_aggregate_stats_by_group**](docs/StatsAApi.md#get_account_aggregate_stats_by_group) | **GET** /account/stat/aggregate/group | Get Account Group Aggregate Stats
*Sendpost::StatsAApi* | [**get_account_stats_by_group**](docs/StatsAApi.md#get_account_stats_by_group) | **GET** /account/stat/group | List Account Group Stats
*Sendpost::StatsAApi* | [**get_all_account_stats**](docs/StatsAApi.md#get_all_account_stats) | **GET** /account/stat | List Account Stats
*Sendpost::SubAccountApi* | [**create_sub_account**](docs/SubAccountApi.md#create_sub_account) | **POST** /account/subaccount/ | Create Sub-Account
*Sendpost::SubAccountApi* | [**delete_sub_account**](docs/SubAccountApi.md#delete_sub_account) | **DELETE** /account/subaccount/{subaccount_id} | Delete Sub-Account
*Sendpost::SubAccountApi* | [**get_all_sub_accounts**](docs/SubAccountApi.md#get_all_sub_accounts) | **GET** /account/subaccount/ | List Sub-Accounts
*Sendpost::SubAccountApi* | [**get_sub_account**](docs/SubAccountApi.md#get_sub_account) | **GET** /account/subaccount/{subaccount_id} | Get Sub-Account
*Sendpost::SubAccountApi* | [**update_sub_account**](docs/SubAccountApi.md#update_sub_account) | **PUT** /account/subaccount/{subaccount_id} | Update Sub-Account
*Sendpost::SuppressionApi* | [**create_suppression**](docs/SuppressionApi.md#create_suppression) | **POST** /subaccount/suppression | Create Suppressions
*Sendpost::SuppressionApi* | [**delete_suppression**](docs/SuppressionApi.md#delete_suppression) | **DELETE** /subaccount/suppression | Delete Suppressions
*Sendpost::SuppressionApi* | [**get_suppression_list**](docs/SuppressionApi.md#get_suppression_list) | **GET** /subaccount/suppression | List Suppressions
*Sendpost::WebhookApi* | [**create_webhook**](docs/WebhookApi.md#create_webhook) | **POST** /account/webhook | Create Webhook
*Sendpost::WebhookApi* | [**delete_webhook**](docs/WebhookApi.md#delete_webhook) | **DELETE** /account/webhook/{webhook_id} | Delete Webhook
*Sendpost::WebhookApi* | [**get_all_webhooks**](docs/WebhookApi.md#get_all_webhooks) | **GET** /account/webhook | List Webhooks
*Sendpost::WebhookApi* | [**get_webhook**](docs/WebhookApi.md#get_webhook) | **GET** /account/webhook/{webhook_id} | Get Webhook
*Sendpost::WebhookApi* | [**update_webhook**](docs/WebhookApi.md#update_webhook) | **PUT** /account/webhook/{webhook_id} | Update Webhook


## Documentation for Models

 - [Sendpost::AccountCycleUsage](docs/AccountCycleUsage.md)
 - [Sendpost::AccountStats](docs/AccountStats.md)
 - [Sendpost::AccountWebhookWithStats](docs/AccountWebhookWithStats.md)
 - [Sendpost::AggregateStat](docs/AggregateStat.md)
 - [Sendpost::AggregateStats](docs/AggregateStats.md)
 - [Sendpost::Attachment](docs/Attachment.md)
 - [Sendpost::BlacklistLinks](docs/BlacklistLinks.md)
 - [Sendpost::BlacklistResource](docs/BlacklistResource.md)
 - [Sendpost::BlacklistedOn](docs/BlacklistedOn.md)
 - [Sendpost::CopyTo](docs/CopyTo.md)
 - [Sendpost::CreateDomainRequest](docs/CreateDomainRequest.md)
 - [Sendpost::CreateSuppressionRequest](docs/CreateSuppressionRequest.md)
 - [Sendpost::CreateSuppressionRequestHardBounceInner](docs/CreateSuppressionRequestHardBounceInner.md)
 - [Sendpost::CreateSuppressionRequestManualInner](docs/CreateSuppressionRequestManualInner.md)
 - [Sendpost::CreateSuppressionRequestSpamComplaintInner](docs/CreateSuppressionRequestSpamComplaintInner.md)
 - [Sendpost::CreateSuppressionRequestUnsubscribeInner](docs/CreateSuppressionRequestUnsubscribeInner.md)
 - [Sendpost::DailyStatistics](docs/DailyStatistics.md)
 - [Sendpost::DateStat](docs/DateStat.md)
 - [Sendpost::DeleteResponse](docs/DeleteResponse.md)
 - [Sendpost::DeleteSubAccountResponse](docs/DeleteSubAccountResponse.md)
 - [Sendpost::DeleteSuppression200Response](docs/DeleteSuppression200Response.md)
 - [Sendpost::DeleteSuppressionRequest](docs/DeleteSuppressionRequest.md)
 - [Sendpost::DeleteSuppressionRequestSuppressionsInner](docs/DeleteSuppressionRequestSuppressionsInner.md)
 - [Sendpost::DeleteWebhookResponse](docs/DeleteWebhookResponse.md)
 - [Sendpost::Device](docs/Device.md)
 - [Sendpost::DnsRecord](docs/DnsRecord.md)
 - [Sendpost::Domain](docs/Domain.md)
 - [Sendpost::DomainStat](docs/DomainStat.md)
 - [Sendpost::EIP](docs/EIP.md)
 - [Sendpost::EmailAddress](docs/EmailAddress.md)
 - [Sendpost::EmailMessage](docs/EmailMessage.md)
 - [Sendpost::EmailMessageObject](docs/EmailMessageObject.md)
 - [Sendpost::EmailMessageWithTemplate](docs/EmailMessageWithTemplate.md)
 - [Sendpost::EmailResponse](docs/EmailResponse.md)
 - [Sendpost::EmailTypeStat](docs/EmailTypeStat.md)
 - [Sendpost::ErrorResponse](docs/ErrorResponse.md)
 - [Sendpost::ErrorResponseError](docs/ErrorResponseError.md)
 - [Sendpost::ErrorResponseErrorDetailsInner](docs/ErrorResponseErrorDetailsInner.md)
 - [Sendpost::Event](docs/Event.md)
 - [Sendpost::EventMetadata](docs/EventMetadata.md)
 - [Sendpost::GeoLocation](docs/GeoLocation.md)
 - [Sendpost::GroupStat](docs/GroupStat.md)
 - [Sendpost::IP](docs/IP.md)
 - [Sendpost::IPAllocationRequest](docs/IPAllocationRequest.md)
 - [Sendpost::IPDeletionResponse](docs/IPDeletionResponse.md)
 - [Sendpost::IPPool](docs/IPPool.md)
 - [Sendpost::IPPoolCreateRequest](docs/IPPoolCreateRequest.md)
 - [Sendpost::IPPoolDeleteResponse](docs/IPPoolDeleteResponse.md)
 - [Sendpost::IPPoolStat](docs/IPPoolStat.md)
 - [Sendpost::IPPoolUpdateRequest](docs/IPPoolUpdateRequest.md)
 - [Sendpost::IPStat](docs/IPStat.md)
 - [Sendpost::IPUpdateRequest](docs/IPUpdateRequest.md)
 - [Sendpost::Label](docs/Label.md)
 - [Sendpost::Member](docs/Member.md)
 - [Sendpost::Message](docs/Message.md)
 - [Sendpost::NewSubAccount](docs/NewSubAccount.md)
 - [Sendpost::NewWebhook](docs/NewWebhook.md)
 - [Sendpost::Os](docs/Os.md)
 - [Sendpost::PostmasterDomainStat](docs/PostmasterDomainStat.md)
 - [Sendpost::ProviderStat](docs/ProviderStat.md)
 - [Sendpost::RAIPPoolStat](docs/RAIPPoolStat.md)
 - [Sendpost::RDStat](docs/RDStat.md)
 - [Sendpost::RIPStat](docs/RIPStat.md)
 - [Sendpost::RStat](docs/RStat.md)
 - [Sendpost::Recipient](docs/Recipient.md)
 - [Sendpost::SDStat](docs/SDStat.md)
 - [Sendpost::SMTPAuth](docs/SMTPAuth.md)
 - [Sendpost::SeedContactStats](docs/SeedContactStats.md)
 - [Sendpost::Stat](docs/Stat.md)
 - [Sendpost::SubAccount](docs/SubAccount.md)
 - [Sendpost::SubAccountStat](docs/SubAccountStat.md)
 - [Sendpost::SubAccountStatForPool](docs/SubAccountStatForPool.md)
 - [Sendpost::Suppression](docs/Suppression.md)
 - [Sendpost::TPSPStat](docs/TPSPStat.md)
 - [Sendpost::UpdateSubAccount](docs/UpdateSubAccount.md)
 - [Sendpost::UpdateWebhook](docs/UpdateWebhook.md)
 - [Sendpost::UserAgent](docs/UserAgent.md)
 - [Sendpost::ValidationStat](docs/ValidationStat.md)
 - [Sendpost::Webhook](docs/Webhook.md)
 - [Sendpost::WebhookObject](docs/WebhookObject.md)


## Documentation for Authorization


Authentication schemes defined for the API:
### accountAuth


- **Type**: API key
- **API key parameter name**: X-Account-ApiKey
- **Location**: HTTP header

### subAccountAuth


- **Type**: API key
- **API key parameter name**: X-SubAccount-ApiKey
- **Location**: HTTP header

