# Invitation

## Get Retailer Invitation Detail

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.12.31 / Joey Huang**

  * Modify Success Parameters:
    * Break user object to a sub-table
  * Modify Fail Parameters:
    * Apply new structure
</details>

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

### Return Parameters

> Return Success Parameters

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
| user | object | registered user |

| user | Type | Description |
| -------: | :---- | :--- |
| id | integer | registered user id |
| email | string | registered user email |

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>invitation not exist: the hash_id of invitation not exist</li></ul>|

## Set Retailer Invitation

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.12.31 / Joey Huang**

  * Modify Success Parameters:
    * Apply new structure
  * Modify Fail Parameters:
    * Apply new structure
</details>

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

### Return Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>invitation not exist: the hash_id of invitation not exist</li><li>account not exist: the api_key of account not register yet</li><li>company not exist: the company_id of company not create yet</li><li>invalid account: login account not register account</li><li>finished: invitation has been finished</li></ul> |