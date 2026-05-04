# PatronTitleListDeleteAllTitles

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronTitleListDeleteAllTitles.htm_

You are here:

## PatronTitleListDeleteAllTitles

Removes all the records from a given list, but leaves the empty list in the patron account.

|
|  
| DELETE
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/patrontitlelistdeletealltitles?list={list_id}
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

Barcode of patron.

### Query parameters

|
| Name
|

Required

|

Description/Notes

|
|

list

|

Yes

|

Unique identifier for the list.

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

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/patrontitlelistdeletealltitles?list=700

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronTitleListDeleteAllTitlesResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronTitleListDeleteAllTitlesResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronTitleListDeleteAllTitlesResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance"><

PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>Could not truncate record-store '999' because it does not exist.</ErrorMessage>

</PatronTitleListDeleteAllTitlesResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0