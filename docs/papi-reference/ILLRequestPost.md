# ILLRequestPost

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/ILLRequestPost.htm_

You are here:

## ILLRequestPost

Start the ILL request process. This process is based on a “messaging” system and will allow a Polaris patron to place an ILL request. After calling the ILL_RequestCreate method, the message exchange is complete when a StatusType of Error (1) or Answer (2) is returned or if an error is raised via a database exception.

|
|  
| POST
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/illrequest
|  

### Authorization required?

Yes

### XML Body Elements

|
| Name
|

Required

|

Description/Notes

|
|

PatronID

|

Yes

|

ID of patron placing ILL request

|
|

VolumeNumber

|

No

|

Volume of ILL request

|
| Author
| No
| Primary author of the work

|
| Title
| Yes
| Primary title of the work

|
| Publisher
| No
| Publisher of the work

|
| Edition
| No
| Edition of the work

|
| PublicationDate
| No
| Year of publication

|
| ISBN
| No
| The ISBN number of the work

|
| ISSN
| No
| The ISSN number of the work

|
| LCCN
| No
| The LCCN number of the work

|
|

ItemType

|

No

|

Item type code for requested item

1 - Monograph
2 - Serial
3 - Other

|
|

MediumType

|

No

|

Medium type code for requested item

1 - Printed
3 - Microform
4 - Film-or-video-recording
5 - Audio-recording
6 - Machine-readable
Other

|
|

PickupOrgID

|

Yes

|

ID of branch where patron would like to pick up item

0 - Use the patron's registered library

|
|

WorkstationID

|

No

|

ID of workstation where this hold request was created

|
|

UserID

|

No

|

ID of Polaris user that created this request

|
| HoldPickupAreaID
| No
| ID of area in the branch where patron would like to pick up item

### XML Elements Returned

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

RequestGUID

|

Internal hold request GUID

|
|

TxnGroupQualifer

|

Txn group qualifier of this hold message

|
|

TxnQualifier

|

Txn qualifier of this hold message

|
|

StatusType

|

Status type

1 - Error
2 - Answer
3 - Conditional

|
|

StatusValue

|

Status value

1 - Hold request placed
3 - Conditional: Item available locally
4 - Conditional: Accept ILL policy
5 - Conditional: Accept even with existing holds
6 - Conditional: No items attached, still place hold
7 - Conditional: Accept local hold policy
2 - Error: Select pickup location
3 - Error: Login
10 - Error: Patron does not meet minimum age requirement

|
|

Message

|

Display text

### Sample Conditional Questions

|
|

Status Value

|

ILL Only

|

Question

|
|

3

|

Yes

|

Item is available locally. Would you like to place a local hold request?

|
|

4

|

Yes

|

Do you accept the ILL policy? [Defined in Polaris SA]

|
|

5

|

No

|

There are [12] active requests for this title. Do you still want to place the request?

|
|

6

|

No

|

No items are linked to this record. Your request may not be filled. Do you still want to place this request?

|
|

7

|

No

|

The library charges for hold requests. Do you still want to place the request?

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/illrequest

### Body

|
|

<ILLRequestCreateData xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PatronID>67794</PatronID>

<Title>Black pioneers in American history </Title>

<ISBN/>

<LCCN/>

<ItemType>0</ItemType>

<MediumType>1</MediumType>

<PickupOrgID>99</PickupOrgID>

<WorkstationID>1243</WorkstationID>

<UserID>1</UserID>

<HoldPickupAreaID>1</HoldPickupAreaID>

</ILLRequestCreateData>

### Return - Success

|
|

HTTP/1.1 200 OK

<ILLRequestResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<RequestGUID>string</RequestGUID>

<TxnGroupQualifer>string</TxnGroupQualifer>

<TxnQualifier>string</TxnQualifier>

<StatusType>0</StatusType>

<StatusValue>0</StatusValue>

<Message>string</Message>

</ILLRequestResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<ILLRequestResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-4020</PAPIErrorCode>

<ErrorMessage>ILL Request Pickup Area invalid for Pickup Branch</ErrorMessage>

<RequestGUID/>

<TxnGroupQualifer/>

<TxnQualifier/>

<StatusType>1</StatusType>

<StatusValue>0</StatusValue>

<Message/>

</ILLRequestResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0