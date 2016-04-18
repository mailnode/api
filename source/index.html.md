---
title: API Reference

language_tabs:
  - shell

toc_footers:


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
  -H "Authorization: Basic yourKey"
```

MailNode uses Authorization credentials to allow access to the API.

MailNode expects for the Authorization credentials to be included in all API requests to the server in a header that looks like the following:

`Authorization: Basic yourKey`


# Campaigns

## Get All Campaigns


```shell

curl -u your@Email:yourPassword "http://api.mailnode.io/campaigns"

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

curl -u your@Email:yourPassword "http://api.mailnode.io/campaigns/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"

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

Parameter | Description
--------- | -----------
campaignToken | The token of the campaign to retrieve


## Update a Campaign

```shell

curl -X PATCH -d 'name=exampleName&subject=exampleSubject&from_email=example@mail.com&from_name=exampleFromName' -u your@Email:yourPassword "http://api.mailnode.io/campaigns/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"

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

Parameter | Description
--------- | -----------
campaignToken | The token of the campaign to update
name | The name of the campaign
template | Template token of new campaign
list | List token of new campaign
subject | Subject text
from_email| Sender email
from_name | Sender name

Optional Parameters | Description
------------------- | -----------
send_time_start | Starting time of email sending
send_time_end |Starting time of email sending

## Create a Campaign

```shell
curl "http://example.com/api/campaigns"
-H "yourEmail"
-H "yourPassword"
-H "Authorization: Basic yourKey"
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

Parameter | Description
--------- | -----------
name | The name of the campaign
template | Template token of new campaign
list | List token of new campaign
subject | Subject text
from_email| Sender email
from_name | Sender name

Optional Parameters | Description
------------------- | -----------
send_time_start | Starting time of email sending
send_time_end |Starting time of email sending

## Delete a Campaign

```shell
curl "http://example.com/api/campaigns/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"
-H "yourEmail"
-H "yourPassword"
-H "Authorization: Basic yourKey"
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

Parameter | Description
--------- | -----------
campaignToken | The token of the campaign to delete


## Campaign Errors

The MailNode API uses the following error codes:


Error Code | Meaning
---------- | -------
401 | Unauthorized -- Your authorization params are invalid
404 | Campaign Not Found -- The specified campaign could not be found
405 | Method Not Allowed -- You tried to access a campaign with an invalid method
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
