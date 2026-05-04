# AuthenticatePatron

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceAuthenticatePatron.htm_

You are here:

## AuthenticatePatron

A call to AuthenticatePatron is required before calling any public method that requires a patron’s password. Starting with Polaris 7.0, the AuthenticatePatron endpoint uses a different authentication scheme depending on the following configuration setting (legacy is the default).

**<add key="LegacyPatronAuthenticationSchemeEnabled" value="true"/>**

The AuthExpDate will be null if the authentication scheme is legacy, otherwise the AuthExpDate indicates when the AccessSecret expires (currently 24 hours after successfully authenticating the patron).

**Notes: **

- It is strongly recommended that you use HTTPS with this call. The HTTP body data will contain the patron’s barcode and password.

- Changing the authentication scheme does not require any changes to third party applications.

- We strongly encourage third party vendors to use the AccessSecret field in the patron authentication response for hashing purposes.

### URI

|
|  
| POST
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/authenticator/patron
|  

### Authorization Required?

Yes

### XML Body Elements

|
| Name
|

Required

|

Description/Notes

|
|

Barcode

|

Yes

|

Barcode or Username

|
|

Password

|

Yes

|

Password

### XML Elements Returned

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

PAPI Error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

|
| AccessToken
| The AccessToken field is considered deprecated, but there is no concrete timeline for removing it from the response.
Access token to be used in place of the patron’s password when building the hash for patron methods.

|
| AccessSecret
| The AccessSecret and AccessToken fields in the patron authentication response will always have the same value.

|
| AuthExpDate
| AuthExpDate indicates when the AccessSecret expires. The expiration is 24 hours after successfully authenticating the patron.

|
| PatronID
| Patron ID

### Example

|
| https://[hostname]/PAPIService/REST/public/v1/1033/100/1/authenticator/patron

### Body

|
|

<PatronAuthenticationData>

<Barcode>21756003332060</Barcode>

<Password>1234</Password>

</PatronAuthenticationData>

**Note**: If three failed authentication attempts are made in five minutes, the account is temporarily locked.

### Return

|
|

HTTP/1.1 200 OK

<PatronAuthenticationResult>

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>string</ErrorMessage>

<AccessToken>string</AccessToken>

<PatronID>358255</PatronID>

<AccessSecret>string</AccessSecret>

<AuthExpDate>2021-06-03T17:16:35.700Z</AuthExpDate>

</PatronAuthenticationResult>

**Error Code**

-3001 Unable to authenticate the patron credentials.

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0