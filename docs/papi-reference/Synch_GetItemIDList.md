# Synch_GetItemIDList

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetItemIDList.htm_

You are here:

## Synch_GetItemIDList

This method gets a list of item record IDs from a specified record ID. An optional parameter is available to allow the user to specify the number of record IDs to retrieve. A maximum 1,000 record IDs are returned for each call to this method.

**Important:** This method provides information for item records that have a “final” status and are attached to a bibliographic record that has a status of final. An optional parameter “nrecs” may be specified. The parameter allows the user to return a particular number of records. This method returns a generic ItemIDListGetResult XML structure (see below). A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/items/idlist?startid={startid}&nrecs={numberofrecords}
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

ItemIDListRows

|

List of item record IDs

|
|

ItemIDListRow

|

Container for data

|
|

ItemRecordID

|

The item record ID

### Examples

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/items/idlist?startid=60000

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/items/idlist?startid=60000&nrecs=150

### Return

|
|

HTTP/1.1 200 OK

<ItemIDListGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode><ErrorMessage/>

<ItemIDListRows>

<ItemIDListRow>

<ItemRecordID>9367071</ItemRecordID>

</ItemIDListRow>

</ItemIDListRows>

</ItemIDListGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0