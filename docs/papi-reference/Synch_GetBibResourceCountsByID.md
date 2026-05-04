# Synch_GetBibResourceCountsByID

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetBibResourceCountsByID.htm_

You are here:

## Synch_GetBibResourceCountsByID

A service will use this endpoint to retrieve the number of linked item record and local hold counts for multiple bibliographic record IDs in the Polaris database. This endpoint allows the consumer to provide up to 100 bibliographic record IDs at a time.

This method returns a list of resource count records related to the bibliographic record(s) requested by the user. The specific resource count records returned by this method may be queried using a single bibliographic record ID, a comma-delimited list of IDs, or by specifying a range.

For example:

- Individual bibliographic record query: ?bibids=243

- Comma-delimited query: ?bibids=243,253,657,2980,32,35

- Ranged query: ?bibids=243-280

**Important**

- No more than 100 compressed holdings records may be requested at a time.

- Bibliographic record IDs must be numeric.

- If a bibliographic record requested does not exist, a row is not returned.

- A call to AuthenticateStaffUser is required before calling any protected methods.

- Query types cannot be combined in a single query. An individual or comma-delimited query must be made separate from a ranged query.

|
|  
| GET
| /protected/.../[Access Token]/synch/bibs/resourcecounts?bibids=[bibids]
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
| bibids
| String
| Yes
|

Single bibliographic record ID, a comma-delimited list of IDs, or range of IDs.

Maximum number of provided IDs is 100.

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

GetBibResourceCountsByIDRows

|

List of GetBibResourceCountsByIDRow

|
|

GetBibResourceCountsByIDRow

|

Container for data

|
|

BibliographicRecordID

|

Bib record ID of the record

|
|

HoldRequestsCount

|

Number of local holds

|
| ItemRecordsCount
| Number of linked item records

### Example

|
|

http://localhost/PAPIService/REST/protected/v1/1033/100/3/HBxhW6u2IFgxj3hfxLCNEPyfckwxNwbk/synch/bibs/resourcecounts?bibids=7%2C55%2C80

### Return - Success

|
|

HTTP/1.1 200 OK

<GetBibResourceCountsByIDResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>3</PAPIErrorCode>

<ErrorMessage></ErrorMessage>

<GetBibResourceCountsByIDRows>

<GetBibResourceCountsByIDRow>

<BibliographicRecordID>7</BibliographicRecordID>

<HoldRequestsCount>5</HoldRequestsCount>

<ItemRecordsCount>4</ItemRecordsCount>

</GetBibResourceCountsByIDRow>

<GetBibResourceCountsByIDRow>

<BibliographicRecordID>55</BibliographicRecordID>

<HoldRequestsCount>0</HoldRequestsCount>

<ItemRecordsCount>34</ItemRecordsCount>

</GetBibResourceCountsByIDRow>

<GetBibResourceCountsByIDRow>

<BibliographicRecordID>80</BibliographicRecordID>

<HoldRequestsCount>0</HoldRequestsCount>

<ItemRecordsCount>1</ItemRecordsCount>

</GetBibResourceCountsByIDRow>

</GetBibResourceCountsByIDRows>

</GetBibResourceCountsByIDResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0