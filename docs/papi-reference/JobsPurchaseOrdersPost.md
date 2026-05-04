# JobsPurchaseOrdersPost

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/JobsPurchaseOrdersPost.htm_

You are here:

## JobsPurchaseOrdersPost

This endpoint allows you to create a purchase order as a job. This endpoint is usually used after JobsPurchaseOrderPut, which performs preorder validation.

|
|  
| POST
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{accesstoken}/jobs/purchaseorders
|  

**Notes:**

- The Polaris user is determined by the AccessToken from staff authentication.

- To limit permission issues, we recommend using a Polaris staff user account with admin permissions.

### Authorization required?

Yes

### Protected method?

Yes

### MARC Data for Line Item Segments

|
| MARC Tag
|

Values

|

Description/Notes

|
|

020/024

|

$c

|

Purchase order line item price. The system uses this value if no 970 tag subfield $p is present.

|
| 970
| $c
| Collection (Polaris collection abbreviation)

|
| 970
| $f
| Fund (Polaris fund name or fund alternative name)

|
| 970
| $h
| Item template code. The system maps this code to the POLineItemsegments.ItemTemplateCode found in the database and attempts to use this code to find matching item templates.

|
|

970

|

$l

|

Location (Polaris branch abbreviation), used for purchase order line item segments

|
| 970
| $m
| Purchase order line item material type. The system attempts to use this value to find matching item templates.

|
| 970
| $n
| Purchase order line item non-public note

|
| 970
| $p
| Purchase order line item price. If no 970 tag subfield $p is present, the system uses the price found in the 020 or 024 tag subfield $c.

|
| 970
| $q
| Quantity

|
| 970
| $w
| Call number

### Postback URL Support

If the system administrator enables postback support in the Polaris.Job.API and you provide a valid PostbackURL, a POST request is sent once the purchase order create job has completed. The postback feature appends a query string value to the end of the supplied URL and will POST a JSON string that represents the PAPI job ID.

**Example**: POST https://localhost:4333/api/postbacklistener?PAPIJobID=C0EB7EB1-0E63-4136-A7A0-0626200C5794

If a postback fails to receive an HTTP 200 OK response, it attempts to resend the request up to six times with an increasing delay between attempts as in the example.

**Example**: 30 seconds, 1 minute, 2 minutes, 5 minutes, 10 minutes, 1 hour

**Note**:
The postback might not occur if the purchase order job fails to complete. Use the job status endpoint as a backup mechanism.

### Elements Returned

The following elements are returned.

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
| ExternalID
| The ExternalID originally passed into the method. This allows the caller to track the process using their own unique IDs.

|
| JobGuid
| The PAPI job globally unique identifier

|
| JobStatusID
| Job status ID

|
| JobStatusDescription
| Job status description

|
| LineItemValidationErrors
| A list of validation errors objects representing each line item in the purchase order

### Example

|
| https://[hostname]/PAPIService/REST/protected/v1/1033/100/3/iNDUIy7LquAMDji6h2oyacFaLx3RyuM1/jobs/purchaseorders

### JSON Body

|
|

