
# System

## Get System Currency List

### Description

| Title | Description |
| -------: | :---- |
| URL | `system/currency/list` |
| Method | `post` |
| Use | To get all currencies in the system |
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
| api_key | string | The identity token of user |


> Return Success Parameters

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
| currencies | array | Collection of currency. Order by name from A-Z |

| currency | Type | Description |
| -------: | :---- | :--- |
| id | integer | The currency id |
| name | string | The currency name |

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li></ul> |



## System Country List

### Description

| Title | Description |
| -------: | :---- |
| URL | `system/country/list` |
| Method | `post` |
| Use | to get all countries in the system |
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
| api_key | string | An unique token after user sign in, then user can use it to request data from API |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"countries":[{
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
| **countries** | **array** | All countries in the system |
| *id* | number | The country id |
| *name* | string | The country name |


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
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |


## System Country List Without Sign In

### Description

| Title | Description |
| -------: | :---- |
| URL | `system/country/list` |
| Method | `get` |
| Use | to get all countries in the system |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"countries":[{
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
| **countries** | **array** | All countries in the system |
| *id* | number | The country id |
| *name* | string | The country name |


<aside class="warning">
Failure
</aside>

```
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |


## Upload Image

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/upload/image` |
| Method | `post` |
| Use | To upload image for company and item |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"image":"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQAAAk..."
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| image | string | base64 encode image string. Image format require as jpg, jpeg, png, gif |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"file_name":"asdasdasds.jpg"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| file_name | string | The filename which just uploaded  |


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
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **not image:** The MIME-type is not image |
||| **invalid image format:** The subtype of MIME-type is not jpg, jpeg, png and gif |


## Delete Image

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/delete/image` |
| Method | `post` |
| Use | To delete image |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"file_name":"asdasdasds.jpg"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| file_name | string | The filename which given by system after upload image |


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
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
