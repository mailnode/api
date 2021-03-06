# Lists

## Get All Lists


```shell

curl -H "Authorization: Bearer yourApiKey" "http://api.mailnode.io/lists"

```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "token": "aTgmVKNpy7RQRRBtHhXqxeiI2e6wHjIw",
      "name": "exampleList2",
      "default_from_name": "",
      "default_from_email": "",
      "default_list_reminder": "",
      "company": "",
      "address": "",
      "city": "",
      "zip_code": "",
      "phone": ""
    },
    {
      "token": "LQMw8oRB2r6mlDt0DmVmym2nUB1HfK4W",
      "name": "exampleList",
      "default_from_name": "",
      "default_from_email": "",
      "default_list_reminder": "",
      "company": "",
      "address": "",
      "city": "",
      "zip_code": "",
      "phone": ""
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

This endpoint retrieves all lists.

### HTTP Request

`GET http://api.mailnode.io/lists`



## Get a Specific List

```shell

curl -H "Authorization: Bearer yourApiKey" "http://api.mailnode.io/lists/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "token": "aTgmVKNpy7RQRRBtHhXqxeiI2e6wHjIw",
    "name": "exampleList",
    "default_from_name": "",
    "default_from_email": "",
    "default_list_reminder": "",
    "company": "",
    "address": "",
    "city": "",
    "zip_code": "",
    "phone": ""
  }
}
```

This endpoint retrieves a specific list.

### HTTP Request

`GET http://api.mailnode.io/lists/<listToken>`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
listToken | string | The token of the list to retrieve | true


## Update a List

```shell

curl -X PATCH
-d
'name=listName&
default_from_name=listFromName&
default_from_email=from@example.com&
default_list_reminder=reminder
company=companyName&
zip_code=exampleZipCode&
phone=examplePhone&
country_id=exampleCountryId'

-H "Authorization: Bearer yourApiKey"
"http://api.mailnode.io/lists/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "token": "aTgmVKNpy7RQRRBtHhXqxeiI2e6wHjIw",
    "name": "listName",
    "default_from_name": "listFromName",
    "default_from_email": "from@example.com",
    "default_list_reminder": "reminder",
    "company": "companyName",
    "address": "",
    "city": "",
    "zip_code": "exampleZipCode",
    "phone": "examplePhone"
  }
}
```

This endpoint updates a specific list.

### HTTP Request

`PATCH http://api.mailnode.io/lists/<listToken>`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
listToken | string | The token of the list to update | true
name | string | The name of the list | false
default_from_name | string | Default sender name | false
default_from_email | string | Default sender email | false
default_list_reminder | text | List reminder | false
company| string | Company name | false
zip_code | string | Company address zip code | false
phone | string | Company phone | false
country_id | integer | Country id | false

## Create a List

```shell

curl -X POST
-d
'name=listName&
default_from_name=listFromName&
default_from_email=from@example.com&
default_list_reminder=reminder
company=companyName&
zip_code=exampleZipCode&
phone=examplePhone&
country_id=exampleCountryId'

-H "Authorization: Bearer yourApiKey"
"http://api.mailnode.io/lists/"

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "token": "aTgmVKNpy7RQRRBtHhXqxeiI2e6wHjIw",
    "name": "listName",
    "default_from_name": "listFromName",
    "default_from_email": "from@example.com",
    "default_list_reminder": "reminder",
    "company": "companyName",
    "address": "",
    "city": "",
    "zip_code": "exampleZipCode",
    "phone": "examplePhone"
  }
}
```

This endpoint creates new list.

### HTTP Request

`POST http://api.mailnode.io/lists`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
listToken | string | The token of the list to update | true
name | string | The name of the list | true
default_from_name | string | Default sender name | false
default_from_email | string | Default sender email | false
default_list_reminder | text | List reminder | false
company| string | Company name | false
zip_code | string | Company address zip code | false
phone | string | Company phone | false
country_id | integer | Country id | false



## List Errors

The MailNode API uses the following error codes:


Error Code | Meaning
---------- | -------
401 | Unauthorized -- Your authorization params are invalid
404 | List Not Found -- The specified list could not be found
405 | Method Not Allowed -- You tried to access a list with an invalid method
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
