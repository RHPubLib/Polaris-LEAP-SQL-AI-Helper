# PatronAccountCreateTitleList

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronAccountCreateTitleList.htm_

You are here:

## PatronAccountCreateTitleList

Creates a named title list in the patron account.

**Note: **The following characters are not valid in a list name and should not be passed into PAPI: plus, backslash, quotation marks (single or double), and pipe.

|
|  
| POST
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/patronaccountcreatetitlelist
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

### Request Body XML

|
|

<PatronAccountCreateTitleListData>

<RecordStoreName></RecordStoreName>

</PatronAccountCreateTitleListData>

### XML Body Elements

|
| Name
|

Required

|

Description/Notes

|
|

RecordStoreName

|

Yes

|

Name of record store

### XML Elements Returned

The following XML elements are returned.

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

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
patronaccountcreatetitlelis

### Body

|
|

<PatronAccountCreateTitleListData>

<RecordStoreName>Favorites</RecordStoreName>

</PatronAccountCreateTitleListData>

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronAccountCreateTitleListResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronAccountCreateTitleListResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronAccountCreateTitleListResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>Please enter a name for the title list</ErrorMessage>

</PatronAccountCreateTitleListResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0