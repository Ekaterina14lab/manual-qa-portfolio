API Testing Checklist: GET /api/v1/tag/
|ID|Test Scenario|Test Data|Status|ID BR|Priority|Severity|
|-|--------------|-----|------|-----|--------|--------|
|01|Response Code `200 OK`<br> An Admin can successfully retrieve all tags||PASSED|
|02|Response Code `200 OK`<br>A Register User can successfuly retrieve all tags||PASSED|
|03|Response Code `200 OK`<br>An Unregistered User can successfully retrieve all tags||PASSED|
|04|Response Code `200 OK`<br>Message: `"No data found"`<br>Response Body: empty list||PASSED|

API Testing Checklist: POST /api/v1/tag/
|ID|Test Scenario|Test Data|Status|ID BR|Priority|Severity|
|-|--------------|-----|------|-----|--------|--------|
|01|Response Code `201 Created`<br>An Admin can successfully create a tag|name: "Мир"<br>group: "4"|PASSED
||*Input field "name" validation*
|02|Response Code `201 Created`<br>Enter a capital Cyrillic letter and send the request with an existing "group" value|name: "Ф"<br>group: "4"|PASSED|
|03|Response Code `201 Created`<br>Enter 2 Cyrillic letters starting with a capital letter and send the request with an existing "group"|name: "Ми"<br>group: "4"|PASSED|
|04|Response Code `201 Created`<br>Enter 4 capital Cyrilic letters and send the request with an existing "group"|name: "МИРА"<br>group: "4"|PASSED|
|05|Response Code `201 Created`<br>Enter two Cyrillic words with whitespace. The first word will be started from a capital letter and the second word will consist of lowercase letters. Send the request with an existing "group"|name: "Миссис дурсль"<br>group: "4"|PASSED|
|06|Response Code `201 Created`<br>Enter 33 Cyrillic letters starting with a capital letter and send the request with an existing "group"|name: "Мистер и миссис дурсль проживали."<br>group: "4"|PASSED|
|07|Response Code `201 Created`<br>Enter 63 Cyrillic letters starting with a capital letter and send the request with an existing "group"|name: "Мистер и миссис дурсль проживали в доме номер четыре по тисовой"<br>group: "4"|PASSED|
|08|Response Code `201 Created`<br>Enter 64 Cyrillic letters starting with a capital letter and send the request with an existing "group"|name: "Мистер и миссис дурсль проживали в доме номер четыре по тисовой."<br>group: "4"|FAILED|BR-4|High|Critical<br>`Response Code 500 Internal Server Error`|
|09|Response code `400 Bad Request`<br>Massege: `"The value of "name"` already exists<br>Enter an existing "name" and send the request with an existing "group"|name: "Мир"<br>group: "4"|PASSED|
|10|Response Code `400 Bad Request`<br>Massage: `"This field is requied"`<br>The input field "name" is empty. Send the request with an existing "group"|name: ""<br>group: "4"|PASSED|
|11|Response Code `400 Bad Request`<br>Massage: `""name" containce invalid characters"`<br>Enter a lowercase Cyrillic letter and send the request with an existing "group"|name: "ф"<br>group: "4"|FAILED|BR-5|Medium|Minor|
|12|Response Code `400 Bad Request`<br>Massage: `"Ensure this value consist no more than 64 characters"`<br>Enter 65 Cyrillic letters starting with a capital letter and send thq request with existing "group"|name: "Мистер и миссис дурсль проживали в доме номер четыре по тисовой у"<br>group: "4"|PASSED|
|13|Response Code `400 Bad Request`<br>Massage: `"Ensure this value consist no vore than 64 characters"`<br>Enter 165 Cyrillic letters starting with a capital letter and send the request with existung "group"|name: "Мистер и миссис дурсль проживали в доме номер четыре по тисовой улице и всегда с гордостью заявляли, что они, слава богу, абсолютно нормальные люди. Уж от кого-кого,"<br>group: "4"|PASSED|
|14|Response Code `400 Bad Request`<br>Massage: `"name" containce invalid characters"`<br>Enter 5 Latin letters starting with a capital letter and send the request with an existing "group"|name: "Lukcy"<br>group: "4"|FAILED|BR-7|Medium|Normal|
