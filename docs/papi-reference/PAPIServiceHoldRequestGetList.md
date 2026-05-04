# HoldRequestGetList

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceHoldRequestGetList.htm_

You are here:

## HoldRequestGetList

This protected method will return a list of hold requests that match the criteria specified by the user. The data returned includes the detailed request, patron, item, and title information. This method optionally allows a user to set an expiration date and time for the items on the list, which prevents duplicates of items already returned on previous calls to this method.

**Important:** A call to AuthenticateStaffUser is required before calling any protected method.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/circulation/requests/list?branch={branch_id}&branchtype={branch_type_id}&requeststatus={status_id}
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

branchtype

|

Yes

|

The type of branch specified. Valid values include:

1=patron’s branch
2=pickup branch
3=item (fulfilling) branch

|
|

requeststatus

|

Yes

|

The desired status of requests returned

|
|

expirationdate

|

No

|

The date and time to expire the list

|
|

useexpirationdate

|

No

|

Indicates if an expiration date filer of the list is desired for the call

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

PickListCreateTime

|

The date and time the list was created

|
|

PickListExpirationTime

|

The expiration time of the list specified by the user

|
|

RequestsPicklistRows

|

A list of request data

|
|

SysHoldRequestID

|

The Polaris unique request ID

|
|

SysHoldStatusID

|

The request status ID

|
|

HoldStatus

|

The request status description

|
|

PickupBranchID

|

The pickup branch ID of the request

|
|

PickupBranch

|

A description of the pickup branch

|
|

ActivationDate

|

The date the request became active

|
|

ExpirationDate

|

The expiration date and time of the request

|
|

StatusDate

|

The date and time the request last changed

|
|

BibliographicRecordID

|

The bibliographic record ID to which the request is attached

|
| ConstituentBibRecordID
| The bibliographic record that is tied to this hold request has another bibliographic record associated with it. The most common use of this is different titles that are "bound together." This is the ID of the associated bibliographic record.

|
|

BrowseAuthor

|

The primary author of the work (if any)

|
|

BrowseTitle

|

The title of the work

|
|

PrimaryMARCTOMID

|

The Polaris primary MARC type of material ID

|
|

MarcTypeOfMaterial

|

The Polaris MARC type of material description

|
|

ItemLevelHold

|

Boolean value indicating if the request was placed for a specific item.

|
|

BorrowByMail

|

Boolean value indicating if the request was borrow by mail.

|
|

PatronID

|

The unique ID of the patron who placed the request.

|
|

PatronBarcode

|

The patron’s barcode.

|
|

PatronBranchID

|

The patron’s branch ID.

|
|

PatronBranch

|

The patron’s branch description.

|
|

PatronFullName

|

The full name of the patron who placed the request.

|
|

PatronCodeID

|

The patron’s Patron Code ID.

|
|

PatronCode

|

The patron’s Patron Code description.

|
|

Email address

|

The patron’s email address (if any)

|
|

AltEmailAddress

|

The patron’s alternate email address (if any)

|
|

PhoneVoice1

|

The patron’s primary phone number (if any)

|
|

SMSAddress

|

The patron’s SMS text message (if any)

|
|

ItemRecordID

|

The Polaris item record ID to which the request is bound (if any)

|
|

ItemBarcode

|

The barcode of the item to which the request is bound (if any)

|
|

ItemBranchID

|

The assigned branch ID for the item to which the request is bound (if any)

|
|

ItemBranch

|

The assigned branch description for the item to which the request is bound (if any)

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

|
|

Pages

|

The number of pages for the request (if any)

|
|

AssignedCollectionID

|

The item’s assigned collection ID (if any)

|
|

CollectionName

|

The item’s assigned collection description (if any)

|
|

MaterialTypeID

|

The item’s material type ID(if any)

|
|

MaterialType

|

The item’s material type description (if any)

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

PublicationYear

|

The year the work was published

|
|

Publisher

