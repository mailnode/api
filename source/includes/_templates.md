# Templates

## Get All Templates


```shell

curl -u your@Email:yourPassword "http://api.mailnode.io/templates"

```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "token": "q1JjBxyE85RTm06coPAslNAvQTlhdbmJ",
      "name": "Dummy template",
      "content": "Qui aliquid harum officiis aliquam. Quidem qui excepturi modi aut. Non ut voluptatum est eos quod.",
      "created_at": "April 18, 2016 12:41 PM"
    },
    {
      "token": "MAoQU8b7QZ3Iyv0XkOmma2MWH4AYVXBx",
      "name": "Dummy template",
      "content": "Dolor iste minus facilis reprehenderit voluptas expedita. Et officia rerum mollitia quasi quam ut. Facilis commodi ut suscipit omnis. Consequuntur labore recusandae odit eos.",
      "created_at": "April 18, 2016 8:48 AM"
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

This endpoint retrieves all templates.

### HTTP Request

`GET http://api.mailnode.io/templates`



## Get a Specific Template

```shell

curl -u your@Email:yourPassword "http://api.mailnode.io/templates/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "token": "MAoQU8b7QZ3Iyv0XkOmma2MWH4AYVXBx",
    "name": "Dummy template",
    "content": "Dolor iste minus facilis reprehenderit voluptas expedita. Et officia rerum mollitia quasi quam ut. Facilis commodi ut suscipit omnis. Consequuntur labore recusandae odit eos.",
    "created_at": "April 18, 2016 8:48 AM"
  }
}
```

This endpoint retrieves a specific template.

### HTTP Request

`GET http://api.mailnode.io/templates/<templateToken>`

### Request Body Parameters

Parameter | Description
--------- | -----------
templateToken | The token of the template to retrieve


## Update a Template

```shell

curl -X PATCH
-d
'name=UpdatedTemplateName&
content=Updated Template Content&
-u your@Email:yourPassword
"http://api.mailnode.io/templates/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "token": "MAoQU8b7QZ3Iyv0XkOmma2MWH4AYVXBx",
    "name": "UpdatedTemplateName",
    "content": "Updated Template Content",
    "created_at": "April 18, 2016 8:48 AM"
  }
}
```

This endpoint updates a specific template.

### HTTP Request

`PATCH http://api.mailnode.io/templates/<templateToken>`

### Request Body Parameters

Parameter | Description
--------- | -----------
templateToken | The token of the template to update
name | The name of the template
content | Template content


## Create a Template

```shell

curl -X POST
-d
'name=NewTemplateName&
content=New Template Content&
-u your@Email:yourPassword
"http://api.mailnode.io/templates"

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "token": "MAoQU8b7QZ3Iyv0XkOmma2MWH4AYVXBx",
    "name": "NewTemplateName",
    "content": "New Template Content",
    "created_at": "April 18, 2016 8:48 AM"
  }
}
```

This endpoint creates new template.

### HTTP Request

`POST http://api.mailnode.io/templates`

### Request Body Parameters

Parameter | Description
--------- | -----------
templateToken | The token of the template to update
name | The name of the template
content | Template content


## Delete a Template

```shell

curl -X DELETE
-u your@Email:yourPassword
"http://api.mailnode.io/templates/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"


```

> The above command returns JSON structured like this:

```json
{
  "message": "Template deleted successfully!",
  "status_code": 200
}
```

This endpoint deletes a specific template.

### HTTP Request

`DELETE http://api.mailnode.io/templates/<templateToken>`

### Request Body Parameters

Parameter | Description
--------- | -----------
templateToken | The token of the template to delete


## Template Errors

The MailNode API uses the following error codes:


Error Code | Meaning
---------- | -------
401 | Unauthorized -- Your authorization params are invalid
404 | Template Not Found -- The specified template could not be found
405 | Method Not Allowed -- You tried to access a template with an invalid method
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
