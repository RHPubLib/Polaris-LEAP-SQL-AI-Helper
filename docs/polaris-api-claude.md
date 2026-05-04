# Polaris REST API (PAPI) — Claude Code Reference

Rochester Hills Public Library | Polaris 8.0  
Drop this file into CLAUDE.md (or include it) on any server that needs to call the Polaris ILS REST API.

---

## Overview

Polaris exposes a REST API called **PAPI** (Polaris Application Programming Interface). All endpoints share a common URL structure and use HMAC-SHA1 request signing for authentication. There is no OAuth, no JWT — just a shared AccessID + Secret and a per-request signature.

**Base URL pattern:**
```
https://{polaris-server}/PolarisAPI/REST/{scope}/v1/{LangID}/{AppID}/{OrgID}/{endpoint}
```

| Parameter | Description | Typical value |
|-----------|-------------|---------------|
| `polaris-server` | Hostname of Polaris ILS server | e.g. `polaris.rhpl.org` |
| `scope` | `public` for public API, `protected` for patron-authenticated calls, `staff` for staff-authenticated calls | `public` |
| `v1` | API version — always `v1` for Polaris 8.x | `v1` |
| `LangID` | Locale ID (LCID) | `1033` (English US) |
| `AppID` | Numeric application ID assigned by Polaris admin | e.g. `100` |
| `OrgID` | Organization (branch/system) ID | e.g. `3` for RHPL Main |

---

## Authentication

### CORRECTED 2026-05-02 — auth IS HMAC-SHA1 PWS signing

The Swagger UI dialog at https://catalog.rhpl.org/PAPIService/swagger/index.html shows three named "Basic auth" schemes (API/Patron/Staff), but **that's just the input form**. Under the hood the Swagger UI generates PWS HMAC-SHA1 signatures and sends them as `Authorization: PWS {AccessID}:{base64_signature}`. Confirmed by inspecting the actual curl command Swagger emits:

```
Authorization: PWS localpull:QopfYMlePv96PSI/9aandb+/Vl4=
PolarisDate: Sun, 03 May 2026 03:34:54 GMT
```

Notes:
- The header name is **`PolarisDate`**, not `Date` (Polaris-specific)
- Three identities are still relevant — but each has its own AccessID + Secret pair, not a Basic password:
  - **API** (`localpull`) — general API access
  - **Patron** — patron barcode + their PIN, for self-service ops
  - **Staff** — for admin ops; first POST `/REST/protected/v1/.../authenticator/staff` to get an `AccessToken`, then send it as `X-PAPI-AccessToken` on subsequent calls
- Public-scope endpoints typically need only API PWS auth
- Protected-scope endpoints additionally need the `X-PAPI-AccessToken` from staff auth

### HMAC-SHA1 PWS signing details

Every request must include:
1. An HTTP `Date` header in RFC 1123 format
2. An `Authorization` header with a PAPI signature

**Signature algorithm (HMAC-SHA1):**
```
message = HTTP_METHOD + "\n"
        + content_type + "\n"
        + date_string + "\n"
        + patron_password + "\n"    ← empty string "" for public methods
        + uri_lowercase
```

- Sign `message` with your **Secret Key** using HMAC-SHA1
- Base64-encode the raw digest
- Authorization header: `PWS {AccessID}:{base64_signature}`

**Python example — GET request:**
```python
import hmac, hashlib, base64, requests
from email.utils import formatdate

ACCESS_ID = "your_access_id"
SECRET_KEY = "your_secret_key"
BASE_URL   = "https://polaris.rhpl.org/PolarisAPI"

def papi_get(path, patron_password=""):
    """
    path: everything after /PolarisAPI, e.g. /REST/public/v1/1033/100/3/shelflocations
    """
    date_str = formatdate(usegmt=True)
    uri = path.lower()

    message = "GET\n\n" + date_str + "\n" + patron_password + "\n" + uri
    sig = base64.b64encode(
        hmac.new(SECRET_KEY.encode(), message.encode(), hashlib.sha1).digest()
    ).decode()

    headers = {
        "Date": date_str,
        "Authorization": f"PWS {ACCESS_ID}:{sig}",
        "Accept": "application/json",
    }
    return requests.get(BASE_URL + path, headers=headers)
```

