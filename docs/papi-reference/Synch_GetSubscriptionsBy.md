# Synch_GetSubscriptionsByID

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetSubscriptionsBy.htm_

You are here:

## Synch_GetSubscriptionsByID

This method returns a list of serial bibliographic record IDs and an XML representation of the serials subscription information associated with the bibliographic record(s) requested by the user. The information returned by this method may be specified using a comma delimited list of bibliographic record IDs. Data returned may include SHR (Serial Holdings Record) Copy information, Compressed Holdings information, SHR Copy shared public notes, Publication Pattern information, textual holdings information, and Issue/Linked Item information. A third-party discovery interface may use this method to return data when a user clicks a Subscription Information button in the discovery interface.

**Important: **No more than 50 bibliographic records may be requested at a time. Bibliographic record IDs must be numeric. If a bibliographic record requested does not exist, a row will not be returned. If serials subscription information does not exist for the record, serials information will not be returned by this method.

A call to AuthenticateStaffUser (see AuthenticateStaffUser) is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/subscriptions/SubscriptionXML?
bibids={BibIDList}
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

Required

|

Description/Notes

|
|

BibIDList

|

Yes

|

Comma separated list of bibliographic record IDs for which to return subscription information.

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

GetSubscriptionsByIDRows

|

List of bibliographic record IDs and Subscription XML records

|
|

GetSubscriptionsByIDRow

|

Container for data

|
|

BibliographicRecordID

|

Bib record ID of the record

|
|

SubscriptionXMLRecord

|

An HTML Encoded representation subscription XML Data. **Important:** The character coding scheme is Unicode.

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/subscriptions/SubscriptionXML?bibids=1,5,7,9,11

### Return

|
|

HTTP/1.1 200 OK

<GetSubscriptionsByIDResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<GetSubscriptionsByIDRows>

<GetSubscriptionsByIDRow>

<BibliographicRecordID>597046</BibliographicRecordID>

<SubscriptionXMLRecord>

<Record>

<BibliographicRecordID>597046</BibliographicRecordID>

<CopyRecords>

<CopyRecord>

<CopyID>33</CopyID>

<CollectionID>75</CollectionID>

<CollectionName>Magazines</CollectionName>

<CompletenessCode>Incomplete</CompletenessCode>

<OrganizationID>101</OrganizationID>

<OrganizationName>Southern Adirondack Library System</OrganizationName>

<CopyNumber>1</CopyNumber>

<DisplayInPAC>1</DisplayInPAC>

<RetentionDescription>Other general retention policy</RetentionDescription>

<HoldingsStatement/>

<HoldingsNote/>

<RetentionNote/>

<Notes>

<Note>

<Ordinal>1</Ordinal>

<PublicNote>This is a serials holdings record publicnote></PublicNote>

</Note>

<Note>

<Ordinal>2</Ordinal>

<PublicNote>This is a second Serials holdings record public note</PublicNote>

</Note>

</Notes>

<PubPatterns>

<PubPattern>

<PubPatternID>967</PubPatternID>

<CategoryID>1</CategoryID>

<Category>Basic Bibliographic Unit</Category>

<EncodLevelH/>

<TextualHoldings>Textual Holdings note</TextualHoldings>

<Issues>

<Issue>

<IssueID>399</IssueID>

<IssuePublicNote>Issue Public Note</IssuePublicNote>

<TitleOfSupIndex/>

<IssueStatusId>1</IssueStatusId>

<IssueStatus>Received</IssueStatus>

<Retained>1</Retained>

<ItemRecordID>0</ItemRecordID>

<Barcode/>

<AssignedBranchID>;0</AssignedBranchID>

<AssignedBranch/>

<AssignedCollectionID>0</AssignedCollectionID>

<Collection/>

<Designation>(Apr. 22 2009)</Designation>

<CallNumber/>

<VolumeNumber/>

<ItemStatusID>0</ItemStatusID>

