# PatronTitleListCopyAllTitles

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronTitleListCopyAllTitles.htm_

You are here:

## PatronTitleListCopyAllTitles

Copy all titles from one list to another list in the patron account.

|
|  
| POST
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/patrontitlelistcopyalltitles
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

### Request Body XML

|
|

<PatronTitleListCopyAllTitlesData>

<FromRecordStoreID></FromRecordStoreID>

<ToRecordStoreID></ToRecordStoreID>

</PatronTitleListCopyAllTitlesData>

### XML Body Elements

|
| Name
|

Required

|

Description/Notes

|
|

FromRecordStoreID

|

Yes

|

Record store to copy the records from.

|
| ToRecordStoreID
| Yes
| Record store to add the records to.

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

Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/patrontitlelistcopyalltitles

### Body

|
|

<PatronTitleListCopyAllTitlesData>

<FromRecordStoreID>123</FromRecordStoreID>

<ToRecordStoreID>720</ToRecordStoreID>

</PatronTitleListCopyAllTitlesData>

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronTitleListCopyAllTitlesResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronTitleListCopyAllTitlesResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

Content-Type: application/xml; charset=utf-8

<PatronTitleListCopyAllTitlesResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>Could not copy record because record-store '999' does not exist.</ErrorMessage>

</PatronTitleListCopyAllTitlesResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0