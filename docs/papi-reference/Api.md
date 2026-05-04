# Api

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Api.htm_

You are here:

## Api

Returns PAPI version information.

|
|  
| GET
| /api
|  

### Authorization required?

No

### HTTP Response Codes

The following HTTP Codes are returned:

|
|

Number

|

Description/Notes

|
| 200
|

Success; service is running

|
| 404
| Not found; service is not running

### PAPI Error Codes

|
|

Values

|

Description/Notes

|
| 0
|

Success; this code is followed by the version information for PAPI.

|
| -1
| Failure

### Example

|
| http://localhost/PAPIService/api

### Response - Healthy

|
|

{

"status": "Healthy",

"totalDuration": "00:00:00.0102442",

"entries": {

"API": {

"data": {

"PAPIService": {

"version": "8.0.64721.0",

"major": 8,

"minor": 0,

"build": 64721,

"revision": 0

}

},

"duration": "00:00:00.0003873",

"status": "Healthy",

"tags": []

},

"DatabaseServer": {

"data": {

"Database": {

"version": "8.0.64721.0"

}

},

"duration": "00:00:00.0101004",

"status": "Healthy",

"tags": []

}

}

}

### Response - Unhealthy

|
|

{

"status": "Unhealthy",

"totalDuration": "00:00:00.1201814",

"entries": {

"API": {

"data": {

"PAPIService": {

"version": "8.0.10.0",

"major": 8,

"minor": 0,

"build": 10,

"revision": 0

}

},

"duration": "00:00:00.0018147",

"status": "Healthy",

"tags": []

},

"DatabaseServer": {

"data": {

 

},

"description": "Login failed for user 'polaris'.",

"duration": "00:00:00.1197896",

"exception": "Login failed for user 'polaris'.",

"status": "Unhealthy",

"tags": []

}

}

}

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0