# RecordSetContentPut

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceRecordSetContentPut.htm_

You are here:

## RecordSetContentPut

This method adds or removes records from a bibliographic, item, or patron record set.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/recordsets/{RecordSetID}?userid={userid}&wsid={workstation_id}&action=add
|  

|
|  
| PUT
| /protected/1/{AccessToken}/recordsets/{RecordSetID}?userid={userid}&wsid={workstation_id}&action=remove
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
| userid
| Yes
| Staff user ID

|
| wsid
| Yes
| Workstation ID

|
| action
| Yes
| Options: **add** or **remove**

### XML Body Elements

**Important:** XML elements must be in the order shown below.

|
|

Name

|

Required

|

Description/Notes

|
| Records
| Yes
| A comma separated list of internal bibliographic, item, or patron IDs that should be added or removed from a record set.

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

http://localhost:5000/protected/v1/1033/100/235/CxhtP0npwo6v7GsHnZ1svzaftKridynS/recordsets/1884?userid=1&wsid=1&action=add

http://localhost:5000/protected/v1/1033/100/235/CxhtP0npwo6v7GsHnZ1svzaftKridynS/recordsets/1884?userid=1&wsid=1&action=remove

Request Body

<ModifyRecordSetContent>

<Records>356950,357374</Records>

</ModifyRecordSetContent>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0