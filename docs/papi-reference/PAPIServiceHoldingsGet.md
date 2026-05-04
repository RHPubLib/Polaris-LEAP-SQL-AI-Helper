# BibHoldingsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceHoldingsGet.htm_

You are here:

## BibHoldingsGet

Returns holdings information for a specified bibliographic record.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/bib/{BibID}/holdings
|  

### Authorization required?

Yes, if authentication level set to ALL.

### Input Parameters

|
|

Name

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

Is the record identifier.

### XML Elements Returned

The result XML contains one node (BibHoldingsGetRow) for each piece (monograph or serial). The nodes are ordered such that all pieces assigned to a given location/collection are grouped together based on the item availability display configuration settings in Polaris System Administration. For a given location and collection, monographic pieces are always sorted before serial pieces. Monographic pieces are sorted by call number and volume (normalized) in ascending order, and serial pieces are sorted by chronology date in descending order.

|
| Name
|

Description/Notes

|
| PAPIErrorCode
|

PAPI Error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

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

Barcode assigned to the piece. If the piece is not associated with an item record then this value will be NULL.

|
|

PublicNote

|

Public note of the piece.

|
|

CallNumber

|

Local call number of the piece.

|
|

Designation

|

Designation assigned to the piece. If the piece is not associated with serial then this value will be NULL.

|
|

ShelfLocation

|

Shelf location assigned to the piece.

|
|

CircStatus

|

Circulation status of the piece. If the piece is checked out then the due date will be appended to the circulation status. Other factors used to determinate the circulation status are outside the scope of this document.

|
|

LastCircDate

|

Last circulation date of the piece. If the piece is not associated with an item record then this value will be NULL.

|
|

MaterialType

|

Material type of the piece. If the piece is not associated with an item record then this value will be NULL.

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

ItemsTotal

|

Total number of pieces associated with the assigned location.

|
|

ItemsIn

|

Number of pieces associated with the assigned location and available for check-out.

|
|

Holdable

|

Specifies whether a hold can be placed on the piece.

|
| VolumeNumber
| Volume number assigned to the piece.

|
|

DueDate

|

Specifies when the item is due back to the library.

|
| IsMaterialTypeChargeable
| Indicates whether the patron is charged for placing a hold request on this type of item.

|
| IsElecronicItem
| Indicates whether this type of item is an electronic resource (e-book).

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/bib/5000/holdings

### Return - Success

|
|

HTTP/1.1 200 OK

<BibHoldingsGetResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<BibHoldingsGetRows>

<BibHoldingsGetRow>

<LocationID>3</LocationID>

<LocationName>Amsterdam Free Library</LocationName>

<CollectionID>25</CollectionID>

<CollectionName>Children's Fiction</CollectionName>

<Barcode>0004300063676</Barcode>

<PublicNote/><CallNumber>j Fict Gra</CallNumber>

<Designation/>

<ShelfLocation/>

<CircStatus>In</CircStatus>

<LastCircDate>Sep 5 2006</LastCircDate>

<MaterialType>Book</MaterialType>

<TextualHoldingsNote/>

<RetentionStatement/>

<HoldingsStatement/>

<HoldingsNote/>

<ItemsTotal>1</ItemsTotal>

<ItemsIn>1</ItemsIn>

<Holdable>true</Holdable>

</BibHoldingsGetRow>

...

<BibHoldingsGetRow>

<LocationID>25</LocationID>

<LocationName>Community Librar(Cobleskill)</LocationName>

<CollectionID>25</CollectionID>

<CollectionName>Children's Fiction</CollectionName>

<Barcode>0001900057256</Barcode>

<PublicNote/>

<CallNumber>j Fict Gra</CallNumber>

<Designation/>

<ShelfLocation/>

<CircStatus>Lost</CircStatus>

<LastCircDate>Jan 17 2006</LastCircDate>

<MaterialType>Book</MaterialType>

<TextualHoldingsNote/>

<RetentionStatement/>

<HoldingsStatement/>

<HoldingsNote/>

<ItemsTotal>1</ItemsTotal>

<ItemsIn>0</ItemsIn>

<Holdable>true</Holdable>

</BibHoldingsGetRow>

</BibHoldingsGetRows>

</BibHoldingsGetResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<BibHoldingsGetResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid BibID</ErrorMessage>

<BibHoldingsGetRows i:nil="true"/></BibHoldingsGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0