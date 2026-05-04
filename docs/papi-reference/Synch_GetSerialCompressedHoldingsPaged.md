# Synch_GetSerialCompressedHoldingsPaged

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetSerialCompressedHoldingsPaged.htm_

You are here:

## Synch_GetSerialCompressedHoldingsPaged

This method returns a list of serial compressed holdings statements using a paging mechanism. The specific records returned are in order of organization ID and bibliographic record ID starting with the IDs after the **lastorgid** and **lastbibid** parameters. The number of records returned is specified by the **nrecs** parameter. By default, this method will return branch level serial compressed holdings statements.

To retrieve the set of system level serial compressed holdings statements, provide a value of "true" for the **systemlevel** query string parameter.

To retrieve the set of branch level serial compressed holdings statements that have been modified since a specified date, use the **startdatemodified** query string parameter.

**Important**

- No more than 100 compressed holdings records may be requested at a time.

- Organization and bibliographic record IDs specified must be numeric.

- When specifying a date, the yyyy-MM-dd HH:mm:ss.fff format may be used.

Example URL to start the paging of branch level serial compressed holdings:

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch//serialholdings/textual/compressed/paged?lastorgid=0&lastbibid=0&nrecs=0&systemlevel=false
|

 

 

Example URL to start the paging of system-level serial compressed holdings:

|
|  
| GET
| /protected/1/{AccessToken}/synch/serialholdings/textual/compressed/paged?lastbibid=0&nrecs=0&systemlevel=true

|  

Example URL to start the paging of modified branch level serial compressed holdings:

|
|  
| GET
| /protected/1/{AccessToken}/synch/serialholdings//textual/compressed/paged?lastbibid=0&systemlevel=false&startdatemodified=2020-12-03%2000%3A00%3A00.000

|  

### Authorization required?

Yes

### Protected method?

Yes

### Query String Parameters

|
|

Name

Value
|

Required

|

Description/Notes

|
|

lastorgid

| Use 0 when starting the retrieval process,
otherwise, use the last retrieved org ID
|

Yes, when paging

non-system level

|

The highest organization ID of the last page of records retrieved. This allows for the current page of record returned to follow sequentially from the previous page retrieved. This value is ignored when systemlevel is set to 1.

Default is 0.

|
| lastbibid
| Use 0 when starting the retrieval process,
otherwise, use the last retrieved bib ID
| Yes, when paging.
|

The highest Bibliographic ID of the last "page" of
records retrieved. This allows for the current page of records
returned to follow sequentially from the previous page retrieved.

Default is 0.

|
| nrecs
| integer
| No
|

Number of record to retrieve

Default is 100.

|
| startdatemodified
| date
| Yes, when retrieving
system level statements.
| Default is false.

|
| systemlevel
| boolean
| Yes, when retrieving
system level statements.
| Default is false.

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

GetSerialCompressedHoldingsRows

|

List of GetSerialCompressedHoldingsRow

|
|

GetSerialCompressedHoldingsRow

|

Container for data

|
| OrganizationID
| The organization ID

|
|

BibliographicRecordID

|

Bib record ID of the record

|
|

CompressedStatement

|

The compressed holdings statement

|
| PublicNotes
| Array of public notes. Not returned at the system level.

|
| RetentionNote
| Retention note

|
| LastReceivedIssue
| Last received issue

|
| CreationDate
| Creation date of compressed holding

|
| ModificationDate
| Modification date of compressed holding

### Example

|
|

http://localhost/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPGsy1tlZPr /synch/serialholdings/textual/compressed/paged?systemlevel=true&lastbibid=0&nrecs=2

### Return - Success

|
|

HTTP/1.1 200 OK

<GetSerialCompressedHoldingsPagedResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>2</PAPIErrorCode>

<ErrorMessage></ErrorMessage>

<LastOrganizationID>1</LastOrganizationID>

<LastBibliographicRecordID>779322</LastBibliographicRecordID>

<GetSerialCompressedHoldingsRows>

<GetSerialCompressedHoldingsRow>

<OrganizationID>1</OrganizationID>

<BibliographicRecordID>685288</BibliographicRecordID>

<CompressedStatement>v. 41 no. 1 (Feb. 2003)-v. 48 no. 1 (Feb. 2010)</CompressedStatement>

<PublicNotes />

<RetentionNote i:nil="true" />

<LastReceivedIssue>v. 48 no. 1 (Feb. 2010)</LastReceivedIssue>

<CreationDate>2020-11-09T12:55:21.12</CreationDate>

<ModificationDate>2020-11-12T14:54:30.023</ModificationDate>

</GetSerialCompressedHoldingsRow>

<GetSerialCompressedHoldingsRow>

<OrganizationID>1</OrganizationID>

<BibliographicRecordID>779322</BibliographicRecordID>

<CompressedStatement>Issue 1 (2006)-year 2 (2009)</CompressedStatement>

<PublicNotes>

<PublicNote>

<Value>Public Note 1</Value>

<DisplayOrder>1</DisplayOrder>

</PublicNote>

<PublicNote>

<Value>Note 2</Value>

<DisplayOrder>2</DisplayOrder>

</PublicNote>

</PublicNotes>

<RetentionNote>Permanently retained</RetentionNote>

<LastReceivedIssue>year 2 (2009)</LastReceivedIssue>

<CreationDate>2020-11-09T12:55:21.12</CreationDate>

<ModificationDate>2020-11-12T14:54:30.023</ModificationDate>

</GetSerialCompressedHoldingsRow>

</GetSerialCompressedHoldingsRows>

</GetSerialCompressedHoldingsPagedResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0