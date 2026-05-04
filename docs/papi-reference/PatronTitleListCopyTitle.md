# PatronTitleListCopyTitle

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronTitleListCopyTitle.htm_

You are here:

## PatronTitleListCopyTitle

Copy a title from one list to another in a patron account.

|
|  
| POST
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/patrontitlelistcopytitle
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

<PatronTitleListCopyTitleData>

<FromRecordStoreID></FromRecordStoreID>

<FromPosition></FromPosition>

<ToRecordStoreID></ToRecordStoreID>

</PatronTitleListCopyTitleData>

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

Record store to copy the records from

|
|

FromPosition

|

Yes

|

Position of the title in the list. Note: A negative RecordID (-990) can be submitted instead of the title's position. The RecordID is a Unique Identifier for a record in the title list from the underlying table IRRecords.RecordID. This is not the Control Number or the Bib Record ID. It can be obtained from the PAPI API call PatronTitleListGetTitles.

|
|

ToRecordStoreID

|

Yes

|

Record store to add the records to

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

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/patrontitlelistcopytitle

### Return - Success

|
|

<PatronTitleListCopyTitleResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronTitleListCopyTitleResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronTitleListCopyTitleResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance"><

PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>Could not copy record because record-store '9999' does not exist.</ErrorMessage>

</PatronTitleListCopyTitleResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0