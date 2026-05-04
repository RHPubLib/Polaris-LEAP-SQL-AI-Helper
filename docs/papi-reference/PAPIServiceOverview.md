# Polaris API - Overview

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceOverview.htm_

You are here:

# Polaris API - Overview

The Polaris REST Application Programming Interface (PAPI) is a web-based service comprised of a set of URIs that return data or perform actions on the Polaris application database. Method calls are made over TCP connections by sending HTTP GET, PUT, POST and DELETE requests. Nearly any computer language can be used to communicate over HTTP with the REST server. This document details the REST API methods, including the URIs, HTTP verbs, request headers, and request bodies required to execute Polaris functionality.

**See Also:**

- Setup

- Configuration

- PAPI and Swagger

- PAPI Web Service Authorization

- Application IDs

- HTTP Method

- PAPI Web Service Authorization - Sample Code

- Using PAPI with SSL

- HTTP Request Header

- Using Public Methods as an Authenticated Staff User

- PAPI Error Codes

- Material Format Types

- General URI Parameters

## Setup

**You must have the following to start using PAPI**:

-

**Polaris API Service (Public)** license is required. Innovative Support creates your license.

-

You can create a staff user account using Polaris System Administration (web-based).

-

You can create a Patron account using the staff client, Leap, or PowerPAC.

-

To use protected endpoints in PAPI, you need a Polaris staff user:

-

domain

-

name

-

password

-

To use Patron endpoints, you need the patron's:

-

barcode or username

-

password

**Note**:
If you see a 401 "Unauthorized" error, one of the following is true:
- Your API call has invalid HTTP authorization header data (for example, the PAPI access ID does not exist, or the signature is not valid).
- You do not have permission to access the endpoint. The library controls access to PAPI endpoints via access keys. Contact the library's technical staff to request access.

## Configuration

The appsettings.json file contains all of the configuration settings for PAPI. Do not make modifications to the settings in this file. Instead, to customize settings, create a new file called appsettings.user.json and add the changes. You can use the file called "appsettings.user.template.json" as a template for your appsettings.user.json file. It contains the correct structure for making customizations to the configuration file.

#### **Sample appsettings.user.json File:**

|
|

{

"Serilog": {

"MinimumLevel": "Error"

},

"Polaris": {

"ExternalHostname": "",

"SwaggerEnabled": false,

"AuthenticationLevel": "ALL",

"AuthenticationRemoteEnabled": false,

"JSONDateFormat": "Microsoft",

"SecurityMode": "Transport",

"KeyedHashAlgorithm": "HMACSHA1"

}

}

### Common Settings

The following settings are supported in the appsettings.user.json file. Unless otherwise specified in the table below, enter all settings in lowercase:

|
|

Key

|

Values

|
|

MinimumLevel (Serilog)

|

Specify the minimum threshold for a log event.

DEBUG - All general, debug and error messages

INFORMATION - All general and error messages

ERROR - All error messages

|
|

ExternalHostname

|

Specify override if the external URI request host name is different from the local domain name. Setting this option affects how the PAPI hash is calculated.

Example: Incoming request uses papiserver.mylibrary.org, server’s local name is papi.local.org

|
| SwaggerEnabled
|

true - Allow access to the Swagger UI.

false - Disable access to the Swagger UI (default).

|
| AuthenticationLevel
|

ALL - Require authentication for all API calls (default).

PATRON
- Require authentication for Patron-related API calls.

NONE - Authentication is not required (debug purposes only).

|
| AuthenticationRemoteEnabled
|

true - The database server completes the all staff-member authentication (i.e., when PAPI is running in a DMZ).

false - The server running PAPI performs the authentication.

|
| JSONDateFormat
|

ISO - Requests using a JSON type will return dates formatted as: `"2022-01-04T14:58:32-0400"`

Microsoft - Requests using a JSON type will return dates formatted as: `"/Date(1642625411380-0500)/"`

|
| SecurityMode
|

Transport - Support HTTPS only.

None - Support HTTP and HTTPS.

For more information on these settings, see Using PAPI with SSL.

|
| KeyedHashAlgorithm
|

HMACSHA1 - Select to compute a hash-based message authentication code (HMAC) by using the SHA1 hash function.

HMACSHA256 - Select to compute a hash-based message authentication code (HMAC) by using the SHA256 hash function.

Note: If you select HMACSHA256, all third parties that connect to your instance of PAPI also must use HMACSHA256.

## PAPI and Swagger

