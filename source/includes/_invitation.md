# Invitation

## Get Retailer Invitation Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `invitation/retailer/detail` |
| Method | `post` |
| Use | to get invitation detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "hash_id": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| hash_id | string | hash value |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "company_name": "Awesome",
    "given_name": "Jianhua",
    "family_name": "Wang",
    "email": "abc@gmail.com",
    "registered_step": "finished",
    "user": {
        "id": 1,
        "email": "a@gmail.com"
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| company_name | string | pre-input company name |
| given_name | string |pre-input given name |
| family_name | string | pre-input family name |
| email | string | receiver email |
| registered_step | string | registered step (signup, create company, finished) |
| **user** | **object** | registered user |
| *id* | integer | registered user id |
| *email* | string | registered user email |


<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"invitation not exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | the name of the wrong type. |
||| **invitation not exist:** invitation not exist |


## Set Retailer Invitation

### Description

| Title | Description |
| -------: | :---- |
| URL | `invitation/retailer/edit` |
| Method | `post` |
| Use | to edit invitation |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "hash_id": "e4cbcdc2faff41a7e311",
    "api_key": "e4cbcdc2faff41a7e311",
    "company_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| hash_id | string | hash value |
| api_key | string | api key which user registered |
| company_id | integer (option) | company id  which user has created |

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
||| **invitation not exist:** invitation not exist |
||| **account not exist:** account not register yet |
||| **company not exist:** company not create yet |
||| **invalid account:** login account not register account |
||| **finished:** invitation has been finished |