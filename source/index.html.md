---
title: MailNode | API Reference

language_tabs:
  - shell

includes:
  - lists
  - members
  - templates
  - reports
  - phpsdk

search: true
---

# Introduction

Welcome to the MailNode API!

You can view code examples in the dark area to the right.

# Authentication

> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "http://api.mailnode.io/"
  -H "Authorization: Bearer yourApiKey"
```

> Make sure to replace `yourApiKey` with your API key.

MailNode uses API keys to allow access to the API. You can register a new MailNode API key at our [settings panel](http://mailnode.io/panel/settings).

MailNode expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer yourApiKey`


# Campaigns

## Get All Campaigns


```shell

curl "http://api.mailnode.io/campaigns"
-H "Authorization: Bearer yourApiKey"


```

> The above command returns JSON structured like this:

```json
{
    "data": [
        {
            "name": "CampaignName1",
            "subject": "SubjectCampaign1",
            "from_name": "fromExampleName",
            "from_email": "fromSomeone@example.com",
            "opens": 12,
            "clicks": 10,
            "token": "HNzrB6QmB7Z8I2x0TjzYcC7aSvCiy2r2",
            "sent_emails": 20,
            "created_at": {
                "date": "2016-04-15 09:59:59.000000",
                "timezone_type": 3,
                "timezone": "UTC"
            }
        },
        {
            "name": "CampaignName2",
            "subject": "SubjectCampaign2",
            "from_name": "fromExampleName",
            "from_email": "fromSomeone@example.com",
            "opens": 12,
            "clicks": 10,
            "token": "HNzrB6QmB7Z8I2x0TjzYcC7aSvCiy2r2",
            "sent_emails": 200,
            "created_at": {
                "date": "2016-04-15 09:59:59.000000",
                "timezone_type": 3,
                "timezone": "UTC"
            }
        }
    ],
    "meta": {
        "pagination": {
            "total": 4,
            "count": 2,
            "per_page": 2,
            "current_page": 1,
            "total_pages": 2,
            "links": {
                "next": "http://api.mailnode.app/campaigns?page=2"
            }
        }
    }
}
```

This endpoint retrieves all campaigns.

### HTTP Request

`GET http://api.mailnode.io/campaigns`



## Get a Specific Campaign

```shell

curl -H "Authorization: Bearer yourApiKey" "http://api.mailnode.io/campaigns/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"

```

> The above command returns JSON structured like this:

```json
{
    "name": "CampaignName",
    "subject": "SubjectCampaign",
    "from_name": "fromExampleName",
    "from_email": "fromSomeone@example.com",
    "opens": 0,
    "clicks": 0,
    "token": "HNzrB6QmB7Z8I2x0TjzYcC7aSvCiy2r2",
    "sent_emails": 0,
    "created_at": {
        "date": "2016-04-15 09:59:59.000000",
        "timezone_type": 3,
        "timezone": "UTC"
    }
}
```

This endpoint retrieves a specific campaign.

### HTTP Request

`GET http://api.mailnode.io/campaigns/<campaignToken>`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
campaignToken | string | The token of the campaign to retrieve | true


## Update a Campaign

```shell

curl -X PATCH
-d
'name=UpdatedCampaignName&
subject=UpdatedSubjectCampaign&
from_email=UpdatedfromSomeone@example.com&
from_name=exampleFromName'

-H "Authorization: Bearer yourApiKey"
"http://api.mailnode.io/campaigns/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"

```

> The above command returns JSON structured like this:

```json
{
    "name": "UpdatedCampaignName",
    "subject": "UpdatedSubjectCampaign",
    "from_name": "UpdatedfromExampleName",
    "from_email": "UpdatedfromSomeone@example.com",
    "opens": 0,
    "clicks": 0,
    "token": "HNzrB6QmB7Z8I2x0TjzYcC7aSvCiy2r2",
    "sent_emails": 0,
    "created_at": {
        "date": "2016-04-15 09:59:59.000000",
        "timezone_type": 3,
        "timezone": "UTC"
    }
}
```

This endpoint updates a specific campaign.

### HTTP Request

`PATCH http://api.mailnode.io/campaigns/<campaignToken>`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
campaignToken | string | The token of the campaign to update | true
name | string | The name of the campaign | true
template | string | Template token of new campaign | false
list | string | List token of new campaign | false
subject | string | Subject text | true
from_email | string | Sender email | true
from_name | string | Sender name | true
send_time_start | timestamp | Starting time of email sending | false
send_time_end | timestamp | Starting time of email sending | false

## Create a Campaign

```shell

curl -X POST
-d
'name=NewCampaignName&
subject=NewSubjectCampaign&
from_email=fromSomeone@example.com&
from_name=fromExampleName&
template=yourTemplateToken&
list=yourListToken'

-H "Authorization: Bearer yourApiKey"
"http://api.mailnode.io/campaigns/"

```

> The above command returns JSON structured like this:

```json
{
    "name": "NewCampaignName",
    "subject": "NewSubjectCampaign",
    "from_name": "fromExampleName",
    "from_email": "fromSomeone@example.com",
    "opens": 0,
    "clicks": 0,
    "token": "HNzrB6QmB7Z8I2x0TjzYcC7aSvCiy2r2",
    "sent_emails": 0,
    "created_at": {
        "date": "2016-04-15 09:59:59.000000",
        "timezone_type": 3,
        "timezone": "UTC"
    }
}
```

This endpoint creates new campaign.

### HTTP Request

`POST http://api.mailnode.io/campaigns`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
campaignToken | string | The token of the campaign to update | true
name | string | The name of the campaign | true
template | string | Template token of new campaign | true
list | string | List token of new campaign | true
subject | string | Subject text | true
from_email | string | Sender email | true
from_name | string | Sender name | true
send_time_start | timestamp | Starting time of email sending | false
send_time_end | timestamp | Starting time of email sending | false

## Delete a Campaign

```shell

curl -X DELETE
-H "Authorization: Bearer yourApiKey"
"http://api.mailnode.io/campaigns/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"


```

> The above command returns JSON structured like this:

```json
{
  "message": "Campaign deleted successfully!",
  "status_code": 200
}
```

This endpoint deletes a specific campaign.

### HTTP Request

`DELETE http://api.mailnode.io/campaigns/<campaignToken>`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
campaignToken | string | The token of the campaign to delete | true


## Campaign Errors

The MailNode API uses the following error codes:


Error Code | Meaning
---------- | -------
401 | Unauthorized -- Your authorization params are invalid
404 | Campaign Not Found -- The specified campaign could not be found
405 | Method Not Allowed -- You tried to access a campaign with an invalid method
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