Swagger is an open-source framework for REST APIs. Effective as of Polaris 5.2, the Polaris API has a Swagger endpoint that provides code and documentation to Polaris customers and third-party vendors who use the Polaris API. For more information about Swagger, go to **http://swagger.io/**.

**Note**:
By default, the Swagger endpoint is disabled. To use Swagger, you must update the SwaggerEnabled value in appsettings.user.json from **false** to **true** and restart the PAPI IIS Application Pool.

The Swagger URL uses the following URL format: **https://<hostname>/PAPIService/swagger/index.html**.

Replace <hostname> with the host name of your library's server. For example:

**https://midlib.polarislibrary.com/PAPIService/swagger/index.html**

## PAPI Web Service Authorization

Secure functions will check HTTP header for valid Authorization element.

Authorization - **PWS [PAPIAccessID]:[Signature]**

-

"**PWS**" must be in caps

-

No space before or after "**:**"

-

"**[PAPIAccessID]**" - Assigned by Polaris

-

"**[Signature]**" - The signature is the following, encoded with SHA1 UTF-8:**
[HTTPMethod][URI][Date][PatronPassword]**

**Note**:

Although **[PatronPassword]** is supported for constructing the authorization signature, we recommend that you use the **AuthenticatePatron** method to retrieve an **AccessSecret**. You can then use the **AccessSecret** instead of the patron’s password. For more information, see Using Public Methods as an Authenticated Staff User.
Use Patron Password only when accessing patron-specific methods.

### Application IDs

{Version}/{LangID}/{**AppID**}/{OrgID}

Unless otherwise specified, customers and third-party developers should use an ApplicationID value of 100 when making calls to PAPI.

### HTTP Method

The HTTP Method uses a Uniform Resource Identifier (URI) to identify an object, resource or concept in Polaris. A URI is composed of the following parts:

