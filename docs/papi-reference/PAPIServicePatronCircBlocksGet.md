# PatronCirculateBlocksGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronCircBlocksGet.htm_

You are here:

## PatronCirculateBlocksGet

Validate that a patron is part of the Polaris database, and return blocks and status telling the caller if the given patron is allowed to perform a circulation activity (checkout).

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/circulationblocks
|  

### Authorization required?

Yes

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

Barcode of patron

### Query String Parameters

|
| Name
|

Values

|

Required

|

Description/Notes

|
|

vendorID

|

varchar

|

No

|

Ebook vendor ID'

|
|

vendorContractID

|

varchar

|

No

|

Ebook vendor contract ID

|
|

usernameSupported

|

Boolean

|

No

|

Can barcode be validated as username

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
| Barcode
| The item barcode

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

Patron’s record ID

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
|

PatronBarcode

|

Patron’s barcode

|
|

AssignedBranchName

|

Name of the branch to which the patron is assigned

|
|

ExpirationDate

|

Patron’s registration expiration date

|
|

OverridePasswordUsed

|

Was password used the staff override password. (Set only if nValidationTypeID = 3)

|
|

Blocks

|

List of Blocks as follows:

PatronID
PatronName
BlockDescription

|
|

CanPatronCirculate

|

T/F value

|
| EmailAddress
| Patron email address

|
| NameFirst
| Patron's first name

|
| NameLast
| Patron's last name

|
| NameMiddle
| Patron's middle name

### Example

|
| http://[HOSTNAME]/PAPIService/REST/public/v1/1033/100/1/patron/{patron_barcode}/
circulationblocks

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronCirculateBlocksResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<Barcode>21234000000166</Barcode>

<ValidPatron>true</ValidPatron>

<PatronID>356971</PatronID>

<PatronCodeID>1</PatronCodeID>

<AssignedBranchID>3</AssignedBranchID>

<PatronBarcode>21234000000166</PatronBarcode>

<AssignedBranchName>Amsterdam Free Library</AssignedBranchName>

<ExpirationDate>2014-11-05T00:00:00</ExpirationDate>

<OverridePasswordUsed>false</OverridePasswordUsed>

<Blocks>

<Block>

<PatronID>356971</PatronID>

<PatronName>Tester, Otto </PatronName>

<BlockDescription>Patron is not allowed to access this vendor account.</BlockDescription>

</Block>

</Blocks>

<CanPatronCirculate>false</CanPatronCirculate>

</PatronCirculateBlocksResult>

### Return - Failed

|
|

HTTP/1.1 401 Unauthorized

WWW-Authenticate: PWS realm="Polaris API"

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0