**Python example — POST/PUT request:**
```python
import json

def papi_post(path, body_dict, patron_password=""):
    date_str = formatdate(usegmt=True)
    content_type = "application/json"
    uri = path.lower()
    body_json = json.dumps(body_dict)

    message = "POST\n" + content_type + "\n" + date_str + "\n" + patron_password + "\n" + uri
    sig = base64.b64encode(
        hmac.new(SECRET_KEY.encode(), message.encode(), hashlib.sha1).digest()
    ).decode()

    headers = {
        "Date": date_str,
        "Authorization": f"PWS {ACCESS_ID}:{sig}",
        "Content-Type": content_type,
        "Accept": "application/json",
    }
    return requests.post(BASE_URL + path, headers=headers, data=body_json)
```

### Critical signing rules
- The `uri` in the signature must be **lowercase** — case mismatch causes 403
- The `Date` header value must match exactly what was signed — reuse the same string
- For GET requests with no body, `content_type` in the signature is an **empty string** (no `\n` gap — just `"GET\n\n"`)
- For POST/PUT, content_type in signature must match the `Content-Type` header exactly

---

## Common Endpoints

### Shelf Locations
```
GET /REST/public/v1/{LangID}/{AppID}/{OrgID}/shelflocations
```
Returns all shelf location codes defined at the given OrgID.

```python
resp = papi_get("/REST/public/v1/1033/100/3/shelflocations")
locations = resp.json()["ShelfLocationGetRows"]
# Each row: { ShelfLocationID, Name, Abbreviation, ... }
```

### Item Availability
```
GET /REST/public/v1/{LangID}/{AppID}/{OrgID}/biblio/{BibID}/availability
```
Returns item availability for a bib record.

### Bib Search
```
GET /REST/public/v1/{LangID}/{AppID}/{OrgID}/search/bibs/keyword/{query}
```

### Patron Authentication (protected scope)
To make patron-authenticated calls, first authenticate:
```
POST /REST/public/v1/{LangID}/{AppID}/{OrgID}/patron/{barcode}
Body: { "Password": "patron_pin" }
```
Returns an `AccessToken` and `AccessSecret`. Use these for protected calls:
- Replace `public` with `protected` in the URL
- Pass patron's `AccessSecret` as `patron_password` in the signature

### Hold Request
```
POST /REST/protected/v1/{LangID}/{AppID}/{OrgID}/patron/{barcode}/holdrequest
```

### Patron Basic Data
```
GET /REST/protected/v1/{LangID}/{AppID}/{OrgID}/patron/{barcode}/basicdata
```

---

## RHPL-Specific Values

| Parameter | Value |
|-----------|-------|
| Polaris server | `polaris.rhpl.org` (internal) |
| LangID | `1033` |
| AppID | Check RHPL's Polaris admin or password manager |
| OrgID | `3` = Main Library, `1` = System-level |
| AccessID / Secret | In RHPL password manager under "Polaris PAPI credentials" |

**Branch OrgIDs:** 1=System, 2=District, 3=Main Library, 4=Bookmobile, 5=Drive-Up Window, 6=Kids' Bus, 7=Books by Mail, 8=Mini-Branch Avon on the Lake, 9=Mini-Branch Avon Tower, 10=Mini-Branch OPC, 11=Mini-Branch Danish Village, 12=Mini-Branch Bellbrook, 13=Mini-Branch Waltonwood

---

## Response Format

All responses are JSON (when `Accept: application/json` is sent) or XML (default). Always send the Accept header.