**scheme:[//authority]path[?query][#fragment]**

Construct the URI as you would expect the server to receive it:

**Example:**

|
| search/bibs/keyword/au?q=roald+dahl&sort=PDTI&limit=TOM=dvd

**not**

|
| search/bibs/keyword/au?q=roald**%20**dahl&sort=PDTI&limit=TOM**%3D**dvd

### Date

**Note**:
The date must be within +/- 30 minutes of the current time or the request will fail.

-

Use HTTP Date format (RFC1123):

ddd, dd MMM yyyy HH:mm:ss GMT

**Example:
**Wed, 17 Oct 2012 22:23:32 GMT

-
If you cannot set the date in the HTTP header, pass the following name:value pair into the header:

**PolarisDate: ddd, dd MMM yyyy HH:mm:ss GMT****PolarisDate: Wed, 17 Oct 2012 22:23:32 GMT**

**Example:
**Authorization: PWS polarisdev:8TD4Nfu+cxdUZPwqlQMVBuDOvMw=

Private key to create HMAC is assigned by Polaris

Current {version} is **v1**

### General URI Parameters

|
|

Name

|

Required

|

Description/Notes

|
|

app-ID

|

Yes

|

Calling application (product) ID (see Application IDs)

|
|

org-ID

|

Yes

|

Organization identifier. This value must be system-level (1) or a branch-level organization identifier.

|
|

bib-ID

|

Yes

|

Record identifier

|
|

lang-ID

|

Yes

|

Language identifier of the Label. Possible values include:

1033 - English
1042 - Korean
1049 - Russian
1065 - Farsi
1066 - Vietnamese
1141 - Hawaiian
2052 - Chinese
3082 - Spanish
3084 - French
12289 - Arabic
15372 - Haitian Creole

### Sample Code

To build the string (hash):

-
Build the data by concatenating the HTTP method (GET, PUT, POST, DELETE), URI, Date, and Patron Password (if required). The Access Key is the private key assigned by Polaris. Pass the resulting routine.

-
The routine returns a hash to the caller similar to this example:
**8TD4Nfu+cxdUZPwqlQMVBuDOvMw=**

-
This hash is combined with the PAPI Access Key ID and used in the HTTP header, similar to the following example:
**Authorization: PWS SOPAC1:8TD4Nfu+cxdUZPwqlQMVBuDOvMw=**

#### **Sample Android-based Java class:**

**Note**:
Anywhere the HMACSHA256 algorithm appears as a choice in the code, you can choose to use it. If you use the HMACSHA256 algorithm, all third parties that connect to your instance of PAPI also must use HMACSHA256.

|
|

package Polaris.CheckMyLibrary;
import java.security.InvalidKeyException;
import java.security.NoSuchAlgorithmException;
import java.security.SignatureException;
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;
import android.util.Base64;
public class PAPIHash {
    private static final String HMAC_SHA1_ALGORITHM = "HmacSHA1";
    public String GetPAPIHash(

       String strAccessKey, String strHTTPMethod, String strURI, String strHTTPDate, String strPatronPassword) {

       String result = "";

// Get an hmac_sha1 or hmac_sha256 key from the raw key bytes

       byte[] secretBytes = strAccessKey.getBytes();
       SecretKeySpec signingKey = new SecretKeySpec(secretBytes, HMAC_SHA1_ALGORITHM);

// Get an hmac_sha1 or hmac_sha256 Mac instance and initialize with the signing key

       try { Mac mac; mac = Mac.getInstance(HMAC_SHA1_ALGORITHM);
       mac.init(signingKey);

       String data = "";

       if (strPatronPassword.length() & gt; 0) data = strHTTPMethod + strURI + strHTTPDate + strPatronPassword;
       else

           data = strHTTPMethod + strURI + strHTTPDate;

// Compute the hmac on input data bytes

      byte[] rawHmac = mac.doFinal(data.getBytes());

// Convert raw bytes to Hex result = Base64.encodeToString(rawHmac, 0);

       } catch (NoSuchAlgorithmException e1) {

// TODO Auto-generated catch block

       e1.printStackTrace(); }
catch (InvalidKeyException e) {

// TODO Auto-generated catch block

       e.printStackTrace();
       }

   return result;

    }

}

#### **Sample C# Method:**

|
|

public string GetPAPIHash(string strAccessKey, string strHTTPMethod, string strURI, string strHTTPDate, string strPatronPassword)

{
byte[] secretBytes = UTF8Encoding.UTF8.GetBytes(strAccessKey);
HMACSHA1 hmac = new HMACSHA1(secretBytes);

**// Computed hash is based on different elements defined by URI**

 byte[] dataBytes = null;
  if (strPatronPassword.Length > 0)
         dataBytes = UTF8Encoding.UTF8.GetBytes(strHTTPMethod +
                     strURI + strHTTPDate + strPatronPassword);
           else
         dataBytes = UTF8Encoding.UTF8.GetBytes(strHTTPMethod +
                     strURI + strHTTPDate);
      byte[] computedHash = hmac.ComputeHash(dataBytes);
     string computedHashString = Convert.ToBase64String(computedHash);
  return computedHashString;
}

## Using PAPI with SSL

All protected method calls require SSL using HTTPS. This is to ensure that all sensitive data, such as domain account information, is encrypted. If a protected method is called without an HTTPS connection, a “403 - Forbidden” error is returned.

You can configure the PAPI to support the following:

- HTTPS only - Required for all methods

- HTTP and HTTPS - HTTPS is required for all protected methods, but public methods can be accessed using HTTP or HTTPS

By default, PAPI is set to require HTTPS.

**To set these options **:

-

Go to the appsettings.user.json file located in C:\Program Files\Polaris\[version]\PAPIService

-

Set the SecurityMode as follows:

- None = Support HTTP and HTTPS

- Transport = Support HTTPS only

**Important:
**When SecurityMode is set to Transport, ALL PAPI method calls (public and protected) must use HTTPS.

### Support for XML and JSON Data Exchange Formats

The Polaris API supports both XML and JSON data exchange formats. The caller may choose to use JSON by specifying the content type in the HTTP request header. XML is the default.

## HTTP Request Header

To specify JSON, you can add the following to the HTTP request header:

Content-Type: application/json

Accept: application/json

To specify XML (the default), you can add the following to the HTTP request header:

Content-Type: application/xml

Accept: application/xml

**Note:
**The HTTP request header must provide the “Content-Length” when using the request body.

### **JSON and DateTime Fields**

All DateTime fields are nullable. The default is no longer MinValue.

We provide two date format options for JSON request/response bodies.

-

When JSONDateFormat is set to "Microsoft", the resulting data is formatted as:

`"/Date(1642625411380-0500)/"`

-

When JSONDateFormat is set to "ISO", the resulting data is formatted as:

`"2022-01-04T14:58:32-0400"`

### **JSON - GetBib **

Example HTTP data returned by a call to GetBib using JSON as the content type:

|
|

HTTP/1.1 200 OK
Cache-Control: private
Content-Length: 1480
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/7.5
X-AspNet-Version: 4.0.30319
X-Powered-By: ASP.NET
Date: Fri, 07 Jan 2011 19:06:54 GMT

"PAPIErrorCode": 0,

"ErrorMessage": "",

"BibGetRows": [{

"ElementID": 35,

"Occurence": 1,

"Label": "Title:",

"Value": "The wind in the willows \/ illustrated by Ernest H. Shepard.",

"Alternate": false

}, {

"ElementID": 18,

"Occurence": 1,

"Label": "Author:",

"Value": "Grahame, Kenneth, 1859-1932.",

"Alternate": false

}, {

"ElementID": 2,

"Occurence": 1,

"Label": "Publisher, Date:",

"Value": "New York : Scribner, 1961, c1933.",

"Alternate": false

}, {

"ElementID": 3,

"Occurence": 1,

"Label": "Description:",

"Value": "259 p. : illus. ; 21 cm.",

"Alternate": false

}, {

"ElementID": 17,

"Occurence": 1,

"Label": "Format:",

"Value": "Book",

"Alternate": false

}, {

"ElementID": 21,

"Occurence": 1,

"Label": "Other Author:",

"Value": "Shepard, Ernest H. (Ernest Howard), 1879-1976.",

"Alternate": false

}, {

"ElementID": 28,

"Occurence": 1,

"Label": "Notes:",

"Value": "\"Atheneum Books for Young Readers\"",

"Alternate": false

}, {

"ElementID": 28,

"Occurence": 2,

"Label": "Notes:",

"Value": "The adventures of four amiable animals, Rat, Toad, Mole and Badger, along a river in the English countryside.",

"Alternate": false

}, {

"ElementID": 6,

"Occurence": 1,

"Label": "ISBN:",

"Value": "0684128195",

"Alternate": false

}, {

"ElementID": 7,

"Occurence": 1,

"Label": "System Availability:",

"Value": "4",

"Alternate": false

}, {

"ElementID": 8,

"Occurence": 1,

"Label": "Current Holds:",

"Value": "0",

"Alternate": false

}, {

"ElementID": 13,

"Occurence": 1,

"Label": "Call Number:",

"Value": "J Fict Gra",

"Alternate": false

}, {

"ElementID": 16,

"Occurence": 1,

"Label": "System Items Available:",

"Value": "3",

"Alternate": false

}

]

}

