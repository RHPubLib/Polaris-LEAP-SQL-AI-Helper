# Synch_GetDeletedAuthsPaged

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetDeletedAuthsPaged.htm_

You are here:

## Synch_GetDeletedAuthsPaged

This method returns a list of authority record IDs for records that have been deleted since a specified date and time. The paged method allows the retrieval of the ID list in smaller packets. If the library does not retain deleted records, you cannot use this method.

A date, last record ID, and number of records to return must be specified. When retrieving the first set of records, the "lastid" of 0 forces the process to start at the beginning of the list. Then, when retrieving subsequent records, the "lastid" is used as the starting ID for the next request.

Important: This method provides information for authority records that have been deleted in the Polaris ILS. This method has a date and time parameter. If the time element is not specified, midnight of the day specified is assumed. This method returns a generic AuthIDListGetResult XML structure (see below). A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/auths/deleted/paged?deletedate=1/1/
2017&lastid=0&nrecs=10
|  

### Authorization required?

Yes

### Protected method?

Yes

### Query String Parameters

|
|

Name

|

Value

|

Required

|

Description/Notes

|
|

deletedate

|

YYYY-MM-DDTHH:MM:SS

|

Yes

|

Start date and time (records that have been deleted since this date/time)

|
| lastid
| Use 0 when starting the retrieval process. Otherwise, use the last retrieved ID
| No
|  

|
| nrecs
| Number of records to return
| Yes
|  

### XML Elements Returned

|
|

Name

|

Description/Notes

|
|

PAPIErrorCode

|

PAPI Error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
|

ErrorMessage

| Error or information message

|
|

AuthIDListRows

|

List of item record IDs

|
|

AuthIDListRow

|

Container for data

|
|

AuthorityRecordID

|

The Authority Record ID

### Example

|
|

https://[HOSTNAME]/PAPISevice/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/auths/deleted/paged?deletedate=1/1/2017&lastid=0&nrecs=10

### Return

|
|

HTTP/1.1 200 OK

<AuthIDListGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<AuthIDListRows>

<AuthIDListRow>

<AuthorityRecordID>807343</AuthorityRecordID>

</AuthIDListRow>

</AuthIDListRows>

</AuthIDListGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0