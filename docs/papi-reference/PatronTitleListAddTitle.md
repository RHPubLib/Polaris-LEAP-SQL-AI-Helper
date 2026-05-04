# PatronTitleListAddTitle

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronTitleListAddTitle.htm_

You are here:

## PatronTitleListAddTitle

Adds the specified bibliographic record to the specified list in the patron account.

|
|  
| POST
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/patrontitlelistaddtitle
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

<PatronTitleListAddTitleData>

<RecordStoreID></RecordStoreID>

<RecordName></RecordName>

<LocalControlNumber></LocalControlNumber>

</PatronTitleListAddTitleData>

### XML Body Elements

|
| Name
|

Required

|

Description/Notes

|
| RecordStoreID
| Yes
| Unique identifier for the record store

|
| RecordName
| No
| Title of the item being added to the list. If present, element is ignored.

|
| LocalControlNumber
| Yes
| Control number of the tile

### XML Elements Returned

|
| Name
|

Description/Notes

|
| Position
| Title position in the list

|
| RecordID
| Unique Identifier for the title in the list

|
| LocalControlNumber
| Control number of the tile

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/patrontitlelistaddtitle

### Body

|
|

<PatronTitleListAddTitleData>

<RecordStoreID>123</RecordStoreID>

<RecordName>Polaris 101: Tips and tricks</RecordName>

<LocalControlNumber>101010</LocalControlNumber>

</PatronTitleListAddTitleData>

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronTitleListAddTitleResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<Position>1</Position>

<RecordID>19498</RecordID>

</PatronTitleListAddTitleResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronTitleListAddTitleResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>Could not add record 'Polaris 101: Tips and tricks' because it does not exist.</ErrorMessage>

<Position>0</Position>

<RecordID>0</RecordID>

</PatronTitleListAddTitleResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0