### **JSON - HoldRequestCreate**

Example HTTP request body when using the POST command with JSON:

|
|

{

"PatronID": 299377,

"BibID": "15593",

"ItemBarcode": "",

"VolumeNumber": "",

"Designation": "",

"PickupOrgID": "74",

"IsBorrowByMail": "0",

"PatronNotes": "",

"ActivationDate": "\/Date(1295352000000)\/",

"WorkstationID": "1",

"UserID": "1",

"RequestingOrgID": "74",

"TargetGUID": ""

}

### **JSON - ItemRenewAllForPatron**

Example HTTP request body when using the PUT command with JSON:

|
|

{

"Action":"renew",

"LogonBranchID":"74",

"LogonUserID":"1",

"LogonWorkstationID":"1",

"RenewData":{"IgnoreOverrideErrors":true}

}

### **JSON - PatronAccountPay**

Example HTTP request body when using the PUT command with JSON:

|
|

{

"TxnAmount":"2.95",

"PaymentMethodID":"11",

"FreeTextNote":"Paid through Polaris API"

}

### **Date Format when using JSON **

Because JSON does not have a standard way of describing dates, you must use one of the following formats:

-

ISO format - **"2011-01-18T07:00:00-0400"**

-

Microsoft format - **"\/Date(1295352000000)\/"**
The number represents the number of milliseconds since January 1st 1970 UTC.
**1295352000000** represents Tuesday, January 18, 2011 7:00:00 AM.

### XML Elements

The order of XML elements matters! (You will see reminders throughout this document.)

### Examples of SHA1 Encoding

**http://msdn.microsoft.com/en-us/library/dd203052.aspx**

**http://en.wikipedia.org/wiki/Sha1**

Example using **http://jssha.sourceforge.net/**

## Using Public Methods as an Authenticated Staff User

In some scenarios, as an authenticated staff user, you might want to call a public method that requires the patron’s password. Instead of looking up the patron’s password, you can build the authentication signature using the AccessSecret. Because the public method does not contain the AccessToken in the URI, you simply pass in a custom HTTP header field called X-PAPI-AccessToken. The PAPI Service will look for the X-PAPI-AccessToken header field and act accordingly.

