# RemoteStorageItemsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceRemoteStorageItemsGet.htm_

You are here:

## RemoteStorageItemsGet

This protected method returns a list of items that match the criteria specified by the user. The data returned includes the detailed item information designed to update remote storage repositories for new, updated, and deleted items. The list may be paged using the **startitemrecordid **parameter.

**Important:** A call to AuthenticateStaffUser is required before calling any protected method.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/cataloging/remotestorage/items?branch=
{branch_id}&startdate={start_date}&enddate={end_date}&maxitems=
{max_items}&listtype={list_type}
|  

### Authorization required?

Yes

### Protected method?

Yes

### Query String Parameters

|
| Name
|

Required

|

Description/Notes

|
|

branch

|

Yes

|

The branch ID for the request list

|
|

startdate

|

Yes

|

The starting date for the delta

|
|

enddate

|

Yes

|

The ending date for the delta

|
|

maxitems

|

Yes

|

The number of items returned for the call

|
|

listtype

|

Yes

|

The list type:

1= newly created items
2= items that were modified
3= items that were deleted

|
|

startitemrecordid

|

No

|

The item record ID after which to start the list

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

RecordCount

|

The total number of records found that met the search criteria

|
|

RowCount

|

The number of items returned in the current result set

|
|

RemoteStorageItemsGetRows

|

A list of item data

|
|

RemoteStorageItemsGetRow

|

Container for the data row

|
|

ItemRecordID

|

The Polaris item record ID

|
|

BibliographicRecordID

|

The bibliographic record ID with which the item is associated

|
|

Barcode

|

The barcode of the item to which the request is bound (if any)

|
|

BrowseTitle

|

The title of the work

|
|

BrowseAuthor

|

The primary author of the work (if any)

|
|

MaterialTypeID

|

The item’s material type ID

|
|

MaterialType

|

The item’s material type description

|
|

CollectionID

|

The item’s collection ID (if any)

|
|

Collection

|

The item’s collection description (if any)

|
|

ShelfLocationID

|

The item’s shelf location ID (if any)

|
|

ShelfLocation

|

The item’s shelf location description (if any)

|
|

CallNumber

|

The item’s call number (if any)

|
|

CopyNumber

|

The item’s copy number (if any)

|
|

VolumeNumber

|

The item’s volume number (if any)

### Example

|
|

HTTP/1.1 200 OK

https://egraham-r2vm.gisinfosystems.com/Plato-R2PAPIService/REST/protected/v1/1033/
100/1/DEsGANrOPNYpnKyaYKJ6fQtg0fKsIonE/cataloging/remotestorage/items?branch=92&startdate=8-1-2013&enddate=8-24-2013&maxitems=100&listtype=1

### Body

N/A

### Return

|
|

<RecordCount>1</RecordCount>

<RowCount>1</RowCount>

<RemoteStorageItemsGetRows>

<RemoteStoragesItemsGettRow>

<ItemRecordID>9942528</ItemRecordID>

<BibliographicRecordID>8577</BibliographicRecordID>

<Barcode>0003658451</Barcode>

<BrowseTitle>Salted lemons</BrowseTitle>

<BrowseAuthor>Smith, Doris Buchanan.</BrowseAuthor>

<MaterialTypeID>1</MaterialTypeID>

<MaterialType>Book</MaterialType>

<CollectionID>87</CollectionID>

<Collection>Reference</Collection>

<ShelfLocationID/>

<ShelfLocation/>

<CallNumber>R</CallNumber>

<CopyNumber/>

<VolumeNumber/>

</RemoteStoragesItemsGettRow>

</RemoteStorageItemsGetRows>undefined</RemoteStoragesItemsGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0