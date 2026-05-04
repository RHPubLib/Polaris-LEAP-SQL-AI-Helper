# Synch_GetUpdatedItems

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetUpdatedItems.htm_

You are here:

## Synch_GetUpdatedItems

This method returns a list of item record IDs for records that have been added or updated since a specified date and time.

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
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/items/updated?updatedate={updatedate
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
|

enddate

|

YYYY-MM-DDTHH:MM:SS

|

No

|

End date for record updates. Limits data set returned to mitigate performance and retrieval issues. If not used, thecurrent date and time are used.

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
sy1tlZPr/synch/items/updated?updatedate=12/2/2011 13:00:00

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