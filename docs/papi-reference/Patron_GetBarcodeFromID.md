# Patron_GetBarcodeFromID

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Patron_GetBarcodeFromID.htm_

You are here:

## Patron_GetBarcodeFromID

This method derives a patron barcode from a patron ID. The return value includes both the patron ID and barcode.

**Important: **The barcode node of the return XML document may be empty. This may indicate one of the following conditions:

- The patron record has been deleted.
- The patron ID does not exist in the Polaris Database.
- The patron does not have a barcode assigned.
- This method accepts only one patron ID at a time.
- This method returns a generic GetBarcodeAndPatronIDResult XML structure (see below).

A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/patron/barcode?patronid={PatronID}
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

Value

|

Required

|

Description/Notes

|
|

PatronID

|

Integer

|

Yes

|

ID of patron

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

BarcodeAndPatronIDRows

|

List of Patron ID’s and barcodes

|
|

BarcodeAndPatronIDRow

|

Container for data

|
|

PatronID

|

The PatronID passed in by the user

|
|

Barcode

|

The patrons barcode (if any)

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6T
QHPGsy1tlZPr/patron/barcode?patronid=15

### Return

|
|

<GetBarcodeAndPatronIDResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<BarcodeAndPatronIDRows>

<BarcodeAndPatronIDRow>

<PatronID>15</PatronID>

<Barcode>1000200000395</Barcode>

</BarcodeAndPatronIDRow>

</BarcodeAndPatronIDRows>

</GetBarcodeAndPatronIDResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0