# Reports


## Get All Reports


```shell

curl -H "Authorization: Bearer yourApiKey" "http://api.mailnode.io/reports"

```

> The above command returns JSON structured like this:

```json
{
    "data": [
      {
    "token": "OKB2nP3OpGirhy8QNTn0UBFOrZ0KHHoL",
    "email": "example1@mail.com",
    "sent_on": "2016-04-18 08:48:56",
    "created_at": {
      "date": "2016-04-18 08:48:56.000000",
      "timezone_type": 3,
      "timezone": "UTC"
    }
  },
  {
    "token": "oqxRTSiNX4EUmqLaT2DglX4sZJWK8d0S",
    "email": "example2@mail.com",
    "sent_on": "2016-04-18 08:48:56",
    "created_at": {
      "date": "2016-04-18 08:48:56.000000",
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
                "next": "http://api.mailnode.io/reports?page=2"
            }
        }
    }
}
```

This endpoint retrieves all Reports.

### HTTP Request

`GET http://api.mailnode.io/Reports`



## Get Reports for specific Campaign

```shell

curl -H "Authorization: Bearer yourApiKey" "http://api.mailnode.io/reports/campaign/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt"

```

> The above command returns JSON structured like this:

```json
{
    "data": [
      {
    "token": "OKB2nP3OpGirhy8QNTn0UBFOrZ0KHHoL",
    "email": "example1@mail.com",
    "sent_on": "2016-04-18 08:48:56",
    "created_at": {
      "date": "2016-04-18 08:48:56.000000",
      "timezone_type": 3,
      "timezone": "UTC"
    }
  },
  {
    "token": "oqxRTSiNX4EUmqLaT2DglX4sZJWK8d0S",
    "email": "example2@mail.com",
    "sent_on": "2016-04-18 08:48:56",
    "created_at": {
      "date": "2016-04-18 08:48:56.000000",
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
                "next": "http://api.mailnode.io/reports/campaign/oRR21ykSBXhMDcZTCZWdEJxZSrBjuTBt?page=2"
            }
        }
    }
}
```

This endpoint retrieves a specific Report.

### HTTP Request

`GET http://api.mailnode.io/reports/campaign/<campaignToken>`

### Request Body Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
campaignToken | string | The token of the campaign which reports to retrieve | true


## Report Errors

The MailNode API uses the following error codes:


Error Code | Meaning
---------- | -------
401 | Unauthorized -- Your authorization params are invalid
404 | Reports Not Found -- The specified Reports could not be found
405 | Method Not Allowed -- You tried to access Reports with an invalid method
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
