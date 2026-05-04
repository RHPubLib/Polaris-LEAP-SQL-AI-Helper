# PatronHoldRequestsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronHoldRequestsGet.htm_

You are here:

## PatronHoldRequestsGet

Returns a list of hold requests placed by the specified patron. The list can be filtered by all hold requests or by the request status. This API requires authorization.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/holdrequests/{RequestID}/{endpoint}
|  

The URI supports the following endpoints:

|
| Endpoint
| Description

|
| all
| Returns all hold requests.

|
| inactive
| Returns inactive hold requests.

|
| active
| Returns active hold requests.

|
| pending
| Returns pending hold requests.

|
| shipped
| Returns shipped hold requests.

|
| held
| Returns hold requests that have been held.

|
| notsupplied
| Returns hold requests that have not been supplied.

|
| unclaimed
| Returns unclaimed hold requests.

|
| expired
| Returns expired hold requests.

|
| cancelled
| Returns cancelled hold requests.

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
|

PatronBarcode

|

Yes

|

Barcode of patron

### XML Elements Returned

The list is sorted in ascending order by activation date.

|
|

Name

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

HoldRequestID

|

Polaris ID of the Hold Request

|
|

BibID

|

The ID of the associated bibliographic record

|
| ConstituentBibID
| The bibliographic record that's tied to this hold request has another bibliographic record associated with it. The is commonly used when different titles are "bound together." This is the id of that associated bibliographic record.

|
|

StatusID

|

Polaris ID of the status of the hold request

1 - Inactive
3 - Active
4 - Pending
5 - Shipped
6 - Held
7 - Not Supplied
8 - Unclaimed
9 - Expired
16 - Cancelled

|
|

StatusDescription

|

Description of the status of the hold request.

|
|

Title

|

Title of the item

|
|

Author

|

Author of the item

|
|

CallNumber

|

Call Number of the item

|
|

FormatID

|

Polaris ID of the type of format (see "Material Format Types" on page 1)

|
|

FormatDescription

|

Format description

|
|

PickupBranchID

|

ID of branch at which the item should be picked up.

|
|

PickupBranchName

|

Name of branch at which the item should be pickup up.

|
|

PickupByDate

|

Date that the item will be held until

|
|

QueuePosition

|

Indicates the position where this hold request is in the queue for this bibliographic record. This may be null depending on the status of the hold request.

|
|

QueueTotal

|

Total number of hold requests for this bibliographic record.

|
|

ActivationDate

|

Date the hold request was activated. An activation date in the future means the request is currently inactive.

|
|

ExpirationDate

|

Expiration date of the hold request

|
|

GroupName

|

Name used to identify a group of titles that can satisfy this hold request

|
|

ItemLevelHold

|

Is the request an item level hold, or will any item associated with this title satisfy the request.

|
|

BorrowByMail

|

Is the request a Borrow by Mail type of request.

|
|

HasConstituentBib

| Does the bibliographic record that's tied to this hold request have constituent (associated) bibliographic records.

|
| NewPickupBranchID
| After placing a hold request, patrons can change which branch they want the item to be sent to. This is the ID of that new branch.

|
| NewPickupBranch
| After placing a hold request, patrons can change which branch they want the item to be sent to. This is the name of that new branch.

|
| InnReachType
| Whether or not this hold request is an INN-Reach request (0 or 1).

|
| Designation
| Designation, when present

|
| VolumeNumber
| Volume, when present

|
| PACDisplayNotes
| PAC Display Note field (maximum 255 characters)

|
| CanSuspend
| A Boolean that indicates whether the patron's hold request can be suspended

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/holdrequests/all

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronHoldRequestsGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage><ErrorMessage/>

<PatronHoldRequestsGetRows>

<PatronHoldRequestsGetRow>

<HoldRequestID>801604</HoldRequestID>

<BibID>620893</BibID>

<StatusID>8</StatusID>

<StatusDescription>Unclaimed</StatusDescription>

<Title>Moose's big idea</Title>

<Author>Greene, Stephanie.</Author>

<CallNumber>J Fict Gre</CallNumber>

<FormatID>1</FormatID>

<FormatDescription>Book</FormatDescription>

<PickupBranchID>90</PickupBranchID>

<PickupBranchName>Saratoga Springs Public Library</PickupBranchName>

<PickupByDate>2008-12-13T23:59:00</PickupByDate>

<QueuePosition>0</QueuePosition>

<QueueTotal>0</QueueTotal>

<ActivationDate>2008-12-03T00:00:00</ActivationDate>

<ExpirationDate>2009-04-02T23:59:00</ExpirationDate>

<GroupName/>

<ItemLevelHold>false</ItemLevelHold>

</PatronHoldRequestsGetRow>

...

</PatronHoldRequestsGetRows>

<PatronHoldRequestsGetResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronHoldRequestsGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid Status ID Filter</ErrorMessage>

<PatronHoldRequestsGetRows i:nil="true"/>

</PatronHoldRequestsGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0