# Synch_GetMaxItemID

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetMaxItemID.htm_

You are here:

## Synch_GetMaxItemID

This method returns the maximum item record ID.

**Important: **This method provides information for item records that have a “final” status and are attached to a bibliographic record that has a status of final. It returns a generic ItemIDListGetResult XML structure (see below). A call to AuthenticateStaffUser is required before calling any protected method.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/items/maxid
|  

### Authorization required?

Yes

### Protected method?

Yes

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

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/items/maxid

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