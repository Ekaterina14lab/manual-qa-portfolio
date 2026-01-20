API Testing Checklist: GET /api/v1/tag/
|ID|Test Scenario|Test Data|Status|ID BR|Priority|Severity|
|-|--------------|-----|------|-----|--------|--------|
|01|Response Code `200 OK`<br> An Admin can successfully retrieve all tags||PASSED|
|02|Response Code `200 OK`<br>A Register User can successfuly retrieve all tags||PASSED|
|03|Response Code `200 OK`<br>An Unregistered User can successfully retrieve all tags||PASSED|
|04|Response Code `200 OK`<br>Response Body: empty list<br>Message: No data found||PASSED|

API Testing Checklist: POST /api/v1/tag/
|ID|Test Scenario|Test Data|Status|ID BR|Priority|Severity|
|-|--------------|-----|------|-----|--------|--------|
|01|Response Code `201 Created`<br>An Admin can successfully create a tag|name: "Мир"<br>group: "4"|PASSED
||*Input field "name" validation*
|02|Response Code `201 Created`<br>Enter a capital Cyrillic letter and send a request with an existing "group" value|name: "Ф"<br>group: "4"|PASSED|
|03|Response Code `201 Created`<br>Enter two Cyrillic letters starting with a capital letter and send a request with an existing "group"|name: "Ми"<br>group: "4"|PASSED|
|04|Response Code `201 Created`<br>Enter two Cyrillic words with whitespace. The first word will be started from a capital letter and the second word will consist of lowercase letters. Send the request with an existing "group"|name: "Миссис дурсль"<br>group: "4"|PASSED|
|05|Response Code `201 Created`<br>Enter thirty-three Cyrillic letters starting with a capital letter and send the request with an existing "group"|name: "Мистер и миссис дурсль проживали."<br>group: "4"|PASSED|
|06|Response Code `201 Created`<br>Enter sixty-three Cyrillic letters starting with a capital letter and send the request with an existing "group"|name: "Мистер и миссис дурсль проживали в доме номер четыре по тисовой"<br>group: "4"|PASSED|
|07|Response Code `201 Created`<br>Enter sixty-four Cyrillic letters starting with a capital letter and send the request with an existing "group"|name: "Мистер и миссис дурсль проживали в доме номер четыре по тисовой."<br>group: "4"|FAILED|BR-4|High|Critical<br>`Response Code 500 Internal Server Error`|
|08|Response code `400 Bad Request`Massege: "The value of "name" already exists<br>Enter an existing "name" and send the request with an existing "group"|name: "Мир"<br>group: "4"|PASSED|
|09|Response Code `400 Bad Request`<br>Massage: "Это поле не может быть пустым"<br>The input field "name" is empty. Send the request with an existing "group"|name<br>group: "4"|PASSED|
|10|Response Code `400 Bad Request`<br>Massage: ""name" containce invalid characters<br>Enter a lowercase Cyrillic letter and send the request with an existing "group"|name: "ф"<br>group: "4"|FAILED|BR-5|Medium|Minor|
|11|Response Code `400 Bad Request`<br>
