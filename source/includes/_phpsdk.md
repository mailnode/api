# PHP SDK


## Install MailNode SDK


```php

<?php

require '/vendor/autoload.php';

MailNodeApp::init('yourApiKey');

//now you can use any mailnode sdk functions

```

You can install mailnode-php-sdk via Composer, just run `composer require` command from your terminal.

`composer require mailnode/mailnode-php-sdk`


### Composer auto loader

You need to autoload mailnode-php-sdk via Composer.

`require 'vendor/autoload.php';`


### Setup MailNode API key

To use mailnode-php-sdk you need first to initialize it with your api key.

`MailNodeApp::init('yourApiKey');`



## Get All Lists

```php
<?

MailNodeApp::getAllLists();

```

This function retrieves all lists and returns an array of EmailList objects.

## Get All Members of the List

```php
<?

MailNodeApp::getAllMembers($listToken);

```

This function retrieves all members of the list with token == $listToken and returns an array of Member objects.

### Function Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
listToken | string | The token of the list which members to retrieve | true

## Add New Member to the List

```php
<?

MailNodeApp::addMemberToList($listToken, new Member('newUser@email.com', "userFirstName", "userLastName"));

```

This function adds a new member to the list with token == $listToken and returns a Member object.

### Function Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
listToken | string | The token of the list where to add new member | true
email | string | The email of the member | true
first_name | string | The first name of the member | true
last_name | string | The last name of the member | true

## Create New Campaign

```php
<?

$campaign = new Campaign('yourCampaignName', 'campaignSubject', 'senderName', 'sender@mail.com');
$campaign->setList($listToken);
$campaign->setTemplate($templateToken);

MailNodeApp::createCampaign($campaign);

```

This function creates a new campaign with list and template which tokens you have provided and returns a Campaign object.

### Function Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
name | string | The name of the campaign | true
listToken | string | The token of the list for which is campaign created | true
templateToken | string | The token of the template for which is campaign created  | true
subject | string | Campaign subject | true
from_email | string | Sender email | true
from_name | string | Sender name | true

## Create New Template

```php
<?

MailNodeApp::createTemplate(new Template('templateName', 'templateContent'));

```

This function creates a new template and returns a Template object.

### Function Parameters

Parameter | Type  | Description | Required
--------- | ----- | ------------| --------
templateName | string | name of the template | true
templateContent | string | template content | true
