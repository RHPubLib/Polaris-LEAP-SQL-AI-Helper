# Synch_GetDeletedItems

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetDeletedItems.htm_

You are here:

## Synch_GetDeletedItems

This method returns a list of item record IDs for records that have been deleted since a specified date and time. If the library does not retain deleted records, you cannot use this method.

**Important: **This method provides a list of item records that have been deleted in the Polaris ILS. The method has a date and time parameter. If the time element is not specified, midnight of the day specified is assumed.This method returns a generic ItemIDListGetResult XML structure (see below). A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/items/deleted?deletedate={deletedate}
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

List of Item record IDs

|
|

ItemIDListRow

|

Container for data

|
|

ItemRecordID

|

The Item Record ID

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZ
uJYREw6TQHPGsy1tlZPr/synch/items/deleted?deletedate=12/2/2011 13:00:00

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