<ItemStatus/>

<ShelfLocationID>0</ShelfLocationID>

<ShelfLocation/>

<ItemPublicNote/>

</Issue>

...

<Issue>

<IssueID>407</IssueID>

<IssuePublicNote/>

<TitleOfSupIndex/>

<IssueStatusId>2</IssueStatusId>

<IssueStatus>Expected</IssueStatus>

<ItemRecordID>0</ItemRecordID>

<Barcode/>

<AssignedBranchID>0</AssignedBranchID>

<AssignedBranch/>

<AssignedCollectionID>0</AssignedCollectionID>

<Collection/>

<Designation>(Apr. 22 2017)</Designation>

<CallNumber/>

<VolumeNumber/>

<ItemStatusID>0</ItemStatusID>

<ItemStatus/>

<ShelfLocationID>0</ShelfLocationID>

<ShelfLocation/>

<ItemPublicNote/>

</Issue>

</Issues>

</PubPattern>

</PubPatterns>

</CopyRecord>

</CopyRecords>

</Record>

</SubscriptionXMLRecord>

</GetSubscriptionsByIDRow>

</GetSubscriptionsByIDRows>

</GetSubscriptionsByIDResult>

### XML Elements in the Subscription Data

|
|

Data Element

|

Description

|
|

Record

|

Top Level Node

|
|

BibliographicRecordID

|

The Bibliographic Record requested

|
|

CopyRecords

|

A list of copy records (if any) Associated with the Bibliographic Record

|
|

CopyID

|

The Unique ID of the copy record

|
|

CollectionID

|

The collection (if any) assigned to the copy record (0 indicates no collection)

|
|

CollectionName

|

The name of the collection (if any)

|
|

CompletenessCode

|

The completeness code (if any) associated with the copy record

|
|

OrganizationID

|

The organization associated with the copy record

|
|

OrganizationName

|

The organization name associated with the copy record

|
|

CopyNumber

|

The copy number assigned by the library (if any) to the copy record

|
|

DisplayInPAC

|

Indicates if the copy record displays in PAC

|
|

RetentionDescription

|

Describes the library’s retention policy

|
|

HoldingsStatement

|

Describes the library’s holdings, built by the Polaris ILS

|
|

HoldingsNote

|

A free text description of the library’s holdings entered by the library

|
|

RetentionNote

|

A free text description of the library’s retention policy

|
|

Notes

|

A list public notes created by the library (if any)

|
|

Note

|

A note associated with the copy record

|
|

Ordinal

|

Indicates the order of the note in the record

|
|

PublicNote

|

The Note

|
|

PubPatterns

|

A list of publication patterns (if any associated with the copy record)

|
|

PubPattern

|

A publication pattern

|
|

PubPatternID

|

A unique ID for the publication pattern

|
|

CategoryID

|

A publication pattern category ID

|
|

Category

|

A description of the publication pattern

|
|

EncodLevelH

|

Indicates the holdings level of textual holdings Indicator Level

|
|

TextualHoldings

|

A free text description of the library’s holdings

|
|

Issues

|

A list of the issues associated with a publication pattern (if any)

|
|

Issue

|

An Issue record

|
|

IssueID

|

The unique ID of the issue

|
|

IssuePublicNote

|

A public note entered by the library for the issue (if any)

|
|

TitleOfSupIndex

|

The title of a supplement or index (if any)

|
|

IssueStatusId

|

The Issue Status ID

|
|

IssueStatus

|

A description of the issue status

|
|

Retained

|

Indicates if the library has retained this issue

|
|

ItemRecordID

|

The Item Record associated with the issue (if any) (0 = there is not item record attached)

|
|

Barcode

|

The barcode of the item associated with the issue (if any)

|
|

AssignedBranchID

|

The Polaris Organization that holds the item record (if any)

|
|

AssignedBranch

|

The name of the Polaris organization that holds the item record (if any)

