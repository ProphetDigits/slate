# customization

## Customization List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/customization/list` |
| Method | `post` |
| Use | to get customization list |
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
| target_company_id | integer | company id which user want get customization list |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"customizations": [{
		"id": 1,
		"name": "Color",
		"display_name": "Color"
	}, {
		"id": 2,
		"name": "Size",
		"display_name": "Size"
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **customizations** | array |  |
| id | integer | customization  id |
| name | string | customization  name |
| display_name | string | customization  display name |

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
|||**no permission:**|


## Create Customization

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/customization/create` |
| Method | `post` |
| Use | to create customization |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"name": "color",
	"display_name": "Color",
	"description": "",
	"categories": [1, 2, 3, 7],
	"values": [{
		"name": "red",
		"price": 0
	}, {
		"name": "blue",
		"price": 100
	}, {
		"name": "Yellow",
		"price": 100
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| name | string | customization’s name |
| display_name | string | customization’s display name |
| description | string | customization’s description |
| categories | array | customization belongs to which categories |
| **values** | **array** | customization’s values |
| name | string | name of customization option |
| price | number | extra price if select this customization value |


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
|||**no permission:**|
|||**illegal form input:** form format does not pass validation|
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| name | array | **required:** it’s necessary parameter |
|||**dulicate:** the name has already been taken|
| display_name | array | **required:** it’s necessary parameter |
| categories | array | **not exist:** incorrect category id in the category set |
|||**root category:** cannot connect root category|


## Customization  Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/customization/detail` |
| Method | `post` |
| Use | to get customization detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"target_company_id": 1,
	"customization_id": 2
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| target_company_id | integer | company id which user want get customization list |
| customization_id | integer | customization's id |


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
		"name": "red",
		"price": 0
	}, {
		"id": 2,
		"name": "blue",
		"price": 100
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **customization** | array |  |
| id | integer | customiation  id |
| name | string | customiation  name |
| display_name | string | customiation  display name |
| description | string | customization  description |
| **categories** | **array** | customizatino belongs to which categories |
| id | integer | category id |
| name | string | category name |
| **values** | **array** | customizatino’s values |
| id | integer | id of customization option |
| name | string | name of customization option |
| price | number |  extra price(default currency) if select this customization value |

<aside class="warning">
Failure
</aside>

```json
{

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
|||**no permission:**|


## Edit Customization

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/customization/edit` |
| Method | `post` |
| Use | to edit customization |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"name": "color",
	"display_name": "Color",
	"description": "",
	"categories": [1, 2, 3, 7],
	"values": [{
		"id": 1,
		"name": "Red",
		"price": 0
	}, {
		"id": 2,
		"name": "Blue",
		"price": 100
	},{
		"id": 3,
		"name": "Yellow",
		"price": 100
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| customization_id | integer | customization’s id |
| name | string | customization’s name |
| display_name | string | customization’s display name |
| description | string | customization’s description |
| categories | array | link relation with category |
| **values** | **array** |  customizatino’s option |
| id | integer | id of value, new value can ignore it or set 0|
| name | string | name of value |
| price | double |  price of value |

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
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not company member:** the user is not the company member|
|||**illegal form input:** validate unsuccess, the exact error message will in validation of data|
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| name | array | **required:** it’s necessary parameter |
|||**dulicate:** the name has already been taken|
| display_name | array | **required:** it’s necessary parameter |
| categories | array | **not exist:** incorrent category id in the category set |
|||**root category:** cannot connect root category|


## Delete Customization

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/customization/delete` |
| Method | `post` |
| Use | to delete customization |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"cusotmization_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| cusotmization_id | integer | customization’s id |


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
|||**no permission:**|
|||**customization using**|