{

"Vendor":"btr",

"OrderedAtLocation": "AMS", // Location is a Polaris Organization abbreviation (branch level)

"OrderType": 3, // Firm order (3) - only order type currently supported

"PaymentMethod": 8, // Purchase (8) - only payment method currently supported

"PONumber":"PO-1234",

"PostbackURL": "https://localhost:4333/api/postbacklistener",

"ExternalID":"{B51F75AC-83AF-42A8-9920-21AA372E1ABF}",

"ImportProfileName": "PAPI PO import profile", // optional field.

"MARCLineItems":[

{

"ExternalLineItemID":"{F3BF63B1-E041-5267-1144-7DEE29B0BB2C}",

"Copies":7,

"MARC":{

"leader":"00767cam 22002175i 4500",

"controlfields":[

{

"tag":"001",

"data":"BK0012473191"

},

{

"tag":"005",

"data":"20200102135243.0"

},

{

"tag":"008",

"data":"190424s2020 nyua c 000 1 eng "

}

],

"datafields":[

{

"tag":"010",

"ind1":" ",

"ind2":" ",

"subfields":[

{

"code":"a",

"data":"2019018578"

}

]

},

{

"tag":"020",

"ind1":" ",

"ind2":" ",

"subfields":[

{

"code":"a",

"data":"9780590353427 (pbk.)"

},

{

"code":"c",

"data":"1.99"

}

]

},

{

"tag":"245",

"ind1":"1",

"ind2":" ",

"subfields":[

{

"code":"a",

"data":"My really cool title"

}

]

},

{

"tag":"970",

"ind1":" ",

"ind2":" ",

"subfields":[

{

"code":"l",

"data":"ME2"

},

{

"code":"f",

"data":"CD Spoken Word"

},

{

"code":"c",

"data":"col1"

},

{

"code":"q",

"data":"3"

},

{

"code":"w",

"data":"MP3 FICTION Baldacci, D"

}

]

},

{

"tag":"970",

"ind1":" ",

"ind2":" ",

"subfields":[

{

"code":"l",

"data":"BB1"

},

{

"code":"f",

"data":"CD Spoken Word"

},

{

"code":"c",

"data":"col1"

},

{

"code":"q",

"data":"4"

},

{

"code":"w",

"data":"MP3 FICTION Baldacci, D"

}

]

}

]

}

},

{

"ExternalLineItemID":"{D2BF63B0-D044-4269-9143-7DEE29B0BB1A}",

"Copies":7,

"MARC":{

"leader":"00767cam 22002175i 4500",

"controlfields":[

{

"tag":"001",

"data":"BK0012473191"

},

{

"tag":"005",

"data":"20200102135243.0"

},

{

"tag":"008",

"data":"190424s2020 nyua c 000 1 eng "

}

],

"datafields":[

{

"tag":"010",

"ind1":" ",

"ind2":" ",

"subfields":[

{

"code":"a",

"data":"2019018578"

}

]

},

{

"tag":"020",

"ind1":" ",

"ind2":" ",

"subfields":[

{

"code":"a",

"data":"9780590353427 (pbk.)"

},

{

"code":"c",

"data":"1.99"

}

]

},

{

"tag":"245",

"ind1":"1",

"ind2":" ",

"subfields":[

{

"code":"a",

"data":"My really cool title"

}

]

},

{

"tag":"970",

"ind1":" ",

"ind2":" ",

"subfields":[

{

"code":"l",

"data":"ME2"

},

{

"code":"f",

"data":"CD Spoken Word"

},

{

"code":"c",

"data":"col1"

},

{

"code":"q",

"data":"3"

},

{

"code":"w",

"data":"MP3 FICTION Baldacci, D"

}

]

},

{

"tag":"970",

"ind1":" ",

"ind2":" ",

"subfields":[

{

"code":"l",

"data":"BB1"

},

{

"code":"f",

"data":"CD Spoken Word"

},

{

"code":"c",

"data":"col1"

},

{

"code":"q",

"data":"4"

},

{

"code":"w",

"data":"MP3 FICTION Baldacci, D"

}

]

}

]

}

}

]

}

### Return

|
|

{

PAPIErrorCode: 0,

ErrorMessage: "",

JobID: "GUID",

JobStatusID: 0,

JobStatusDescription: "",

ExternalID: "{B51F75AC-83AF-42A8-9920-21AA372E1ABF}" , // unique in B&T TS360

LineItemValidationErrors: [

{

ExternalLineItemID: "{0438E02C-CD66-4432-8FAE-669E58CC2413}",

Errors: [

{ PAPIErrorCode: -12108, ErrorMessage: "Line item segment branch/location 'ME2' not found." },

{ PAPIErrorCode: -12112, ErrorMessage: "Line item segment branch/location 'ME2' does not have any available funds." },

{ PAPIErrorCode: -12110, ErrorMessage: "Line item segment fund 'CD Spoken Word' not found for branch/location 'ME2'." },

{ PAPIErrorCode: -12113, ErrorMessage: "Line item segment collection 'Col1' not found." },

]

}

]

}

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0