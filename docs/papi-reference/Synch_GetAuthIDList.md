# Synch_GetAuthIDList

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetAuthIDList.htm_

You are here:

## Synch_GetAuthIDList

This method gets a list of authority record IDs from a specified record ID. An optional parameter is available to allow the user to specify the number of record IDs to retrieve. A maximum 1,000 record IDs are returned for each call to this method.

**Important: **This method provides information for item records that have a “final” status and are set to display in PAC. The items must be attached to a bibliographic record that has a status of final and displays in PAC. An optional parameter “nrecs” may be specified. The parameter allows the user to return a particular number of records. This method returns a generic AuthIDListGetResult XML structure (see below). A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/auths/idlist?startid={startid}&nrecs={numberofrecords}
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

startid

|

Integer

|

Yes

|

Starting record ID

|
|

numberofrecords

|

Integer

|

No

|

Number of record IDs to retrieve

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

The authority Record ID

### Examples

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/auths/idlist?startid=60000

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/auths/idlist?startid=60000&nrecs=150

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