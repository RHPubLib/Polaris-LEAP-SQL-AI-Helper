# HoldRequestReply

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceHoldRequestReply.htm_

You are here:

## HoldRequestReply

Send a reply message responding to the results of a previous HoldRequestCreate or HoldRequestReply procedure call. The HoldRequestCreate procedure must be called before executing this procedure. The RequestGUID, TxnGroupQualifier and TxnQualifier returned by the HoldRequestCreate procedure will be used as input parameters for this procedure call. These three values connect the messages together to create an ILL conversation. After calling the HoldRequestReply procedure, one or more calls to the HoldRequestReply procedure may be required. The message exchange is complete when a StatusType of Error (1) or Answer (2) is returned or if an error is raised via a database exception.

|
|  
| PUT
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/holdrequest/{RequestGuid}
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

RequestGuid

|

Yes

|

GUID of original request message

### Request Body XML

**Important:** XML elements must be in the order shown below.

|
|

<HoldRequestReplyData>

<TxnGroupQualifier/>

<TxnQualifier/>

<RequestingOrgID/>

<Answer/>

<State/>

</HoldRequestReplyData>

### XML Body Elements

|
|

Name

|

Required

|

Description/Notes

|
|

TxnGroupQualifier

|

Yes

|

Txn group qualifier

|
|

TxnQualifier

|

Yes

|

Txn qualifier

|
|

RequestingOrgID

|

Yes

|

Org ID of branch processing this request

|
|

Answer

|

Yes

|

Answer

1 - Yes
0 - No or Cancel

|
|

State

|

Yes

|

Which conditional will this answer be applied to?

1 - Item available locally
2 - Accept ILL policy
3 - Accept even with existing holds
4 - No items attached, still place hold
5 - Accept local hold policy (charge)

### XML Elements Returned

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

Negative values represent errors and are defined elsewhere.

**Note**: On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

|
| RequestGUID
| When a patron is placing a hold request, they may be asked to confirm details before the request is placed. This field, with TxnGroupQualifier and TxnQualifer, is an internal identifier created by the system to maintain the transaction state while a multistep hold request is being processed.

|
| TxnGroupQualifier
| See RequestGUID, above.

|
| TxnQualifier
| See RequestGUID, above.

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

0 - Hold request not placed
1 - Hold request placed
2 - Error: Select pickup location
3 - Error: Login3 - Conditional: Item available locally
4 - Conditional: Accept ILL policy
5 - Conditional: Accept even with existing holds
6 - Conditional: No items attached, still place hold
7 - Conditional: Accept local hold policy

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

### Example (issue reply to previous create)

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/holdrequest/B9313957-78AD-4633-87CE-40B7391F7862

### Body

|
|

<HoldRequestReplyData>

<TxnGroupQualifier>BQeK9WLrNew_0BRKISzr2G</TxnGroupQualifier>

<TxnQualifier>496QYG6MMKss1C6nagTGkG</TxnQualifier>

<RequestingOrgID>74</RequestingOrgID>

<Answer>1</Answer>

<State>3</State>

</HoldRequestReplyData>

### Return - Success

|
|

HTTP/1.1 200 OK

<HoldRequestResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<RequestGUID/>

<TxnGroupQualifer/>

<TxnQualifier/>

<StatusType>2</StatusType>

<StatusValue>1</StatusValue>

<Message>Your request has been placed.</Message>

<QueuePosition>2</QueuePosition>

<QueueTotal>2</QueueTotal>

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