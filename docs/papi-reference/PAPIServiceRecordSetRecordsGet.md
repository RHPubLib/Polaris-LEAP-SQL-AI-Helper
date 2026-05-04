# RecordSetRecordsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceRecordSetRecordsGet.htm_

You are here:

## RecordSetRecordsGet

This method returns a list of record IDs in a specified bibliographic, item, or patron record set.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/recordsets/{RecordSetID}/records
|  

### Authorization required

Yes

### Protected method

Yes

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
| RecordSetID
| Yes
| Bibliographic, item, or patron record set ID

### Query String Parameters

|
| Name
|

Required

|

Description/Notes

|
|

userid

|

Yes

|

User ID (not patron ID)

|
|

wsid

|

Yes

|

Workstation ID

|
| startIndex
| Yes
| The starting index position of a page of internal bibliographic, item, or patron IDs from a bibliographic, item, or patron record set.

|
| numRecords
| Yes
| The number of bibliographic, item, or patron IDs to return in the page from a record set. This allows for the use of multiple calls to get all bibliographic, item, or patron IDs from a record set.

### XML Elements Returned

List of bibliographic, item, or patron records in the specified record set.

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
| RecordID
| Record ID

|
| ErrorMessage
| Error or information message

### Return - Success

|
|

HTTP/1.1 200 OK

<RecordSetRecordsGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage i:nil="true" />

<RecordSetRecordsGetRows>

<RecordSetRecordsGetRow>

<RecordID>33343</RecordID>

</RecordSetRecordsGetRow>

<RecordSetRecordsGetRow>

<RecordID>33959</RecordID>

</RecordSetRecordsGetRow>

<RecordSetRecordsGetRow>

<RecordID>73953</RecordID>

</RecordSetRecordsGetRow>

<RecordSetRecordsGetRow>

<RecordID>132277</RecordID>

</RecordSetRecordsGetRow>

</RecordSetRecordsGetRows>

</RecordSetRecordsGetResult>

### Error Messages

|
Code
Description

|
| -8000
| Invalid PolarisUserID supplied

|
| -8001
| Polaris user is not permitted

|
| -9000
| Invalid WorkstationID supplied

|
| -11000
| Supplied RecordSetID is not of type patron

|
| -11001
| RecordSetID does not exist

|
| -11002
| Supplied RecordSetID is not of type bib, item, or patron

### Example

|
|

http://localhost:5000/protected/v1/1033/100/235/CxhtP0npwo6v7GsHnZ1svzaftKridynS/recordsets/540/records?userid=1&wsid=1&startIndex=0&numRecords=15

### Result - Success

|
|

HTTP/1.1 200 OK

<RecordSetRecordsGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance"><PAPIErrorCode>0</PAPIErrorCode><ErrorMessage i:nil="true" /><RecordSetRecordsGetRows>

<RecordSetRecordsGetRow>

<RecordID>86985</RecordID>

</RecordSetRecordsGetRow>

<RecordSetRecordsGetRow>

<RecordID>276575</RecordID>

</RecordSetRecordsGetRow>

<RecordSetRecordsGetRow>

<RecordID>276578</RecordID>

</RecordSetRecordsGetRow>

<RecordSetRecordsGetRow>

<RecordID>276579</RecordID>

</RecordSetRecordsGetRow>

<RecordSetRecordsGetRow>

<RecordID>276598</RecordID>

</RecordSetRecordsGetRow>

<RecordSetRecordsGetRow>

<RecordID>276599</RecordID>

</RecordSetRecordsGetRow>

</RecordSetRecordsGetRows>

</RecordSetRecordsGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0