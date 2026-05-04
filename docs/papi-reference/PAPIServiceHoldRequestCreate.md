# HoldRequestCreate

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceHoldRequestCreate.htm_

You are here:

## HoldRequestCreate

Start the local hold request process. This process is based on a “messaging” system and will allow a Polaris patron to place a local hold request. After calling the HoldRequestCreate method, one or more calls to the HoldRequestReply method may be required. The message exchange is complete when a StatusType of Error (1) or Answer (2) is returned or if an error is raised by a database exception.

### Placing Hold Requests Against Serial Publications

Although a call to BibGet will return a format of **Serial**, Polaris logic that is not exposed in the API determines whether the record is actually a “serial bib.” However, if you default to “first available copy,” the library member can get a copy quicker. Here are the possibilities:

- **Bib ID and item barcode** - Item-specific request

- **Bib ID, item barcode, and item’s volume number** - First available copy of a specific volume or issue

- **Bib ID and item’s designation** - First available copy of a specific “serial bib”

- **Bib ID and item’s volume number** - First available copy of a specific multi-part set bib

|
|  
| POST
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/holdrequest
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

ID of Patron placing hold request

|
|

BibID

|

Yes

|

ID of bibliographic record hold is being placed on

|
|

ItemBarcode

|

 

|

Barcode of item-specific hold request

|
|

VolumeNumber

|

 

|

Volume of hold request

|
|

Designation

|

 

|

Serial designation of hold request

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

IsBorrowByMail

|

 

|

If request is Borrow by Mail request. 0 - no; 1 - yes.

|
|

PatronNotes

|

 

|

Notes created by patron

|
|

ActivationDate

|

 

|

Date this hold request will become active

|
|

WorkstationID

|

Yes

|

ID of workstation where this hold request was created

|
|

UserID

|

Yes

|

ID of Polaris user that created this request

|
|

RequestingOrgID

|

Yes

|

ID of branch where this hold request was created

|
|

TargetGUID

|

 

|

GUID of search target. ONLY USED IF NOT LOCAL.

|
| HoldPickupAreaID
|  
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
| Error or information message.

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

|
|

QueuePosition

|

If successfully placed, position in hold queue

|
|

QueueTotal

|

If successfully placed, total holds in queue

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

 

|

There are [12] active requests for this title. Do you still want to place the request?

|
|

6

|

 

|

No items are linked to this record. Your request may not be filled. Do you still want to place this request?

|
|

7

|

 

|

The library charges for hold requests. Do you still want to place the request?

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/holdrequest

### Body

|
|

<HoldRequestCreateData>

<PatronID>299377</PatronID>

<BibID>15592</BibID>

<ItemBarcode/>

<VolumeNumber/>

<Designation/>

<PickupOrgID>74</PickupOrgID>

<IsBorrowByMail>0</IsBorrowByMail>

<PatronNotes/>

<ActivationDate>2009-11-17T09:28:00.00</ActivationDate>

<WorkstationID>1</WorkstationID>

<UserID>1</UserID>

<RequestingOrgID>74</RequestingOrgID>

<TargetGUID></TargetGUID>

<HoldPickupAreaID>0</HoldPickupAreaID>

</HoldRequestCreateData>

### Return - Success

|
|

HTTP/1.1 200 OK

<HoldRequestResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<RequestGUID>7F279D6E-CFDE-4AE3-BE96-EE12305CDF11</RequestGUID>

<TxnGroupQualifer>BQeK9WLrNew_0BRKISzr2G</TxnGroupQualifer>

<TxnQualifier>496QYG6MMKss1C6nagTGkG</TxnQualifier>

<StatusType>3</StatusType>

<StatusValue>5</StatusValue>

<Message>There are [1] active requests for this title. Do you still want to place the request?</Message>

<QueuePosition>0</QueuePosition>

<QueueTotal>0</QueueTotal>

</HoldRequestResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<HoldRequestResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-4006</PAPIErrorCode>

<ErrorMessage/>

<RequestGUID/>

<TxnGroupQualifer/>

<TxnQualifier/>

<StatusType>0</StatusType>

<StatusValue>0</StatusValue>

<Message/>

<QueuePosition>0</QueuePosition>

<QueueTotal>0</QueueTotal>

</HoldRequestResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0