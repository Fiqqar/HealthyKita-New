{nb: please call me before fetch to turn on tunelling server}

[Users API]
[SIGNUP & LOGIN]

[POST]
/api/signup/user
BODY property: {username,password,email}
response: {message}

[POST]
/api/login/user
BODY property: {username,passworODYd}
response: JSON {message}
COOKIE: tokenUser

for recovery password, this API have a child API
[POST]
api/recovery/password
BODY property: {email}
response: JSON {message}

//in page frontend
//check if have action changes pw

in frontend[redirect] in this route vue -> http://localhost:8080/forgotPW/:email
:email is param
AND NEXT fetch API
[GET]
/verify/forgotPw/:email //:email for your param :email 
response: HEADER {changesPwCode} //recommended store at variable

in input newPw
fetch
[POST]
api/changes/pw
BODY property: {newPw,changesPwCode} //changesPwCode is value from header 
response: JSON {message}