**Note:**
This process might fail if a firewall or network device is configured to remove nonstandard HTTP header fields.

### SSL Requirements for Protected Methods

SSL must be used because domain account information is being passed to perform the initial account authentication.

You must enable SSL in the PAPI Service by changing the security mode to Transport.

**Important:**
Once you have set the security mode to Transport, all PAPI method calls (public and protected) must use HTTPS.

The certificate must be installed on the IIS website.

PAPI Service must contain binding on port 443 to the web server certificate.

### Development Tools - Fiddler2 (Freeware)

**http://www.fiddler2.com/fiddler2/**

## PAPI Error Codes

The following error codes are returned from the Polaris REST API.

|
|

Code

|

Reason

|
|

General

|
|

Any positive number

|

Represents either the count of rows returned or the number of rows affected by the procedure. See individual procedure definitions for details.

|
|

0

|

Success

|
|

-1

|

FAILURE - General

|
|

-2

|

Multiple errors. See returned rowset for list of errors.

|
|

-3

|

PARTIAL FAILURE - Multiple errors (but some items succeeded). See returned rowset for list of errors.

|
|

-4

|

FAILURE - ERMS error

|
| -5
| Failure. Database error occurred

|
| -6
| Failure. Invalid parameter

|
| -9
| SQL timeout

|
| -10
| Failure. ID does not exist

|
| -11
| Validation_Errors

|
|

Bibliographic Errors - [1000-1499]

|
|

-1000

|

Invalid BibliographicRecordID specified

|
| -1001
| Bibliographic import profile name not found

|
|

MARC Errors - [1500-1999]

|
| -1500
| MARC not supplied

|
| -1501
| MARC Leader not supplied

|
| -1502
| MARC control field not supplied

|
| -1503
| MARC control field 008 not supplied

|
| -1504
| MARC data fields not supplied

|
| -1505
| MARC data field title not supplied

|
| -1506
| MARC data field price not supplied

|
| -1507
| MARC XML collection is missing or empty

|
| -1508
| MARC XML collection record count exceeds configured maximum

|
|

Item/Holdings Errors - [2000-2999]

|
|

-2000

|

Invalid ItemRecordID specified

|
|

-2001

|

Invalid barcode specified

|
|

-2002

|

Duplicate barcode specified

|
| -2005
| Item status ID is not 'Claim Missing Parts'

|
| -2006
| Item missing parts patron not found.

|
| -2007
| Patron must be the last used patron for check in with charge for missing parts.

|
| -2008
| The patron has already been billed for this item. To check-in the item, use normal check-in.

|
| -2009
| According to the settings in the patron account, this user is excluded from billing.

|
| -2010
| According to the settings in the patron account, this user is excluded from billing.

|
| -2011
| Quick-circ items cannot be checked in for in-house use.

|
| -2012
| Quick-circ items cannot be checked in for inventory.

|
|

Patron Errors - [-201, -221; -501; 3000-3999]

|
| -201
| Failed to insert entry in addresses table

|
| -221
| Failed to insert entry in PostalCodes table

|
| -222
| Invalid PostalCodeLength

|
| -223
| Invalid PostalCodeFormat

|
| -501
| Patron personal information change is not allowed

|
| -3000
| Patron does not exist

|
| -3001
| Failed to insert entry in Patrons table

|
| -3400
| Failed to insert entry in Patronaddresses table

|
| -3401
| Invalid AddressType

|
|

-3500

|

Country code does not exist

|
|

-3501

|

Patron branch is not defined

|
|

-3502

|

Patron branch is not a valid branch

|
|

-3503

|

Last name is not defined

|
|

-3504

|

First name is not defined

|
|

-3505

|

Barcode is already used for another patron

|
|

-3506

|

Transaction branch is not defined

|
|

-3507

|

Transaction user is not defined

|
|

-3508

|

Transaction workstation is not defined

|
|

-3509

|

Passwords do not match

|
|

-3510

|

Postal code problems - mismatch city, state, county

|
|

-3511

|

Postal code problems - mismatch city, state

|
|

-3512

|

Postal code problems - mismatch city, county

|
|

-3513

|

Postal code problems - mismatch state, county

|
|

-3514

|

Postal code problems - mismatch county

|
|

-3515

|

Postal code problems - mismatch state

|
|

-3516

|

Postal code problems - mismatch city

|
|

-3517

|

Postal code problems - postal code not found

|
|

-3518

