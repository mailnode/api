# Members

## Get All Members


```shell

curl -H "Authorization: Bearer yourApiKey" "http://api.mailnode.io/lists/<listToken>/members"

```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "email": "user1@mail.com",
      "first_name": "ExampleFirstName1",
      "last_name": "ExampleSecondName1",
      "token": "g3dpPqTtNdarFoNq17iwpqxZojJI65aW"
    },
    {
      "email": "user2@mail.com",
      "first_name": "ExampleFirstName2",
      "last_name": "ExampleSecondName2",
      "token": "c1hlGSPl2H0eHICfGb40mcEI1yyIQ1w8"
    }
  ],
  "meta": {
    "pagination": {
      "total": 2,
      "count": 2,
      "per_page": 25,
      "current_page": 1,
      "total_pages": 1,
      "links": []
    }
  }
}
```

This endpoint retrieves all members.

### HTTP Request

`GET http://api.mailnode.io/lists/<listToken>/members`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
listToken | string | The token of the list of which members to retrieve | true

## Get a Specific Member

```shell

curl -H "Authorization: Bearer yourApiKey" "http://api.mailnode.io/lists/<listToken>/members/<memberToken>"

```

> The above command returns JSON structured like this:

```json

{
  "data": {
      "email": "user1@mail.com",
      "first_name": "ExampleFirstName1",
      "last_name": "ExampleSecondName1",
      "token": "g3dpPqTtNdarFoNq17iwpqxZojJI65aW"
    }
}

```

This endpoint retrieves a specific member.

### HTTP Request

`GET http://api.mailnode.io/lists/<listToken>/members/<memberToken>`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
listToken | string | The token of the list of which members to retrieve | true
memberToken | string | The token of the member to retrieve | true


## Update a Member

```shell

curl -X PATCH
-d
'email=updateUser@mail.com&
first_name=updateFirstName&
last_name=updateLastName'

-H "Authorization: Bearer yourApiKey"
"http://api.mailnode.io/lists/<listToken>/members/<memberToken>"

```

> The above command returns JSON structured like this:

```json

{
  "data": {
      "email": "updateUser@mail.com",
      "first_name": "updateFirstName",
      "last_name": "updateLastName",
      "token": "g3dpPqTtNdarFoNq17iwpqxZojJI65aW"
    }
}

```

This endpoint updates a specific member.

### HTTP Request

`PATCH http://api.mailnode.io/lists/<listToken>/members/<memberToken>`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
listToken | string | The token of the list of which members to retrieve | true
memberToken | string | The token of the member to retrieve | true
first_name | string | The first name of the member | false
last_name | string | The last name of the member | false
email | string | The email of the member | true


## Create a Member

```shell

curl -X POST
-d
'email=newUser@mail.com&
first_name=FirstName&
last_name=LastName'

-H "Authorization: Bearer yourApiKey"
"http://api.mailnode.io/members/"

```

> The above command returns JSON structured like this:

```json
{
  "data": {
      "email": "newUser@mail.com",
      "first_name": "FirstName",
      "last_name": "LastName",
      "token": "g3dpPqTtNdarFoNq17iwpqxZojJI65aW"
    }
}
```

This endpoint creates new member.

### HTTP Request

`POST http://api.mailnode.io/lists/<listToken>/members/<memberToken>`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
listToken | string | The token of the list of which members to retrieve | true
memberToken | string | The token of the member to retrieve | true
first_name | string | The first name of the member | false
last_name | string | The last name of the member | false
email | string | The email of the member | true


## Delete a Member

```shell

curl -X DELETE
-H "Authorization: Bearer yourApiKey"
"http://api.mailnode.io/lists/<listToken>/members/<memberToken>"


```

> The above command returns JSON structured like this:

```json
{
  "message": "Member deleted successfully!",
  "status_code": 200
}
```

This endpoint deletes a specific member.

### HTTP Request

`DELETE http://api.mailnode.io/lists/<listToken>/members/<memberToken>`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
listToken | string | The token of the list of which members to retrieve | true
memberToken | string | The token of the member to delete | true


## Member Errors

The MailNode API uses the following error codes:


Error Code | Meaning
---------- | -------
401 | Unauthorized -- Your authorization params are invalid
404 | Member Not Found -- The specified member could not be found
405 | Method Not Allowed -- You tried to access a member with an invalid method
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
