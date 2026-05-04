# JobsPurchaseOrdersPut

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/JobsPurchaseOrdersPut.htm_

You are here:

## JobsPurchaseOrdersPut

This jobs endpoint validates acquisitions line items before creating a purchase order. When used with the 'preordervalidation' query string value, this method will validate acquisition purchase-order job data. This is usually called before submitting an acquisition purchase-order job to verify locations, funds and collections. Firm order (3) is the only order type currently supported. Purchase (8) is the only payment method currently supported.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{accesstoken}/jobs/purchaseorders?preordervalidation=1
|  

**Notes:**

- The Polaris user is determined by the AccessToken from staff authentication.

- To limit permission issues, we recommend using a Polaris staff user account with admin permissions.

### Authorization required?

Yes

### Protected method?

Yes

### Query String Parameters

|
| Name
|

Values

|

Required

|

Description/Notes

|
|

preordervalidation

|

0 or 1

|

No

|

Preorder validation mode is enabled when set to 1.

### Elements Returned

The following XML elements are returned.

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

### Example

|
| https://[hostname]/PAPIService/REST
/protected/v1/1033/100/3/iNDUIy7LquAMDji6h2oyacFaLx3RyuM1/jobs/purchaseorders?preordervalidation=1

### Body

|
|

{

"Vendor": "btr", // Polaris supplier RecordName

"OrderedAtLocation": "AMS", // Location is a Polaris Organization abbreviation (branch level)

"OrderType": 3, // Firm order (3) - only order type currently supported

"PaymentMethod": 8, // Purchase (8) - only payment method currently supported

"ExternalID": "{B51F75AC-83AF-42A8-9920-21AA372E1ABF}" ,

"Copies": 7,

"ImportProfileName": "PAPI PO import profile", // optional field.

"LineItems" : [

// line 1

{

"ExternalLineItemID": "{0438E02C-CD66-4432-8FAE-669E58CC2413}",

"Copies": "4",

"LineItemSegments": [

{

"Location": "ME2",

"Fund": "CD Spoken Word",

"Collection": "Col1",

"Copies": 2

},

{

"Location": "BB1",

"Fund": "CD Spoken Word",

"Collection": "Col1",

"Copies": 2

}

]

},

// line 2

{

"ExternalLineItemID": "{D2BF63B0-D044-4269-9143-7DEE29B0BB1A}",

"Copies": "3",

"LineItemSegments": [

{

"Location": "ME2",

"Fund": "CD Spoken Word",

"Collection": "Col2",

"Copies": 3

}

]

}

]

}

### Return - Success

|
|

HTTP/1.1 200 OK

<JobsPurchaseOrdersPreorderValidationResult>

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>string</ErrorMessage>

<ExternalID>string</ExternalID>

<LineItemValidationErrors>

<LineItemValidationError>

<ExternalLineItemID>string</ExternalLineItemID>

<Errors>

<Error>

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>string</ErrorMessage>

</Error>

</Errors>

</LineItemValidationError>

</LineItemValidationErrors>

</JobsPurchaseOrdersPreorderValidationResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

{

"PAPIErrorCode":-12117,

"ErrorMessage":"Line item validation errors found.",

"ExternalID":"{B51F75AC-83AF-42A8-9920-21AA372E1ABF}",

"LineItemValidationErrors":[

{

"ExternalLineItemID":"{0438E02C-CD66-4432-8FAE-669E58CC2413}",

"Errors":[

{

"PAPIErrorCode":-12108,

"ErrorMessage":"Line item segment branch/location 'ME2' not found."

},

{

"PAPIErrorCode":-12108,

"ErrorMessage":"Line item segment branch/location 'BB1' not found."

}

]

},

{

"ExternalLineItemID":"{D2BF63B0-D044-4269-9143-7DEE29B0BB1A}",

"Errors":[

{

"PAPIErrorCode":-12110,

"ErrorMessage":"Line item segment fund 'CD Spoken Word' not found for branch/location 'SAR'."

},

{

"PAPIErrorCode":-12113,

"ErrorMessage":"Line item segment collection 'Col2' not found."

}

]

}

]

}

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0