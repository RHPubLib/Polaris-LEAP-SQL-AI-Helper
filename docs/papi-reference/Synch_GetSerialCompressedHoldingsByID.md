# Synch_GetSerialCompressedHoldingsByID

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetSerialCompressedHoldingsByID.htm_

You are here:

## Synch_GetSerialCompressedHoldingsByID

This method provides compressed serial holdings data based on a list of one or more bibliographic record and branch ID pairs. Data returned contains the compressed holdings statement, location, and last received issue.

A service may use this endpoint to retrieve compressed holdings in the Polaris database. This endpoint allows retrieval of specific holdings based on a list of IDs. The specific serial compressed holdings records returned by this method may be queried using a single organization ID and bibliographic record ID pair or a comma-delimited list of ID pairs. For example:

- Individual bibliographic record query: ?ids=3:243

- Comma-delimited query: ?ids=3:243,5:1009,5:2873

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/serialholdings/textual/compressed?ids=[IDList]
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

ids

| orgid:bibid
|

Yes

|

Comma delimited list of ID pairs representing compressed holdings to return

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

Bibliographic record ID of the record

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

http://localhost/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPGsy1tlZPr/synch/serialholdings/textual/compressed?ids=3:174328

### Return - Success

|
|

HTTP/1.1 200 OK

<GetSerialCompressedHoldingsByIDResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>1</PAPIErrorCode>

<ErrorMessage></ErrorMessage>

<GetSerialCompressedHoldingsRows>

<GetSerialCompressedHoldingsRow>

<OrganizationID>3</OrganizationID>

<BibliographicRecordID>174328</BibliographicRecordID>

<CompressedStatement i:nil="true" />

<PublicNotes>

<PublicNote>

<Value> 1</Value>

<DisplayOrder>1</DisplayOrder>

</PublicNote>

</PublicNotes>

<RetentionNote i:nil="true" />

<LastReceivedIssue i:nil="true" />

<CreationDate>2020-11-09T12:55:21.12</CreationDate>

<ModificationDate>2020-11-16T23:00:27.773</ModificationDate>

</GetSerialCompressedHoldingsRow>

</GetSerialCompressedHoldingsRows>

</GetSerialCompressedHoldingsByIDResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0