checkmobi-php
=================

#Requirements

You can use `CURL` extension:

```
php-curl
php-openssl
```

Or instead `CURL` you can use `HTTP_Request2`

```
pear package HTTP_Request2
```

#API Documentation

CheckMobi APIs are based on `HTTP` methods, which make it easy to integrate into your own products. You can use any `HTTP` client in any programming language to interact with the API.
The SDK is only a wrapper over the REST API described [here][1]

#Basic Usage for SDK:

For all properties accepted by the following methods check [the documentation][1].

```php
//create an instance of `CheckMobiRest`

$api = new CheckMobiRest("secret key here");

//get list of countries & flags

$response = $api->GetCountriesList();

//get prefixes

$response = $api->GetPrefixes();

//checking a number for being valid

$response = $api->CheckNumber(array("number" => "+number here"));

//validate a number using "Missed call method". (type can be : sms, ivr, cli, reverse_cli)

$response = $api->RequestValidation(array("type" => "reverse_cli", "number" => "+number_here"));

//verify a pin for a certain request

$response = $api->VerifyPin(array("id" => "request id here", "pin" => "5659"));

//check validation status for a certain request

$response = $api->ValidationStatus(array("id" => "request id here"));

//send a custom sms

$response = $api->SendSMS(array("to" => "number here", "text" => "message here"));

//get details about an SMS

$response = $api->GetSmsDetails(array("id" => "sms id here"));

//place a call

$event = [["action" => "speak", "text" => "Hello world", "loop" => 2, "language" => "en-US"]];
$params = ["from" => "+number here", "to" => "+number here", "events" => $event];
$response = $api->PlaceCall($params);

//get a call details

$response = $api->GetCallDetails(array("id" => "call id here"));

//hangup a call

$response = $api->HangUpCall(array("id" => "call id here"));

```

[1]:https://checkmobi.com/documentation.html
