# Synch_GetUpdatedItemsPaged

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetUpdatedItemsPaged.htm_

You are here:

## Synch_GetUpdatedItemsPaged

This method returns a list of item record IDs for records that have been added or updated since a specified date and time. The paged method allows the retrieval of the ID list in smaller packets.

A date, last record ID, and number of records to return must be specified. When retrieving the first set of records, the "lastid" of 0 forces the process to start at the beginning of the list. Then, when retrieving subsequent records, the "lastid" is used as the starting ID for the next request.

Important: This method provides information for item records that have a “final” status.

If the time element is not specified, the date and time parameter will assume midnight of the day specified.

This method returns a generic ItemIDListGetResult XML structure (see below).

A call to AuthenticateStaffUser is required before calling any protected methods.

The following events and actions will cause an item to appear in the list of updated items:

- Created via Acquisitions PO Line Item processing

- Created via Acquisitions Invoice processing

- Modified via PO Line Item Receive processing

- Modified via PO Line Item Segment Undo Receipt processing

- Created via Cataloging

- Modified via Item Bulk Change

- Modified via Cataloging

- Checked in

- Checked in (item was lost)

- Checked out

- Declared lost

- Claim was deleted

- Claim was made (returned or never had)

- Circulation status modified via Manage Item dialog from Check In

- Shelf location modified via Manage Item dialog from Check In

- Returned via ILL processing

- Sent in transit via Removing from Course Reserve

- Modified via PO Line Item Segment Receive processing

- Automatic status change from Check In

- Modified by automatic billed to lost processing

- Circulation status modified because item was held and request pickup branch was modified

- Circulation status modified to Routed by creation of linked route list piece

- Circulation status modified by modification of linked route list piece

- Modified via Floating Collections processing

- Renewal

- Transferred due to hold request

- Transferred due to ILL request

- Created via Acquisitions

- Created via Serials

- Marked for deletion

- Undeleted

- Barcode replaced via Check In

- Non public note modified via Manage Item dialog from Check In

- Free text block modified via Manage Item dialog from Check In

- Library assigned block modified via Manage Item dialog from Check In

- Assigned collection modified via Manage Item dialog from Check In

- Material type modified via Manage Item dialog from Check In

- Bulk checked out via Outreach Services

- Bulk checked out via Borrow by Mail

- Modified via Receive Shipment

- Linked to new bib

- Linked to new bib via Serials

- Due date reset

|
|  
| GET
| /protected/v1/1033/100/1/[token]/synch/items/updated/paged?updatedate=
6/5/2017&lastid=0&nrecs=10
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

updatedate

|

YYYY-MM-DDTHH:MM:SS

|

Yes

|

Start date for record updates

|
| lastid
| Use 0 when starting the retrieval process, otherwise, use the last retrieved ID
| No
|  

|
| nrecs
| Number of records to return
| No
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

The Item record ID

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/items/updated/paged?updatedate=6/5/2017&lastid=0&nrecs=10

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