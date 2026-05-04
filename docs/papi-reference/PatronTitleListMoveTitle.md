# PatronTitleListMoveTitle

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronTitleListMoveTitle.htm_

You are here:

## PatronTitleListMoveTitle

Moves a specified bibliographic record from one title list to another. Both title lists are in the same patron account.

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

<PatronTitleListMoveTitleData>

<FromRecordStoreID></FromRecordStoreID>

<FromPosition></FromPosition>

<ToRecordStoreID></ToRecordStoreID>

</PatronTitleListMoveTitleData>

### XML Body Elements

|
| Name
|

Required

|

Description/Notes

|
| FromRecordStoreID
| Yes
| Record store to move (remove) the record from.

|
| FromPosition
| Yes
| Position of the title in the list.

|
| ToRecordStoreID
| Yes
| Record store to add the record to.

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

### Examples

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/patrontitlelistmovetitle

### **Body**

|
|

<PatronTitleListMoveTitleData>

<FromRecordStoreID>123</FromRecordStoreID>

<FromPosition>3</FromPosition>

<ToRecordStoreID>720</ToRecordStoreID>

</PatronTitleListMoveTitleData>

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronTitleListMoveTitleResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronTitleListMoveTitleResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronTitleListMoveTitleResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>Could not move record because record-store '9999' does not exist.</ErrorMessage>

</PatronTitleLisMoveTitleResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0