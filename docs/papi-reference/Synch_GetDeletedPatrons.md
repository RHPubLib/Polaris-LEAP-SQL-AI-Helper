# Synch_GetDeletedPatrons

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetDeletedPatrons.htm_

You are here:

## Synch_GetDeletedPatrons

This method returns a list of patron records that have been deleted since a specified date and time. The return value includes both the patron ID and barcode. If the library does not retain deleted records, you cannot use this method.

**Important: **This method provides a list of patron records that have been deleted in the Polaris ILS. The method has a date and time parameter. If the time element is not specified, midnight of the day specified is assumed. It returns a generic GetBarcodeAndPatronIDResult XML structure (see below). A call to AuthenticateStaffUser is required before calling any protected method.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/patrons/deleted?deletedate={deletedate}
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

deletedate

|

YYYY-MM-DDTHH:MM:SS

|

Yes

|

Start date and time (records that have been deleted since this date/time)

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

PatronAndBarcodeIDRows

|

List of patron record IDs and barcodes

|
|

PatronAndBarcodeIDRow

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

The patron’s barcode (if any)

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/patrons/deleted?deletedate=12/2/2011 13:00:00

### Return

|
|

HTTP/1.1 200 OK

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