Common response wrapper fields:
```json
{
  "PAPIErrorCode": 0,
  "ErrorMessage": "",
  "ShelfLocationGetRows": [ ... ]
}
```

`PAPIErrorCode = 0` means success. Any non-zero value is an error — check `ErrorMessage`.

Common error codes:
| Code | Meaning |
|------|---------|
| 0 | Success |
| -1 | General error |
| -3501 | Invalid credentials / signature mismatch |
| -4 | Record not found |
| -6000 | Patron not found |
| -6001 | Invalid patron password |

---

## Common Mistakes

- **403 on every request** — signature URI must be lowercase; check that `date_str` is identical in header and signature
- **XML response instead of JSON** — add `Accept: application/json` header
- **"Invalid AppID"** — AppID must be registered in Polaris admin; use the correct numeric ID
- **OrgID matters for shelf locations** — pass the specific branch OrgID, not the system-level `1`, or you may get an empty list
- **Clock skew** — Polaris rejects requests where the `Date` header is more than ~5 minutes off server time; ensure server time is NTP-synced
- **Content-Type for GET** — do NOT send `Content-Type` header on GET requests; the signature `content_type` field should be empty string

---

## Full Working Example — ShelfLocationsGet

```python
import hmac, hashlib, base64, requests
from email.utils import formatdate

ACCESS_ID  = "your_access_id"
SECRET_KEY = "your_secret_key"
BASE_URL   = "https://polaris.rhpl.org/PolarisAPI"
LANG_ID    = 1033
APP_ID     = 100   # replace with real AppID
ORG_ID     = 3     # Main Library

def papi_get(path):
    date_str = formatdate(usegmt=True)
    message = f"GET\n\n{date_str}\n\n{path.lower()}"
    sig = base64.b64encode(
        hmac.new(SECRET_KEY.encode(), message.encode(), hashlib.sha1).digest()
    ).decode()
    headers = {
        "Date": date_str,
        "Authorization": f"PWS {ACCESS_ID}:{sig}",
        "Accept": "application/json",
    }
    resp = requests.get(BASE_URL + path, headers=headers)
    resp.raise_for_status()
    return resp.json()

path = f"/REST/public/v1/{LANG_ID}/{APP_ID}/{ORG_ID}/shelflocations"
data = papi_get(path)

if data["PAPIErrorCode"] != 0:
    print(f"PAPI error: {data['ErrorMessage']}")
else:
    for loc in data["ShelfLocationGetRows"]:
        print(loc["ShelfLocationID"], loc["Name"])
```

---

## Local mirror of the full PAPI reference

Pulled the entire III Polaris 8.0 PAPI doc set (135 pages) on 2026-05-04. Lives at:
```
/var/opt/rhpl/polarissql/docs/papi-reference/
```
Start at `INDEX.md` — pages are categorized (Authentication, Holds, Patron Self-Service Updates, etc.). Each `.md` file links to its source URL.

## Polaris API Documentation

The official Polaris PAPI documentation is distributed with each Polaris version. If you have access to the Polaris server, the docs are typically at:
```
https://{polaris-server}/PolarisAPI/swagger
```
or available from Clarivate's support portal (requires login).

The Swagger UI lists all available endpoints, parameters, and response schemas for your installed Polaris version — it is the authoritative reference for endpoint-specific fields. RHPL's swagger UI is at:
```
https://catalog.rhpl.org/PAPIService/swagger/index.html
```

## Notable absences (verified 2026-05-02)

PAPI does NOT expose:
- **Patron Merge** — merging two patron records is LEAP-UI only (or paid Clarivate work)
- **Patron full update** (only `UpdatePatronNotes` exists for the Notes field)
- **Patron barcode change** (`ItemsUpdateBarcodePut` is for cataloging items, not patrons)
- **Patron delete**

These constraints matter for any workflow that wants to consolidate duplicate patron records or change a patron's barcode programmatically — they have to happen via LEAP UI or a paid Clarivate workorder.