|

Invalid Email address

|
|

-3519

|

Invalid DeliveryMethod Value (No Address for Patron)

|
|

-3520

|

Invalid DeliveryMethod Value (No Email Address for Patron)

|
|

-3521

|

Invalid DeliveryMethod Value (No PhoneVoice1 for Patron)

|
|

-3522

|

Invalid DeliveryMethod Value (No PhoneVoice2 for Patron)

|
|

-3523

|

Invalid DeliveryMethod Value (No PhoneVoice3 for Patron)

|
|

-3524

|

Invalid DeliveryMethod Value (No PhoneFax for Patron)

|
|

-3525

|

Invalid DeliveryMethod Value

|
|

-3526

|

Invalid EmailFormat Value

|
|

-3527

|

Invalid ReadingList Value

|
|

-3528

|

Duplicate name

|
|

-3529

|

Duplicate username

|
|

-3530

|

Failed to insert entry in Patron Registration table

|
| -3531
| Patron delivery notices address not defined

|
| -3532
| Invalid PhoneVoice1 value

|
| -3533
| Invalid Password format

|
| -3534
| Invalid Password length

|
| -3535
| Patron password change is not allowed

|
| -3536
| Invalid GenderID for the Registered Branch

|
| -3537
| Invalid LegalName Configuration

|
| -3540
| Invalid Birthdate

|
| -3541
| Invalid NameLast Length

|
| -3542
| Invalid NameFirst Length

|
| -3543
| Invalid NameMiddle Length

|
| -3544
| Invalid LegalNameLast Length

|
| -3545
| Invalid LegalNameFirst Length

|
| -3546
| Invalid LegalNameMiddle Length

|
| -3547
| Invalid Username Length

|
| -3548
| Invalid Barcode Length

|
| -3550
| Invalid Patron Barcode

|
| -3551
| Patron Address Not Defined

|
| -3552
| Patron Password Not Defined

|
| -3553
| Patron Address Street One Invalid

|
| -3554
| Patron Address Postal Code Invalid

|
| -3555
| Patron Address City Invalid

|
| -3556
| Patron Address State Invalid

|
| -3557
| Patron Username Format Invalid

|
| -3558
| Patron Address Country Not Defined

|
| -3559
| Patron Delivery Notices Address Not Defined

|
| -3560
| Patron Address Street Two Invalid

|
| -3561
| Patron Address Street Three Invalid

|
| -3562
| Patron Address Free Text Label Invalid

|
|

-3600

|

Charge transaction does not exist

|
|

-3601

|

Charge transaction for this patron does not exist

|
|

-3602

|

Payment method for payment is invalid

|
|

-3603

|

Invalid amount is being paid

|
|

-3604

|

Invalid transaction type being paid

|
|

-3605

|

General patron account database error

|
|

-3606

|

Payment transaction does not exist

|
|

-3607

|

Payment transaction for this patron does not exist

|
|

-3608

|

Payment transaction cannot be voided because another action taken on payment

|
|

-3610

|

Payment amount is more than the sum of the charges

|
| -3612
| Invalid PatronCodeID

|
| -3613
| Invalid PhoneVoice2

|
| -3614
| Invalid PhoneVoice3

|
| -3615
| Invalid Alt Email Address

|
| -3616
| Invalid TXTPhoneNumber

|
| -3617
| Invalid PhoneCarrier

|
| -3619
| Invalid DeliveryMethod No Phone

|
| -3620
| Invalid Email Address for EReceipt

|
| -3621
| Patron Is Secure

|
| -3622
| Invalid RequestPickupBranchID

|
| -3623
| Invalid User1

|
| -3624
| Invalid User2

|
| -3625
| Invalid User3

|
| -3626
| Invalid User4

|
| -3627
| Invalid User5

|
| -3628
| Invalid LanguageID

|
| -3629
| Invalid FormerID

|
| -3630
| Invalid StatisticalClassID for the Registered Branch

|
| -3634
| Patron Required Fields Missing

|
| -3635
| Invalid Patron Address Country

|
| -3637
| Patron record is secured

|
|

Hold Request Errors - [4000-4999]

|
|

-4000

|

Invalid application ID supplied

|
|

-4001

|

Invalid patron ID supplied

|
|

-4002

|

Invalid workstation ID supplied

|
|

-4003

|

Invalid request ID supplied

|
|

-4004

|

Invalid requesting org ID supplied

|
|

-4005

|

Invalid patron barcode

|
|

-4006

|

