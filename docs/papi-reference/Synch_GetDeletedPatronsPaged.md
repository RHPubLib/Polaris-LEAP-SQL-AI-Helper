# Synch_GetDeletedPatronsPaged

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetDeletedPatronsPaged.htm_

You are here:

## Synch_GetDeletedPatronsPaged

This method returns a list of patron record IDs for records that have been deleted since a specified date and time. The paged method allows the retrieval of the ID list in smaller packets. If the library does not retain deleted records, you cannot use this method.

A date, last record ID, and number of records to return must be specified. When retrieving the first set of records, the "lastid" of 0 forces the process to start at the beginning of the list. When retrieving subsequent records, the "lastid" value is set to the last retrieved record ID.

**Important: **This method provides a list of patron records that have been deleted in the Polaris ILS. The method has a date and time parameter. If the time element is not specified, midnight of the day specified is assumed. It returns a generic GetBarcodeAndPatronIDResult XML structure (see below).

Use the lastid parameter to specify the starting point in the 'paged' list. Use 0 to start at the beginning. Use the nrecs parameter to specify the number of records to return.

A call to AuthenticateStaffUser is required before calling any protected method.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/patrons/deleted/paged?deletedate=
1/1/2017&lastid=0&nrecs=10
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

|
| lastid
| Use 0 when starting the retrieval process, otherwise, use the last retrieved ID
| No
|  

|
| nrecs
| Number of records to return

| Yes
|  

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

https://[HOSTNAME]/PAPISevice/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/patrons/deleted/paged?deletedate=1/1/2017&lastid=0&nrecs=10

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