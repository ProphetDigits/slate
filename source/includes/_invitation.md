# Invitation

## Get Invitation Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `invitation/detail` |
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
||| **option not exist:** option not exist |
||| **invitation not exist:** invitation not exist |


## Set Invitation

### Description

| Title | Description |
| -------: | :---- |
| URL | `invitation/edit` |
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
| api_key | string | api key  which user login |
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
||| **lack of parameters:** some input parameters missing, not in the request |
||| **invitation not exist:** invitation not exist |
||| **account not exist:** account not register yet |
||| **company not exist:** company not create yet |
||| **invalid account:** login account not register account |