Invalid bibliographic record ID supplied

|
|

-4007

|

Invalid pickup org ID supplied

|
| -4016
| Cannot change pickup branch for request in statusID

|
|

-4019

|

Hold Pickup Area SA disabled

|
| -4020
| Hold Pickup Area Invalid for pickup branch

|
| -4021
| Hold Pickup Area ID Invalid

|
| -4022
| Hold Pickup Area not enabled for the pickup branch

|
| -4023
| Hold Pickup Area already set

|
| -4100
| Invalid request GUID supplied

|
|

-4101

|

Invalid txn group qualifier supplied

|
|

-4102

|

Invalid txn qualifier supplied

|
|

-4103

|

Invalid answer supplied

|
|

-4104

|

Invalid state supplied

|
|

-4201

|

Invalid request ID supplied

|
|

-4202

|

Invalid current org ID supplied

|
|

-4203

|

Cancel prevented for hold requests with status of Held

|
| -4204
| Cancel prevented for hold request with status of Unclaimed

|
| -4205
| Cancel prevented for hold request with a status of Canceled

|
| -4206
| Cancel prevented for hold request with a status of Expired

|
| -4207
| Cancel prevented for hold request with a status of Out to Patron

|
| -4208
| Cancel prevented for hold request with a status of Shipped

|
|

-4300

|

No requests available to cancel

|
|

-4400

|

Invalid Application date supplied

|
|

-4401

|

Application date must be greater than or equal to today's date

|
|

-4402

|

Application date must be earlier than 2 years from today

|
|

-4403

|

Invalid pickup branch assigned to hold request

|
|

-4404

|

Error occurred loading SA "days to expire"

|
|

-4405

|

Request must have a status of Active, Inactive or Pending

|
|

-4406

|

No requests available to suspend

|
|

-4407

|

Request status invalid for this process

|
|

-4408

|

Invalid request status change requested

|
|

-4409

|

Invalid hold user not supplied reason

|
|

-4410

|

This is the only item available for hold

|
|

-4411

|

No other items at other branches are available to fill this hold

|
|

Organization Errors - [5000-5999]

|
|

-5000

|

Invalid OrganizationID specified

|
|

Circulation Errors - [6000-6299]

|
|

-6000

|

Invalid loan unit supplied

|
|

-6001

|

ItemCheckout record does not exist

|
| -6101
|

Patron block

|
|

-6103

|

Item record status is not Final

|
|

-6104

|

Item status is Returned-ILL

|
|

-6110

|

Item Status is Non-Circulating

|
|

-6112

|

Item block

|
|

-6113

|

Item status is In-Transit

|
|

-6115

|

Invalid item circulation period

|
|

-6116

|

Item on-the-fly

|
|

-6117

|

Multiple course reserves

|
|

-6118

|

Overdue fine

|
|

-6119

|

Renewal block

|
|

Checkin Errors - [6300-6999]

|
| -6301
| Checkin Failed

|
| -6302
| Item with specified material type cannot be self-check-in

|
| -6303
| Self check-in is not allowed for resolving lost or billed items.

|
| -6304
| Item check-in status is blocked

|
|

Course Reserve Errors - [7000-7999]

|
|

-7000

|

Invalid CourseReserveID specified

|
|

PolarisUser Errors - [8000-8999]

|
|

-8000

|

Invalid PolarisUserID specified

|
| -8001
| Polaris user is not permitted

|
| -8002
| StaffUser_NotSupplied

|
| -8003
| StaffUser_NotFound

|
| -8004
| StaffUser_Account_Disabled

|
|

Workstation Errors - [9000-9999]

|
|

-9000

|

Invalid WorkstationID specified

|
| Record Set Errors - [11000-11999]

|
| -11000
| Supplied recordSetID is not of type patron

|
| -11001
| RecordSetID does not exist

|
| Acquisitions Errors - [12000-12999]

|
| -12100
| Acquisitions supplier record name not supplied

|
| -12101
| Acquisitions supplier record name not found

|
| -12102
| Acquisitions line items not supplied

|
| -12103
| Acquisitions line item segments not supplied

|
| -12104
| Acquisitions total copies not supplied

|
| -12105
| Acquisitions line item copies not supplied

|
| -12106
| Acquisitions line item segment copies not supplied

|
| -12107
| Acquisitions copy counts do not match

|
| -12108
| Acquisitions branch location not found

|
| -12109
| Acquisitions branch location not a branch

|
| -12110
| Acquisitions fund not found

