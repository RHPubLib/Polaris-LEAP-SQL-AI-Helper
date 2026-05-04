# ItemCheckinPost

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/ItemCheckinPost.htm_

You are here:

## ItemCheckinPost

The ItemCheckin endpoint allows you to check in an item as a staff member.

|
|  
| POST
|

/protected/1 {Version}/{LangID}/{AppID}/{OrgID}/item/{ItemBarcode}/checkin

|

 

### Authorization Required?

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

ItemBarcode

|

Yes

|

The item's barcode

### Request Body XML

|
|

<ItemCheckInData>

<LogonBranchID>{organization-id}</LogonBranchID>

<LogonUserID>{user-id}</LogonUserID>

<LogonWorkstationID>{workstation-id}</LogonWorkstationID>

</ItemCheckInData>

### Request Body XML

|
|

Name

|

Description/Notes

|
| LogonBranchID
| Current branch (can default to System [1]).

|
|

LogonUserID

|

Current user (can default to PolarisExec).

|
|

LogonWorkstationID

|

Current workstation (can default to OPACDefault).

### XML Elements Returned

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

PAPI error code. Negative values represent errors and are defined here.

|
| ErrorMessage
| Error or information message.

|
| ItemRecordID
| The Polaris item record identifier associated with the specified item barcode.

|
| OriginalCheckOutDate
|

The date the item was originally checked out to the specified patron.

|
| AssignedBranchID
| The numeric identifier of the branch the item is assigned to.

|
| AssignedCollectionID
|

The numeric identifier of the collection the item is assigned to.

|
| ItemStatusID
|

The numeric identifier of the item's current status.

|
| PreviousItemStatusID
|

The numeric identifier of the item's previous status.

|
| ItemBarcode
| The barcode of the item checked in.

|
| Title
| Primary title of the work.

|
| MaterialTypeID
| The material type code for item records (see MaterialTypesGet).

|
| SelfCheckMediaTypeID
| Numeric ID for the self-check media type configuration in the system.

|
| IsMagnetic
|

Indicates if the item is affected by magnetic fields.

-

true - The item is magnetic.

-

false - The item is not magnetic.

|
| CanDesensitize
|

Indicates if the item has a security strip that can be desensitized.

-

true - The item can be desensitized.

-

false - The item cannot be desensitized.

|
| DoubleSided
|

Indicates if the item has both a spine and cover magnet to desensitize.

-

true - The item has multiple magnets to desensitize.

-

false - The item does not have multiple magnets to desensitize.

|
| Unlocker
|

Indicates if the item is stored in an AV case or security locker.

-

true - The item is stored in a locker, which must be opened after check out.

-

false - The item is not stored in a locker.

|
| DDM_MediaFormatID
|

For EnvisionWare RFID, this references the Danish Data Model (DDM) format for the item material type.

-

0 - Undefined

-

1 - Book

-

2 - CD/DVD/etc.

-

3 - Magnetic Tape

-

4 - Other

-

5 - Special Handling Required

-

6 - Small Item

|
| ShelfLocation
| The item's location on the shelf.

|
| CallNumber
| The item's ISBN number.

|
| PatronBarcode
| The barcode of the patron checking in the item.

|
| Comment
| A comment entered by staff at the time of check in.

|
| HoldDataResult
| More detailed information if the item has a hold.

|
| HoldDataResult.TrappingPatronBarcode
| The barcode of the patron who is trapping the item.

|
| HoldDataResult.TrappingPatronName
| The name of the patron who is trapping the item.

|
| HoldDataResult.PickupBranchName
| The name of the branch where the patron will pick up the item.

|
| HoldDataResult.PickupArea
| The name of the branch area where the patron will pick up the item.

|
| InTransitResult
| More detailed information if the item has a status of In-Transit.

|
| InTransitResult.InTransitSentBranchID
| The ID of the branch the item is sent from.

|
| InTransitResult.InTransitRecvdBranchID
| The ID of the branch that will receive the item.

|
| InTransitResult.ItemStatusDate
| The date when the item status changed.

|
| InTransitResult.InTransitSentDate
| The date when the item was sent to transit.

|
| InTransitResult.Status
| The item's status, in the form of a comment.

### Example

|
| https://localhost/REST/protected/v1/1033/100/1/22I4eghLmnbbpgFOPE0PP7OLC8ZJpwV7
/item/0000100004126/checkin

### Body

|
|

<ItemCheckInData>

<LogonBranchID>99</LogonBranchID>

<LogonUserID>1</LogonUserID>

<LogonWorkstationID>1243</LogonWorkstationID>

</ItemCheckInData>

### Return - Success

|
|

<ItemCheckInResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage i:nil="true" />

<ItemRecordID>68</ItemRecordID>

<OriginalCheckOutDate i:nil="true" />

<AssignedBranchID>101</AssignedBranchID>

<AssignedCollectionID i:nil="true" />

<ItemStatusID>6</ItemStatusID>

<PreviousItemStatusID>2</PreviousItemStatusID>

<ItemBarcode>R0244500840</ItemBarcode>

<Title>Drum Runnin' Fool</Title>

<MaterialTypeID>1</MaterialTypeID>

<SelfCheckMediaTypeID>1</SelfCheckMediaTypeID>

<IsMagnetic>false</IsMagnetic>

<CanDesensitize>true</CanDesensitize>

<DoubleSided>true</DoubleSided>

<Unlocker>false</Unlocker>

<DDM_MediaFormatID>1</DDM_MediaFormatID>

<ShelfLocation i:nil="true" />

<CallNumber>Fict suffix318218</CallNumber>

<PatronBarcode>patronbarcode</PatronBarcode>

<Comment>string</Comment>

<HoldData i:nil="true" />

<InTransitResult>

<InTransitSentBranchID>3</InTransitSentBranchID>

<InTransitRecvdBranchID>101</InTransitRecvdBranchID>

<ItemStatusDate>2024-10-15T15:02:46.36</ItemStatusDate>

<InTransitSentDate>2024-10-15T15:02:46.363</InTransitSentDate>

<Status>Out -&gt; In-Transit</Status>

</InTransitResult>

</ItemCheckInResult>

### Return - Failed

|
|

<ItemCheckInResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-3506</PAPIErrorCode>

<ErrorMessage>Check in failed, invalid organization ID: xxxx </ErrorMessage>

<ItemRecordID>2265135</ItemRecordID>

<OriginalCheckOutDate>2024-08-12T14:19:26.596Z</OriginalCheckOutDate>

<AssignedBranchID>0</AssignedBranchID>

<AssignedCollectionID>0</AssignedCollectionID>

<ItemStatusID>0</ItemStatusID>

<PreviousItemStatusID>0</PreviousItemStatusID>

<ItemBarcode>string</ItemBarcode>

<Title>string</Title>

<MaterialTypeID>0</MaterialTypeID>

<SelfCheckMediaTypeID>0</SelfCheckMediaTypeID>

<IsMagnetic>true</IsMagnetic>

<CanDesensitize>true</CanDesensitize>

<DoubleSided>true</DoubleSided>

<Unlocker>false</Unlocker>

<DDM_MediaFormatID>0</DDM_MediaFormatID>

<ShelfLocation>string</ShelfLocation>

<CallNumber>string</CallNumber>

<PatronBarcode>string</PatronBarcode>

<Comment>string</Comment>

</ItemCheckInResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0