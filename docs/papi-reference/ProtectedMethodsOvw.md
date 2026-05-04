# PAPI Protected Methods

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/ProtectedMethodsOvw.htm_

You are here:

# PAPI Protected Methods

The PAPI Service supports protected methods. These are functions that can be performed by a staff member and not a patron. The staff member must authenticate with the PAPI service using the AuthenticateStaffUser method over a secure connection. Domain account information is exchanged and verified only once. If authentication is successful, the user is provided an AccessToken and AccessSecret which users can use for the remainder of their operations. SA_GetValueByOrg, below, is an example of how to use this authentication mechanism. A PAPI Processing job runs at 5:30 a.m. to delete expired authentication tokens. The job calls the PAPI_DeleteExpiredAuthTokens database stored procedure which checks the PAPIStaffAuthentication table’s AuthenticationExpDate column.

### Using Protected Methods

Once you have authenticated using the AuthenticateStaffUser method, you can use the protected methods. The access token and access secret returned by the AuthenticateStaffUser method are required for all protected calls. The access token is valid for 24 hours. All protected methods contain the access token in the URI. When creating the authentication signature, the append the AccessSecret to the data being hashed.

**Example:**

**[HTTP Method][URI][HTTP Date][Access Secret]**

Note that AuthenticateStaffUser does not require the “AccessSecret” when building the signature.

**Example calling a protected method:**

SA_GetValueByOrg

|
|

https://[hostname]/PAPIService/REST/protected/v1/1033/100/1/[AccessToken]/
organization/1/sysadmin/attribute/ORGPHONE1

HTTP Verb: GET

Authorization Required: Yes

Header:

|
|

Date: Sat, 14 May 2011 22:23:32 GMT

Authorization: PWS polarisdev:ZasTURsRdlEHeKgdA1MGXROUxTI=

Content-Type: text/xml

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0