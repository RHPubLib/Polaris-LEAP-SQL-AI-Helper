# JobsPurchaseOrdersResultGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/JobsPurchaseOrdersResultsGet.htm_

You are here:

## JobsPurchaseOrdersResultGet

This jobs endpoint returns acquisitions purchase order job results. Results are restricted to the Polaris user's purchase order. The Polaris System Administration (staff client) Profile, "API: Use Fund Name" (Profiles > Acquisitions/Serials) controls if this endpoint returns the Fund name (Yes) or the Alternate Fund name (No).

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{accesstoken}/jobs/purchaseorders/{jobguid}/result
|  

### Authorization required?

Yes

### Protected method?

Yes

### HTTP Response Codes

The following HTTP codes are returned.

|
|

Number

|

Description/Notes

|
| 200
|

Success

|
| 401
| Unauthorized

### PAPI Error Codes

|
|

Values

|

Description/Notes

|
| 0
|

Success, the purchase order, line items, bibliographic records, line item segments are created and released.

|
| -1
| Failure, the purchase order is not created, or cannot be released.

|
| -3
|

The purchase order is created, but one of the following errors occurred:

-

One or more line item segments weren't created

-

One or more item records weren't created

### Example

|
| https://[hostname]/PAPIService/REST/protected/v1/1033/100/3/iNDUIy7LquAMDji6h2oyacFaLx3RyuM1/jobs/purchaseorders/B3BF63B0-D044-4269-9143-7DEE29B0BB1F/result

### Response

|
|

{

"PAPIErrorCode": 0,

"ErrorMessage": "",

"ExternalID": "{D2BF63B0-D044-4269-9143-7DEE29B0BB1A}",

"PONumber": "PN1000",

"PurchaseOrderID": 1000,

"LineItems": [

{

"POLineItemID": 443365,

"LineNumber": 1,

"ExternalLineItemID": "{D2BF63B0-D044-4269-9143-7DEE29B0BB1A}",

"BibRecordID": 1000,

"LineItemSegments": [

{

"POLineItemSegmentID": 2343,

"POLISegmentNumber": 1,

"EDIPOLISegNum": "443365-1",

"Location":"ME2",

"Fund":"CD Spoken Word",

"Collection":"col1",

"CallNumber":"MP3 FICTION Baldacci, D",

"Copies":3

}

]

}

],

"LineItemErrors": [

{

"ExternalLineItemID": "{0438E02C-CD66-4432-8FAE-669E58CC2413}",

"ErrorMessage": "",

"LineItemSegmentErrors": [

{

"ErrorMessage": "Unable to create line item segment.",

"Organization": "",

"Collection": "",

"Fund": "",

"Quantity": 0,

"CallNumber": ""

}

]

}

],

"ItemRecordCreateErrors": [

"Item creation failed for (Line#, Seg#): (1, 1) - no available item template"

]

}

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0