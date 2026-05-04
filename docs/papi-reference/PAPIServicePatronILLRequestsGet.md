# PatronILLRequestsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronILLRequestsGet.htm_

You are here:

## PatronILLRequestsGet

This method returns a list of ILL requests placed by the specified patron. The list can be filtered by the status of the request.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/illrequests/all
|  

|
|  
| GET
| /public/1/patron/{PatronBarcode}/illrequests/ReceivedTransferred
|  

|
|  
| GET
| /public/1/patron/{PatronBarcode}/illrequests/cancelled
|  

### Authorization required?

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

PatronBarcode

|

Yes

|

Barcode of patron

### XML Elements Returned

One or more ILL requests placed by the patron. The list is sorted in ascending order by activation date.

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

|
|

ILLRequestID

|

Polaris ID of the Hold Request

|
| ILLStatusID
| Status code of an inter-library loan (ILL) request.
1 - Inactive
3 - Active
5 - Shipped
10 - Received-Held
11 - Received-Transferred
12 - Received-Satisfied
13 - Received-Used
14 - Received-Unused
15 - Returned
16 - Cancelled

|
| PatronID
| Internal patron record ID.

|
| ItemRecordID
| Internal item record ID.

|
| BibRecordID
| Internal bibliographic record ID.

|
| PickupBranchID
| ID of branch at which the item should be picked up

|
| Author
| Author of the item

|
| Title
| Title of the item

|
| Format
| Format (TOM - Type of Material) for the ILL request title.

|
| CreationDate
| Date ILL request was created.

|
| ActivationDate
| Date and ILL request becomes active.

|
| Status
| Status description label that corresponds with the ILLStatusID field.

|
| Item
| Item status description.

|
| NeedByDate
| Provided by patron as the date the request is needed

|
| PickupBranch
| Name of the branch the item should be picked up at.

|
| FormatID
| Polaris ID of the type of material (TOM)

|
| LastStatusTransitionDate
| The date that the ILL request status was last changed.

|
| OpacNotes
| Note in public access catalog

|
| CallNumber
| Call Number of the item (populated after item is "received")

|
| VolumeAndIssue
| Volume and issue number if applicable

|
| PickupByDate
| Date that the item will be held until

|
| InnReachTrackingID
| If the ILL request is associated with INN-Reach, this is the internal ID of the record containing related INN-Reach field data for the request.

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/3/patron/21234000002105/
illrequests/all

http://localhost/PAPIService/REST/public/v1/1033/100/3/patron/21234000002105/
illrequests/ReceivedTransferred

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronILLRequestsGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage></ErrorMessage>

<PatronILLRequestsGetRows>

<PatronILLRequestsGetRow>

<ILLRequestID>6</ILLRequestID>

<ILLStatusID>11</ILLStatusID>

<PatronID>71128</PatronID>

<ItemRecordID>9475571</ItemRecordID>

<BibRecordID>806821</BibRecordID>

<PickupBranchID>107</PickupBranchID>

<Author i:nil="true" />

<Title>HARRY POTTER AND THE GOBLET OF FIRE BOO</Title>

<Format>Sound Recording</Format>

<CreationDate>2008-03-05T10:08:54.857</CreationDate>

<ActivationDate>2011-11-18T09:06:06.86</ActivationDate>

<Status>Received</Status>

<Item>Transferred</Item>

<NeedByDate>2009-03-05T00:00:00</NeedByDate>

<PickupBranch>Waterford Public Library</PickupBranch>

<FormatID>5</FormatID>

<LastStatusTransitionDate>2011-12-06T16:21:12.857</LastStatusTransitionDate>

<OpacNotes i:nil="true" />

<CallNumber>ILL</CallNumber>

<VolumeAndIssue i:nil="true" />

<PickupByDate i:nil="true" />

</PatronILLRequestsGetRow>

</PatronILLRequestsGetRows>

</PatronILLRequestsGetResult>

### Error Message

If the organization ID does not exist in the database, error code -5000 ("Invalid OrganizationID supplied") is returned.

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0