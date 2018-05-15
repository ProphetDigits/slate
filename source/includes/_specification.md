# Specification

## Specification List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec/list` |
| Method | `post` |
| Use | to get specification list |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"target_company_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| target_company_id | integer | company id which user want get spec list |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"specs": [{
		"id": 1,
		"name": "spec name",
		"display_name": "spec 1"
	}, {
		"id": 2,
		"name": "spec name2",
		"display_name": "spec 1"
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **specs** | array |  |
| id | integer | spec id |
| name | string | spec name |
| display_name | string | spec display name |

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
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|


## Create Specification

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec/create` |
| Method | `post` |
| Use | to create specification |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"name": "color",
	"display_name": "Color",
	"categories": [1, 2, 3],
	"values": [{
		"name": "red"
	}, {
		"name": "blue"
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| name | string | spec name |
| display_name | string | spec display name |
| description | string | spec description |
| categories | array | category id set |
| **values** | **array** | spec value set |
| name | string | value name |


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
	"validation": {
		"name": ["dulicate"],
		"display_name": ["required"],
		"categories": ["not exist"]
	},
	"error_name": "illegal form input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**illegal form input:** form format does not pass validation|
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| name | array | **required:** it’s necessary parameter |
|||**dulicate:** the name has already been taken|
| display_name | array | **required:** it’s necessary parameter |
| categories | array | **not exist:** incorrent category id in the category set |


## Specification Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec/detail` |
| Method | `post` |
| Use | to show specification detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"target_company_id": 1,
	"spec_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| target_company_id | integer | company id which user want get spec list |
| spec_id | integer | spec id |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"id": 1,
	"name": "color",
	"display_name": "color",
	"description": "",
	"categories": [{
		"id": 1,
		"name": "root"
	}],
	"values": [{
		"id": 1,
		"name": "red"
	}, {
		"id": 2,
		"name": "blue"
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **specs** | array |  |
| id | integer | spec id |
| name | string | spec name |
| display_name | string | spec display name |
| description | string | spec description |
| **categories** | **array* | category id set |
| id | integer | category id |
| name | string | category name |
| **values** | **array** | spec value set |
| id | integer | value id |
| name | string | value name |

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
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|



## Edit Specification

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec/edit` |
| Method | `post` |
| Use | to edit specification |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"spec_id": 1,
	"name": "color",
	"display_name": "Color",
	"categories": [1, 2, 3],
	"values": [{
		"name": "red"
	}, {
		"name": "blue"
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| spec_id | integer | spec id |
| name | string | spec name |
| display_name | string | spec display name |
| description | string | spec description |
| categories | array | category id set |
| **values** | **array** | spec value set |
| id | integer | value id, new value can ignore it or set 0 |
| name | string | value name |


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
	"validation": {
		"name": ["dulicate"],
		"display_name": ["required"],
		"categories": ["not exist"]
	},
	"error_name": "illegal form input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**illegal form input:** form format does not pass validation|
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| name | array | **required:** it’s necessary parameter |
|||**dulicate:** the name has already been taken|
| display_name | array | **required:** it’s necessary parameter |
| categories | array | **not exist:** incorrent category id in the category set |



## Delete Specification

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec/delete` |
| Method | `post` |
| Use | to delete specification |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"spec_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| spec_id | integer | spec id |


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
	"error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
