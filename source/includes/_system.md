
# System

## System Currency List

### Description

| Title | Description |
| -------: | :---- |
| URL | `system/currency/list` |
| Method | `post` |
| Use | to get all currencies in the system |
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
	"currencies":[{
		"id": 1,
		"name": "CHF"
	}, {
		"id": 2,
		"name": "EUR"
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **currencies** | array | all currencies in the system. Order by name from A-Z |
| id | number | currency id |
| name | string | currency name |


<aside class="warning">
Failure
</aside>

```
{
	"error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|


## System Country List

### Description

| Title | Description |
| -------: | :---- |
| URL | `system/country/list` |
| Method | `post` |
| Use | to get all countrues in the system |
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
	"currencies":[{
		"id": 115,
		"name": "Japan"
	}, {
		"id": 228,
		"name": "Taiwan"
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **currencies** | array | all countries in the system |
| *id* | number | country id |
| *name* | string | country name |


<aside class="warning">
Failure
</aside>

```
{
	"error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|