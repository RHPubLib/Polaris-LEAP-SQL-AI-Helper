# Synch_ItemsByBibIDGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_ItemsByBibIDGet.htm_

You are here:

## Synch_ItemsByBibIDGet

This method will return all item records attached to a particular bib as requested by the user. The items may be specified by bibliographic record ID. Use the "excludeecontent" parameter to choose if econtent is excluded from the result set.

Important: Only one bibliographic record may be requested at a time. Bibliographic record IDs must be numeric. If the bibliographic record requested does not exist, a row will not be returned.

This method is not appropriate for gathering holdings during the context of a catalog search by a library customer; it is meant to be used only during a synchronization process. To get holdings during a search use the public BibHoldingsGet method. See "BibHoldingsGet" on page 1

A call to AuthenticateStaffUser is required before calling any protected methods."BibHoldingsGet" on page 1

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/items/bibid/{BibID}?excludeecontent=false
|  

### Authorization required?

Yes

### Protected method?

Yes

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
|

BibID

|

Yes

|

The bibliographic record identifier.

### Query String Parameters

|
| Name
|

Value

Required
|

Description/Notes

|
|

excludeecontent

|

true/false

| No
|

To exclude econtent records from the result set. Default: false

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

|

Error or information message

|
|

ItemGetRows

|

List of item data

|
|

ItemGetRow

|

Container for data

|
|

LocationID

|

Location identifier to which this piece is assigned.

|
|

LocationName

|

Location name to which this piece is assigned.

|
|

CollectionID

|

Collection identifier to which this piece is assigned.

|
|

CollectionName

|

Collection name to which this piece is assigned.

|
|

Barcode

|

Barcode assigned to the piece.

|
|

PublicNote

|

Public note of the piece.

|
|

CallNumber

|

Local call number of the piece. Includes VolumeNumber if exists.

|
|

Designation

|

Designation assigned to the piece. If the piece is not associated with serial then this value will be NULL.

|
|

VolumeNumber

|

Volume number assigned to the piece.

|
|

ShelfLocation

|

Shelf location assigned to the piece.

|
|

CircStatus

|

Circulation status of the piece.

|
|

LastCircDate

|

Last circulation date of the piece.

|
|

MaterialType

|

Material type of the piece.

|
|

TextualHoldingsNote

|

Textual holdings note associated with the assigned location/collection.

|
|

RetentionStatement

|

Retention statement associated with the assigned location.

|
|

HoldingsStatement

|

Holdings statement associated with the assigned location.

|
|

HoldingsNote

|

Holdings note associated with the assigned location.

|
|

Holdable

|

Specifies whether a hold can be placed on the piece.

|
|

DueDate

|

Specifies when the item is due back to the library.

|
|

ItemRecordID

|

The items record ID

|
|

BibliographicRecordID

|

The bibliographic record ID to which the item is attached

|
|

IsDisplayInPAC

|

Boolean true or false. Indicates if the library wishes the record to display in PAC.

|
|

CreationDate

|

The date and time that the record was created in the system.

|
|

FirstAvailableDate

|

The first available date for the bib is the first day the first item linked to the bib becomes available for circulation. This data may be NULL.

|
|

ModificationDate

|

The date and time of last record modification. This data may be NULL.

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/items/bibid/1

### Return

|
|

HTTP/1.1 200 OK

<ItemGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<ItemGetRows>

<ItemGetRow>

<LocationID>97</LocationID>

<LocationName>Scotia Branch - Schenectady County Public Library</LocationName>

<CollectionID>0</CollectionID>

<CollectionName/><Barcode>0000408366227</Barcode>

<PublicNote/>

<CallNumber>Fict Hel</CallNumber>

<Designation/>

<VolumeNumber/>

<ShelfLocation/>

<CircStatus>In</CircStatus>

<LastCircDate>Apr 27 2007 </LastCircDate>

<MaterialType>Book</MaterialType>

<TextualHoldingsNote/>

<RetentionStatement/>

<HoldingsStatement/>

<HoldingsNote/>

<Holdable>true</Holdable>

<DueDate/>

<ItemRecordID>572680</ItemRecordID>

<BibliographicRecordID>1</BibliographicRecordID>

<IsDisplayInPAC>true</IsDisplayInPAC>

<CreationDate>2009-07-28T11:57:09.347</CreationDate>

<FirstAvailableDate>2009-07-28T11:57:09.347</FirstAvailableDate>

<ModificationDate>2009-07-28T11:57:09.347</ModificationDate>

</ItemGetRow>

</ItemGetRows>

</ItemGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0