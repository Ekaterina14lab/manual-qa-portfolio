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
|01|`201 Created`<br>An Admin can successfully create a tag|name: "Мир"<br>group: "4"|PASSED
||*Input field "name" validation*
|02|`201 Created`<br>Enter a capital Cyrillic letter and send a request with an existing "group" value|name: "Ф"<br>group: "4"|PASSED|
|03|`201 Created`<br>Enter two Cyrillic letters stared from a capital letter and send a request with an existing "group"|name: "Ми"<br>group: "4"|PASSED|
|04|`201 Created`<br>Enter two Cyrillic words with whitespace. The first word will be started from a capital letter and the second word will be consist of lowercase letters. Send the request with an existing "group"|name: "Миссис дурсль"<br>group: "4"|PASSED|
|05|`201 Created`<br>Enter thirty three Cyrillic letters started from a capital letter and send the request with an existing "group"|name: "Мистер и миссис дурсль проживали."<br>group: "4"|PASSED|
|06|`201 Created`<br>Enter sixty three Cyrillic leters started from a capital letter and send the request with an axisting "group"|name: "Мистер и миссис дурсль проживали в доме номер четыре по тисовой"<br>|group: "4"|PASSED|
|07|`201 Created`<br>Enter sixty four Cyrillic letters started from a capital letter and send the request with an existing "group"|name: "Мистер и миссис дурсль проживали в доме номер четыре по тисовой."<br>group: "4"|PASSED|
|08|`400 Bad Request`<br>
