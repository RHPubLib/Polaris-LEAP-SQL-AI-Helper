# AuthenticateStaffUser

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceAuthenticate.htm_

You are here:

## AuthenticateStaffUser

A call to AuthenticateStaffUser is required before calling any protected methods. Upon success, this method returns an access token and access secret. These are used to create the hash for protected methods. The access token is valid for 24 hours. Subsequent calls to AuthenticateStaffUser with the same domain account information generate a new access token, access secret, and expiration date. For more information about protected methods, see PAPI Protected Methods.

|
|  
| POST
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/authenticator/staff
|  

### Process Overview

IsAuthorizedPAPIPolarisUser

PAPI_IsAuthorizedPAPIPolarisUser - Verifies the user is in the PolarisUsers table and returns a PolarisUserID

IsStaffAuthenticationLocked

PAPI_IsStaffAuthenticationLocked - Check PAPIStaffAuthenticationFailures database table. If three failed attempts are made in the last five minutes, temporarily lock the account.

Authenticate user against the domain.

If failed:

- Call **PAPI_StaffAuthenticationFailed**.

- Update **PAPIStaffAuthenticationFailures** database table.

If success:

- Call **PAPI_StaffAuthenticationSucceeded**.

- Return access token and access secret.

- Set **AuthenticationExpDate** to current time + one day.

- Reset entry in **PAPIStaffAuthenticationFailure**s database table.

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

Domain

|

Yes

|

Domain name

|
|

Username

|

Yes

|

Username

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
| Error or information message.

|
|

AccessToken

|

Access token to be used in URI of protected method calls.

|
|

AccessSecret

|

AccessSecret used to create hash when calling protected methods.

|
|

PolarisUserID

|

Polaris User ID

|
|

BranchID

|

Polaris User’s Default Branch ID.

|
|

AuthExpDate

|

Expiration date of provided access token.

### Example

|
| https://[hostname]/PAPIService/REST/protected/v1/1033/100/1/authenticator/staff

### Body

|
|

<AuthenticationData>

<Domain>TestDomain</Domain>

<Username>StaffUser1</Username>

<Password>mypassword</Password>

</AuthenticationData>

### Return

|
|

HTTP/1.1 200 OK

<AuthenticationResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<AccessToken>IGYhCPGcutuKmZFcKUystVAkgmi4g1Db</AccessToken>

<AccessSecret>B8sD7y0CYOhlsIyk</AccessSecret>

<PolarisUserID>799</PolarisUserID>

<BranchID>5</BranchID>

<AuthExpDate>2011-07-26T15:48:39.437</AuthExpDate>

</AuthenticationResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0