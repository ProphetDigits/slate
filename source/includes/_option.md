# Option

## Option List

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
| **options** | array |  |
| id | integer |  option id |
| name | string |  option name |
| **company** | **object** |  |
| *id* | integer | company id |
| *name* | string | company name |
| start_time | timestamp | timestamp/second |
| end_time | timestamp | timestamp/second |
| status | boolean | is option executable |

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
| error_name | string | the name of the wrong type. |
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:**|


## Create Option

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
| **retailers** | **array** | company id set |
| **distributors** | **array** | |
| company_id | integer | company  id |
| sharing | integer | distributor sharing |
| role | string | customization role name |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| (Nothing return) | - | - |

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
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
||| **lack of parameters:** the request does not include the necessary parameters |
||| **does not signin:** user does not signin |
||| **not select company yet:** user need change current company |
||| **company not exist:** currenct company not exist |
||| **not company member:** the user is not the company member |
||| **no permission:** |
||| **duplicate retailer relation:** reatiler has be joined to your other option |
||| **illegal form input:** form format does not pass validation |
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| name | array | **required:** it’s necessary column for this api |
| deposit | array | **invalid format:** deposit not boolean |
| deposit_sharing | array | **invalid format:** deposit  sharing not numeric |
| brand_sharing | array | **invalid format:** brand sharing not numeric |
| retailer_sharing | array | **invalid format:** retailer  sharing not numeric |


## Option   Detail

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
    }
}
```

| Parameter | Type | Description ||
| -------: | :---- | :--- |:--|
| name | string | option  name |
| start_time | timestamp | timestamp/second |
| end_time | timestamp | timestamp/second |
| status | boolean | is option  executable |
| **status_message** | **object** | the reasons why status is false |
| *start_time* | **array** | error reasons |
| *required* | string | it’s necessary to option |
| *end_time* | **array** | error reasons |
| *expired* | string | time is expired |
| *active*| **array** | error reasons |
| *no* | string | option is close |
| *sharing* | **array** | error reasons |
| *invalid value* | string | total sharing is not equal to 100 |
| deposit | boolean | the result that brand want retailer to pay deposit |
| deposit_sharing | integer | deposit sharing |
| brand_sharing | integer | brand sharing |
| retailer_sharing | integer | retailer sharing |
| **retailers** | **array** | |
| *id* | integer | company id |
| *name* | string | company name |
| **distributors** | **array** | |
| *id* | integer | company id |
| *name* | string | company name |
| *sharing* | integer | distributor sharing |
| *role* | string | customization role name |
| **distributors** | **object** | |
| *id* | integer | company id |
| *name* | string | company name |

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
| error_name | string | the name of the wrong type. |
||| **lack of parameters:** some input parameters missing, not in the request |
||| **does not signin:** user does not signin |
||| **not select company yet:** user need change current company |
||| **company not exist:** currenct company not exist |
||| **not company member:** the user is not the company member |
||| **no permission:** |
||| **option not exist:** |


## Edit Option

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
| **retailers** | **array** | company id set |
| **distributors** | **array** | |
| *company_id* | integer | company id |
| *sharing* | integer | distributor sharing |
| *role* | string | customization role name |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| (Nothing return) | - | - |


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
| error_name | string | the name of the wrong type. |
||| **lack of parameters:** some input parameters missing, not in the request |
||| **does not signin:** user does not signin |
||| **not select company yet:**   user need change current company |
||| **company not exist:** currenct company not exist |
||| **not company member:** the user is not the company member |
||| **no permission:** |
||| **duplicate retailer relation:** reatiler has be joined to your other option |
|||**illegal form input:**  form format does not pass validation option not exist |
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| name | array | **required:** it’s necessary column for this api |
| deposit | array | **required:**  deposit not boolean |
| deposit_sharing | array | **invalid format:**  deposit sharing not numeric |
| brand_sharing | array | **invalid format:**  brand  sharing not numeric |
| retailer_sharing | array | **invalid format:**  retailer  sharing not numeric |