|
|

AssignedCollectionID

|

The collection assigned to the item record (if any)

|
|

Collection

|

The name of the collection assigned to the item record (if any)

|
|

Designation

|

Issue/Part’s designation. This string is converted from chronology and enumeration values, formats and captions by Polaris. This is usually the string appears on the publication’s face and displays in PAC.

|
|

CallNumber

|

The call number associated with the item (if any)

|
|

VolumeNumber

|

The volume number associated with the item (if any)

|
|

ItemStatusID

|

The ID of the items status (if any)

|
|

ItemStatus

|

A textual description of the items status (if any)

|
|

ShelfLocationID

|

The ID of the items shelf location (if any)

|
|

ShelfLocation

|

A textual description of the item’s shelf location (if any)

|
|

ItemPublicNote

|

A public note assigned by the library to the item (if any)

### Example: Subscription XML After HTML Decoding

|
|

<Record>

<BibliographicRecordID>597046</BibliographicRecordID>

<CopyRecords>

<CopyRecord>

<CopyID>33</CopyID>

<CollectionID>75</CollectionID>

<CollectionName>Magazines</CollectionName>

<CompletenessCode>Incomplete</CompletenessCode>

<OrganizationID>101</OrganizationID>

<OrganizationName>Southern Adirondack Library System</OrganizationName>

<CopyNumber>1</CopyNumber>

<DisplayInPAC>1</DisplayInPAC>

<RetentionDescription>Other general retention policy</RetentionDescription>

<HoldingsStatement/>

<HoldingsNote/>

<RetentionNote/>

<Notes>

<Note>

<Ordinal>1</Ordinal>

<PublicNote>This is a serials holdings record public note</PublicNote>

</Note>

<Note>

<Ordinal>2</Ordinal>

<PublicNote>This is a second Serials holdings record public</PublicNote>

</Note>

</Notes>

<PubPatterns>

<PubPattern>

<PubPatternID>967</PubPatternID>

<CategoryID>1</CategoryID>

<Category>Basic Bibliographic Unit</Category>

<EncodLevelH/>

<TextualHoldings>Textual Holdings note</TextualHoldings>

<Issues>

<Issue>

<IssueID>399</IssueID>

<IssuePublicNote>Issue Public Note</IssuePublicNote>

<TitleOfSupIndex/>

<IssueStatusId>1</IssueStatusId>

<IssueStatus>Received</IssueStatus>

<Retained>1</Retained>

<ItemRecordID>0</ItemRecordID>

<Barcode/>

<AssignedBranchID>0</AssignedBranchID>

<AssignedBranch/>

<AssignedCollectionID>0</AssignedCollectionID>

<Collection/>

<Designation>(Apr. 22 2009)</Designation>

<CallNumber/>

<VolumeNumber/>

<ItemStatusID>0</ItemStatusID>

<ItemStatus/>

<ShelfLocationID>0</ShelfLocationID>

<ShelfLocation/>

<ItemPublicNote/>

</Issue>

...

<Issue>

<IssueID>407</IssueID>

<IssuePublicNote/>

<TitleOfSupIndex/>

<IssueStatusId>2</IssueStatusId>

<IssueStatus>Expected</IssueStatus>

<ItemRecordID>0</ItemRecordID>

<Barcode/>

<AssignedBranchID>0</AssignedBranchID>

<AssignedBranch/>

<AssignedCollectionID>0</AssignedCollectionID>

<Collection/>

<Designation>(Apr. 22 2017)</Designation>

<CallNumber/>

<VolumeNumber/>

<ItemStatusID>0</ItemStatusID>

<ItemStatus/>

<ShelfLocationID>0</ShelfLocationID>

<ShelfLocation/>

<ItemPublicNote/>

</Issue>

</Issues>

</PubPattern>

</PubPatterns>

</CopyRecord>

</CopyRecords>

</Record>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0