|

The publisher of the work

|
|

Designation

|

The item’s serial designation (if any)

|
|

Edition

|

The edition of the work (if any)

|
|

StaffDisplayNotes

|

The request’s staff note (if any)

|
|

NonPublicNotes

|

The request’s non-public note (if any)

|
|

PACDisplayNotes

|

The request’s public note (if any)

|
|

SortTitle

|

The NACO normalized title of the work (if any). Appropriate for sorting the list.

|
|

SortAuthor

|

The NACO normalized author of the work (if any). Appropriate for sorting the list.

### Example

|
| https://egraham-r2vm.gisinfosystems.com/Plato-R2PAPIService/REST/protected/v1/1033/
100/1/DEsGANrOPNYpnKyaYKJ6fQtg0fKsIonE/circulation/requests/list?branch=17&branchtype
=2&requeststatus=4

### Return

|
|

HTTP/1.1 200 OK

<RequestsPicklistGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<RecordCount>1</RecordCount>

<PickListCreateTime>2013-08-14T12:53:05.0172244-04:00</PickListCreateTime>

<PickListExpirationTime>0001-01-01T00:00:00</PickListExpirationTime>

<RequestsPicklistRows>

<RequestsPicklistGetRow>

<SysHoldRequestID>811071</SysHoldRequestID>

<SysHoldStatusID>4</SysHoldStatusID>

<HoldStatus>Pending</HoldStatus>

<PickupBranchID>17</PickupBranchID>

<PickupBranch>Cambridge Public Library</PickupBranch>

<ActivationDate>2013-07-08T00:00:00</ActivationDate>

<ExpirationDate>2013-10-06T23:59:59</ExpirationDate>

<StatusDate>2013-07-08T17:18:07.22</StatusDate>

<BibliographicRecordID>23792</BibliographicRecordID>

<BrowseAuthor>Bix, Cynthia Overbeck.</BrowseAuthor>

<BrowseTitle>Cats</BrowseTitle>

<PrimaryMARCTOMID>1</PrimaryMARCTOMID>

<MarcTypeOfMaterial>Book</MarcTypeOfMaterial>

<ItemLevelHold>false</ItemLevelHold>

<BorrowByMail>false</BorrowByMail>

<PatronID>52324</PatronID>

<PatronBarcode>1000500534226</PatronBarcode>

<PatronBranchID>29</PatronBranchID>

<PatronBranch>Crandall Public Library (Glens Falls)</PatronBranch>

<PatronFullName>Batson, Billy</PatronFullName>

<PatronCodeID>1</PatronCodeID>

<PatronCode>Regular</PatronCode>

<EmailAddress/>

<AltEmailAddress/>

<PhoneVoice1>315-555-1234</PhoneVoice1>

<SMSAddress>3156341234@example.net</SMSAddress>

<ItemRecordID>102167</ItemRecordID>

<ItemBarcode>0000201430097</ItemBarcode>

<ItemBranchID>90</ItemBranchID>

<ItemBranch>Saratoga Springs Public Library</ItemBranch>

<CallNumber>J 636.8 Ove</CallNumber>

<CopyNumber/>

<VolumeNumber/>

<Pages/>

<AssignedCollectionID>32</AssignedCollectionID>

<CollectionName>Children's Nonfiction</CollectionName>

<MaterialTypeID>1</MaterialTypeID>

<MaterialType>Book</MaterialType>

<ShelfLocationID/>

<ShelfLocation/>

<PublicationYear>1983</PublicationYear>

<Publisher>Lerner Publications Co.,</Publisher>

<Designation/>

<Edition/>

<StaffDisplayNotes/>

<NonPublicNotes/>

<PACDisplayNotes/>

<SortTitle>CATS</SortTitle>

<SortAuthor>BIX CYNTHIA OVERBECK</SortAuthor>

</RequestsPicklistGetRow>

</RequestsPicklistRows>

</RequestsPicklistGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0