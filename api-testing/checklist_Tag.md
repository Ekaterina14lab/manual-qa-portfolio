API Testing Checklist: GET /api/v1/tag/
|#|Check|Means|Status|ID BR|Preority|Severity|
|-|-----|-----|------|-----|--------|--------|
|01|`200 OK`<br> An Admin can successfilly retrieve all tags||PASSED|
|02|`200 OK`<br>A Register User can successfuly retrieve all tags||PASSED|
|03|`200 OK`<br>An Unregister User can successfully retrieve all tags||PASSED|
|04|`400 Bad Request`<br>There is no dats to retrieve||PASSED|

API Testing Checklist: POST /api/v1/tag/
|#|Check|Means|Status|ID BR|Preority|Severity|
|-|-----|-----|------|-----|--------|--------|
|01|`201 Created`<br>An Admin can successfully create a tag||PASSED
||*Input field "name" validation*
|02|`201 Created`<br>Enter three Cyrillic letters starting a capital letter and send a request with an existing "group" value
