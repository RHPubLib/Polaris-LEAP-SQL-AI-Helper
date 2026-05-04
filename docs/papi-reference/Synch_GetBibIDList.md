# Synch_GetBibIDList

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetBibIDList.htm_

You are here:

## Synch_GetBibIDList

This method gets a list of bibliographic record IDs from a specified record ID. An optional parameter is available to allow the user to specify the number of record IDs to retrieve. A maximum 1,000 record IDs are returned for each call to this method.

**Important:** This method provides information for bibliographic records that have a “final” status.

An optional parameter “nrecs” may be specified. The parameter allows the user to return a particular number of records. This method returns a generic BibIDListGetResult XML structure (see below).

A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/bibs/idlist?startid={startid}&nrecs={numberofrecords}
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

integer

|

Yes

|

Starting record ID

|
|

numberofrecords

|

integer

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

BibIDListRows

|

List of bibliographic record IDs

|
|

BibIDListRow

|

Container for data

|
|

BibliographicRecordID

|

The Bibliographic Record ID

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQ
HPGsy1tlZPr/synch/bibs/idlist?startid=60000

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQ
HPGsy1tlZPr/synch/bibs/idlist?startid=60000&nrecs=150

### Return

|
|

HTTP/1.1 200 OK

<BibIDListGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<BibIDListRows>

<BibIDListRow>

<BibliographicRecordID>600000</BibliographicRecordID>

</BibIDListRow>

</BibIDListRows>

</BibIDListGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0