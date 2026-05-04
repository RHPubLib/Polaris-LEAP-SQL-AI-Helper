# PatronValidate

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronValidate.htm_

You are here:

## PatronValidate

Validate that a patron is part of the Polaris database.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}
|  

### Authorization required?

Yes

### URI Parameters

|
| Name
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

Barcode of patron

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
|

Barcode

|

Patron's barcode

|
|

ValidPatron

|

Does patron exist in the Polaris database?

false - No
true - Yes

|
|

PatronID

|

Patron's record ID

|
|

PatronCodeID

|

Patron’s patron code ID

|
|

AssignedBranchID

|

ID of the branch to which the patron is assigned

|
| PatronBarcode
| Barcode of patron.

|
|

AssignedBranchName

|

Name of the branch to which the patron is assigned

|
|

ExpirationDate

|

Patron's registration expiration date

|
|

OverridePasswordUsed

|

Was the staff override passwordused. Set only if nValidationTypeID = 3.

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronValidateResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<Barcode>21756003332022</Barcode>

<ValidPatron>true</ValidPatron>

<PatronID>299377</PatronID>

<AssignedBranchID>90</AssignedBranchID>

<AssignedBranchName>Saratoga Springs Public Library</AssignedBranchName>

<ExpirationDate>2010-04-08T00:00:00</ExpirationDate>

</PatronValidateResult>

### Return - Failed

|
|

HTTP/1.1 401 Unauthorized

WWW-Authenticate: PWS realm="Polaris API"

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0