# Option

## Option List

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.02 / Joey Huang**

  * Modify Fail Parameters:
    * Apply new structure
    * modify descriptions of error messages
</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/option/list` |
| Method | `post` |
| Use | to get company option list |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "options": [{
        "id": "AAAA160401000002OD",
        "name": "option 1",
        "start_time": 213216546,
        "end_time": 213216998,
        "status": 0,
        "company": {
            "id": 1,
            "name": "Company A"
        }
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| options | array |  |

| option | Type | Description |
| -------: | :---- | :--- |
| id | integer |  option id |
| name | string |  option name |
| company | object |  |
| start_time | timestamp | timestamp/second |
| end_time | timestamp | timestamp/second |
| status | boolean | is option executable |

| company | Type | Description |
| -------: | :---- | :--- |
| *id* | integer | company id |
| *name* | string | company name |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: the request does not include the api_key parameter</li><li>does not signin: the api_key of user does not signin</li><li>not select company yet: the api_key of user need change current company</li><li>company not exist: the api_key of currenct company not exist</li><li>not company member: the api_key of the user is not the company member</li></ul> |

## Create Option

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.02 / Joey Huang**

  * Modify Success Parameters:
    * Apply new structure
  * Modify Fail Parameters:
    * Apply new structure
    * modify descriptions of error messages
</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/option/create` |
| Method | `post` |
| Use | to company options. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "name": "Option with XXX",
    "start_time": "123548765",
    "end_time": "123654987",
    "brand_sharing": 50,
    "retailer_sharing": 30,
    "retailers": [1, 2, 3, 4],
    "distributor": [{
        "currency_id": 1,
        "role": "Test",
        "sharing": 20
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| name | string | option name |
| start_time | timestamp | timestamp/second |
| end_time | timestamp | timestamp/second |
| deposit | boolean | the result that brand want retailer to pay deposit |
| deposit_sharing | integer | deposit sharing |
| brand_sharing | integer | brand sharing |
| retailer_sharing | integer | retailer sharing |
| retailers | array | company id set |
| distributors | array | |

| distributor | Type | Description |
| -------: | :---- | :--- |
| company_id | integer | company  id |
| sharing | integer | distributor sharing |
| role | string | customization role name |

### Return Parameters

<aside class="success">
Success
</aside>

Nothing was returned

> Return Failure Parameters (illegal form input)

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "illegal form input",
    "validation": {
        "name": [
            "required"
        ],
        "deposit": [
            "invalid format"
        ],
        "deposit_sharing": [
            "invalid format"
        ],
        "brand_sharing": [
            "invalid format"
        ],
        "retailer_sharing": [
            "invalid format"
        ]
    }
}
```

> Return Failure Parameters (duplicate retailer relation)

```json
{
    "error_name": "duplicate retailer relation",
    "retailers": [
        {
            "id": 235,
            "name": "7-11"
        }
    ]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: the request does not include the api_key parameter</li><li>does not signin: the api_key of user does not signin</li><li>not select company yet: the api_key of user need change current company</li><li>company not exist: the api_key of currenct company not exist</li><li>not company member: the api_key of the user is not the company member</li><li>duplicate retailer relation: reatiler has be joined to your other option</li><li>illegal form input: form format does not pass validation</li></ul> |
| validation | object | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input.|
| retailers | array | duplicate retailer list |

| validation | Type | Description |
| -------: | :---- | :--- |
| name | array | <ul><li>required: it’s necessary column for this api</li></ul> |
| deposit | array | <ul><li>invalid format: deposit not boolean</li></ul> |
| deposit_sharing | array | <ul><li>invalid format: deposit  sharing not numeric</li></ul> |
| brand_sharing | array | <ul><li>invalid format: brand sharing not numeric</li></ul> |
| retailer_sharing | array | <ul><li>invalid format: retailer  sharing not numeric</li></ul> |

| retailer | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id |
| name | string | company name |


## Option   Detail

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.02 / Joey Huang**

  * Modify Fail Parameters:
    * Apply new structure
    * modify descriptions of error messages
</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/option/detail` |
| Method | `post` |
| Use | to get option detail. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "option_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| option_id | integer | option id |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": "AAAA160401000002OD",
    "name": "option 1",
    "start_time": 213216546,
    "end_time": 213216998,
    "stabrand_sharingtus": 40,
    "retailer_sharing": 45,
    "status": 1,
    "status_message": {},
    "retailers": [{
        "id": 1,
        "name": "Company A"
    }],
    "distributors": [{
        "id": 1,
        "name": "Company A",
        "sharing": 15,
        "role": "Distributor 1"
    }],
    "company": {
        "id": 1,
        "name": "Company A"
    },
    "invitations": [{
    	"id": 1,
    	"company_name": "ZARZ",
		"given_name": "Jianhua",
		"family_name": "Wang",
		"email": "abc@gmail.com",
		"status": "Waiting",
		"invited_time": 432165987622,
		"invited_counter": 1
    }]
}
```

| Parameter | Type | Description ||
| -------: | :---- | :--- |:--|
| name | string | option  name |
| start_time | timestamp | timestamp/second |
| end_time | timestamp | timestamp/second |
| status | boolean | is option  executable |
| status_message | object | the reasons why status is false |
| deposit | boolean | the result that brand want retailer to pay deposit |
| deposit_sharing | integer | deposit sharing |
| brand_sharing | integer | brand sharing |
| retailer_sharing | integer | retailer sharing |
| company | object | |
| retailers | array | |
| distributors | array | |
| invitations | array | invitation list of option |

| status_message | Type | Description ||
| -------: | :---- | :--- |:--|
| *start_time* | **array** | error reasons |
| *required* | string | it’s necessary to option |
| *end_time* | **array** | error reasons |
| *expired* | string | time is expired |
| *active*| **array** | error reasons |
| *no* | string | option is close |
| *sharing* | **array** | error reasons |
| *invalid value* | string | total sharing is not equal to 100 |

| company | Type | Description ||
| -------: | :---- | :--- |:--|
| *id* | integer | company id |
| *name* | string | company name |

| retailer | Type | Description ||
| -------: | :---- | :--- |:--|
| *id* | integer | company id |
| *name* | string | company name |

| distributor | Type | Description ||
| -------: | :---- | :--- |:--|
| *id* | integer | company id |
| *name* | string | company name |
| *sharing* | integer | distributor sharing |
| *role* | string | customization role name |

| invitation | Type | Description ||
| -------: | :---- | :--- |:--|
| *id* | integer | invitation id |
| *company_name* | string | pre-input company name |
| *given_name* | string | pre-input given name |
| *family_name* | string | pre-input family name |
| *email* | string | receiver email |
| *status* | string | invited status |
| *last_invited_time* | timestamp | last invited time |
| *invited_counter* | integer | invited counter |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: the request does not include the api_key parameter</li><li>does not signin: the api_key of user does not signin</li><li>not select company yet: the api_key of user need change current company</li><li>company not exist: the api_key of currenct company not exist</li><li>not company member: the api_key of the user is not the company member</li><li>option not exist: the option_id of option is not exist</li></ul> |


## Edit Option

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.02 / Joey Huang**

  * Modify Fail Parameters:
    * Apply new structure
    * Modify the json of input parameters
  * Modify Fail Parameters:
    * Apply new structure
    * Modify descriptions of error messages
</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/option/edit` |
| Method | `post` |
| Use | to edit option |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "option_id": 5566,
    "name": "Option with XXX",
    "start_time": "123548765",
    "end_time": "123654987",
    "brand_sharing": 50,
    "retailer_sharing": 30,
    "retailers": [1, 2, 3, 4],
    "distributor": [{
        "company_id": 1,
        "role": "Test",
        "sharing": 20
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| option_id | integer |  option id |
| name | string | option  name |
| deposit | boolean |the result that brand want retailer to pay deposit |
| deposit_sharing | integer | deposit sharing |
| start_time | timestamp | timestamp/second |
| end_time | timestamp | timestamp/second |
| brand_sharing | integer | brand sharing |
| retailer_sharing | integer | retailer sharing |
| retailers | array | company id set |
| distributors | array | |

| distributor | Type | Description |
| -------: | :---- | :--- |
| *company_id* | integer | company id |
| *sharing* | integer | distributor sharing |
| *role* | string | customization role name |

### Return Parameters

> Return Success Parameters

<aside class="success">
Success
</aside>

Nothing was returned

> Return Failure Parameters (illegal form input)

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "illegal form input",
    "validation": {
        "name": [
            "required"
        ],
        "deposit": [
            "invalid format"
        ],
        "deposit_sharing": [
            "invalid format"
        ],
        "brand_sharing": [
            "invalid format"
        ],
        "retailer_sharing": [
            "invalid format"
        ]
    }
}
```

> Return Failure Parameters (duplicate retailer relation)

```json
{
    "error_name": "duplicate retailer relation",
    "retailers": [
        {
            "id": 235,
            "name": "7-11"
        }
    ]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: the request does not include the api_key or option_id parameter</li><li>does not signin: the api_key of user does not signin</li><li>not select company yet: the api_key of user need change current company</li><li>company not exist: the api_key of currenct company not exist</li><li>not company member: the api_key of the user is not the company member</li><li>duplicate retailer relation: reatiler has be joined to your other option</li><li>illegal form input: form format does not pass validation</li></ul> |
| validation | object | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input.|
| retailers | array | duplicate retailer list |

| validation | Type | Description |
| -------: | :---- | :--- |
| name | array | <ul><li>required: it’s necessary column for this api</li></ul> |
| deposit | array | <ul><li>invalid format: deposit not boolean</li></ul> |
| deposit_sharing | array | <ul><li>invalid format: deposit  sharing not numeric</li></ul> |
| brand_sharing | array | <ul><li>invalid format: brand sharing not numeric</li></ul> |
| retailer_sharing | array | <ul><li>invalid format: retailer  sharing not numeric</li></ul> |

| retailer | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id |
| name | string | company name |

## Create Option Invitation

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.02 / Joey Huang**

  * Modify Fail Parameters:
    * Apply new structure
  * Modify Fail Parameters:
    * Apply new structure
    * Modify descriptions of error messages
</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/option/invitation/create` |
| Method | `post` |
| Use | to invite retailer |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
	"option_id": 1,
	"company_name": "Zara",
	"given_name": "Jianhua",
	"family_name": "Wang",
	"email": "abc@gmail.com",
	"path": "http://..../"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| option_id | integer |  option id |
| company_name | string | pre-input company name |
| given_name | string |pre-input given name |
| family_name | string | pre-input family name |
| email | string | receiver email |
| path | string | the base path of url which to finish inviting step |

### Return Parameters

> Return Success Parameters

<aside class="success">
Success
</aside>

Nothing was returned

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: the request does not include one or more parameters</li><li>does not signin: the api_key of user does not signin</li><li>not select company yet: the api_key of user need change current company</li><li>company not exist: the api_key of currenct company not exist</li><li>not company member: the api_key of the user is not the company member</li><li>option not exist: the option_id of option not exist</li><li>email is invalid: email format is invalid</li><li>dplicate invitation: duplicate email</li></ul> |

## Reinvite Option Invitation

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.02 / Joey Huang**

  * Modify Fail Parameters:
    * Apply new structure
  * Modify Fail Parameters:
    * Apply new structure
    * Modify descriptions of error messages
</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/option/invitation/reinvite` |
| Method | `post` |
| Use | to reinvite retailer |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
	"option_id": 1,
	"id": 1,
	"path": "http://..../"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| option_id | integer |  option id |
| id | integer | invitation id |
| path | string | the base path of url which to finish inviting step |

### Return Parameters

> Return Success Parameters

<aside class="success">
Success
</aside>

Nothing was returned

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: the request does not include one or more parameters</li><li>does not signin: the api_key of user does not signin</li><li>not select company yet: the api_key of user need change current company</li><li>company not exist: the api_key of currenct company not exist</li><li>not company member: the api_key of the user is not the company member</li><li>option not exist: the option_id of option not exist</li><li>invitation not exist: the id of invitation not exist</li><li>invitation has been finished: invitation has been finished</li></ul> |

## Delete Option Invitation

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.02 / Joey Huang**

  * Modify Fail Parameters:
    * Apply new structure
  * Modify Fail Parameters:
    * Apply new structure
    * Modify descriptions of error messages
</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/option/invitation/delete` |
| Method | `post` |
| Use | to delete invitation |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
	"option_id": 1,
	"id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| option_id | integer |  option id |
| id | integer | invitation id |

### Return Parameters

> Return Success Parameters

<aside class="success">
Success
</aside>

Nothing was returned

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"lack of parameters"
}
```
| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: the request does not include one or more parameters</li><li>does not signin: the api_key of user does not signin</li><li>not select company yet: the api_key of user need change current company</li><li>company not exist: the api_key of currenct company not exist</li><li>not company member: the api_key of the user is not the company member</li><li>option not exist: the option_id of option not exist</li><li>invitation has been finished: invitation has been finished</li></ul> |
