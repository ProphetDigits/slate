# Spec2

## Get Spec2 List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/list` |
| Method | `post` |
| Use | to get spec list |
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
| api_key | string | System gives it after user sign in |


> Return Parameters When Success

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"specs": [{
		"id": 1,
		"name": "spec name",
		"display_name": "spec 1",
		"part": true
	}, {
		"id": 2,
		"name": "spec name2",
		"display_name": "spec 1",
		"part": false
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **specs** | array |  |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| part | boolean | The spec is part or not |


> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
	"error_name": "not_sign_in"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ol><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li></ol> |



## Get Spec2 Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/detail` |
| Method | `post` |
| Use | to get spec detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | System gives it after user sign in |
| id | integer | The id of spec |


> Return Parameters When Success

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"spec": {
		"id": 1,
		"name": "color",
		"display_name": "color",
		"comment": "",
		"part": true,
		"categories": [{
			"id": 1,
			"name": "root"
		}]
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **spec** | object | |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| comment | string | The comment of spec |
| part | boolean | The spec is part or not |
| **categories** | *array* | The set of category |
| id | integer | The id of category |
| name | string | The name of category |



> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
	"error_name":"not_sign_in"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ol><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li></ol> |



## Create Spec2

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/create` |
| Method | `post` |
| Use | to create spec |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"name": "color",
	"display_name": "Color",
	"comment": "",
	"part": false,
	"categories": [1, 2, 3]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | System gives it after user sign in |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| comment | string | The comment of spec |
| part | boolean | The spec is part or not |
| categories | array | The set of id of category |


> Return Parameters When Success

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"spec": {
		"id": 1
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **spec** | *object* | |
| id | integer | The id of spec |


> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
	"error_name": "illegal form input",
	"validation": {
		"display_name": ["required"],
		"categories": ["invalid"]
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ol><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>illegal form input: The form format does not pass validation</li></ol> |
| **validation** | object (option) | if the err_name is 'illegal form input', system should assign the name of wrong type for each error input |
| name | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol> |
| display_name | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol> |
| part | array (option) | invalid: <ol><li>The data is not boolean</li></ol> |
| categories | array (option) | invalid: <ol><li>The id of category is not exist</li><li>The category is not belongs to the current company </li></ol> |

