# PatronUpdateUserName

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronUpdateUserName.htm_

You are here:

## PatronUpdateUserName

This method allows a third party to add/update a patron’s username.

|
|  
| PUT
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/username/{NewUsername}
|  

### Authorization required?

Yes (use patron’s PIN in password/secret)

### URI Parameters

|
|

Name

|

Required

|

Description/Notes

|
|

PatronBarcode

|

Yes

|

The patron’s username or barcode

|
|

NewUsername

|

Yes

|

The new username associated with the patron

### XML Elements Returned

|
|

Name

|

Description/Notes

|
|

PAPIErrorCode

|

PAPI error code

|
|

ErrorMessage

|

Error or information message

### Example

|
|

https://egraham-r2vm.gisinfosystems.com/Plato-R2PAPIService/REST/public/v1/1033/100/
1/patron/eric1234/username/egraham

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronUpdateResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronUpdateResult>

### PAPI Error Codes Unique to This Method

|
| PAPI Error Code
|

Description

|
|

-3606

|

The username must be at least 4 characters but not longer than 50 characters.

|
|

-3607

|

The Username you entered is unavailable. Please try another Username.

|
|

-3608

|

All usernames must begin with a letter. Usernames can contain letters, numbers, and special characters. Spaces are not allowed, and special characters cannot be contiguous.

|
|

-3609

|

Username and barcode may not be the same.

|
|

-3610

|

The username you entered is identical to your previous username.

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0