|
| -12111
| Acquisitions fund not open

|
| -12112
| Acquisitions fund none available

|
| -12113
| Acquisitions collection not found

|
| -12114
| Acquisitions collection not assigned to branch location

|
| -12115
| Acquisitions order type not firm order

|
| -12116
| Acquisitions payment method not purchase

|
| -12117
| Acquisitions line items validation errors found

|
| -12118
| Acquisitions fund multiple entries found

|
| -12119
| Acquisitions total of copies does not match

|
| -12120
| Acquisitions login is Organization level, not Branch level

|
| -12121
| Acquisitions branch location is not allowed

|
| -12122
| Acquisitions create Purchase Order not permitted at this branch

|
| -12123
| Acquisitions ordered at location not supplied

|
| -12124
| Acquisitions ordered at location not found

|
| -12125
| Acquisitions ordered at location not a branch

|
| -12126
| Acquisitions PO number not supplied

|
| -12127
| Acquisitions PO number exists

|
| -12128
| Acquisitions MARC validation errors found

|
| -12129
| Acquisitions line item segments duplicate

|
| -12130
| Acquisitions supplier record name duplicate

|
| -12131
| Acquisitions item template match not found

|
| -12133
| Import profile - PAPI PO import profile, not found.

## Material Format Types

The following IDs are associated with the FormatID columns in several of the returned rowsets.

|
|

ID

Searchcode
|

Format Description

|
|

1

| bks
|

Book

|
|

2

| mus
|

Printed or Manuscript Music

|
|

3

| cmt
|

Cartographic Material

|
|

4

| vis
|

Visual Materials

|
|

5

| rec
|

Sound Recording

|
|

6

| elr
|

Electronic Resources

|
|

7

| mix
|

Archival Mixed Materials

|
|

8

| ser
|

Serial

|
|

9

| pmu
|

Printed Music

|
|

10

| mmu
|

Manuscript Music

|
|

11

| pmc
|

Printed Cartographic Material

|
|

12

| mcm
|

Manuscript Cartographic Material

|
|

13

| map
|

Map

|
|

14

| glb
|

Globe

|
|

15

| mss
|

Manuscript Material

|
|

16

| pgr
|

Projected Medium

|
|

17

| mot
|

Motion Picture

|
|

18

| vid
|

Video Recording

|
|

19

| ngr
|

Two Dimensional Non-projected Graphic

|
|

20

| art
|

Three Dimensional Object

|
|

21

| msr
|

Musical Sound Recording

|
|

22

| nsr
|

Nonmusical Sound Recording

|
|

23

| kit
|

Kit

|
|

24

| per
|

Periodical

|
|

25

| new
|

Newspaper

|
|

26

| mic
|

Microform

|
|

27

| lpt
|

Large Print

|
|

28

| brl
|

Braille

|
|

33

| dvd
|

DVD

|
|

34

| vcr
|

Videotape

|
|

35

| mcd
|

Music CD

|
|

36

| ebk
|

eBook

|
|

37

| abk
|

Audio Book

|
| 38
| dmc
| Digital Collection

|
| 39
| abs
| Abstract

|
| 40
| brd
| Blu-ray Disc

|
| 41
| aeb
| Eaudiobook

|
| 42
| bcd
| Book + CD

|
| 43
| bcs
| Book + Cassette

|
| 44
| vgm
| Video Game

|
| 45
| bdv
| Blu-ray + DVD

|
| 46
| bkv
| Book + DVD

|
| 47
| atl
| Atlas

|
| 48
| stm
| Streaming Music

|
| 49
| stv
| Streaming Video

|
| 50
| emg
| Emagazine

|
| 51
| vyl
| Vinyl

|
| 52
| abc
| Audio Book on CD

|
| 53
| abt
| Audio Book on Cassette

## General URI Parameters

|
|

Name

|

Required

|

Description/Notes

|
|

app-ID

|

Yes

|

Calling application (product) ID (see Application IDs)

|
|

org-ID

|

Yes

|

Organization identifier. This value must be system-level (1) or a branch-level organization identifier.

|
|

bib-ID

|

Yes

|

Record identifier

|
|

lang-ID

|

Yes

|

Language identifier of the label. Possible values include:

1033 - English
1042 - Korean
1049 - Russian
1065 - Farsi
1066 - Vietnamese
1141 - Hawaiian
2052 - Chinese
3082 - Spanish
3084 - French
12289 - Arabic
15372 - Haitian Creole

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0