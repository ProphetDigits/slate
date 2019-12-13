
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

```json
{
	"error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li></ul> |



## Get System Country List

### Description

| Title | Description |
| -------: | :---- |
| URL | `system/country/list` |
| Method | `post` |
| Use | To get all countries in the system |
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
| countries | array | Collection of country |

| country | Type | Description |
| -------: | :---- | :--- |
| id | integer | The country id |
| name | string | The country name |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li></ul> |



## Get System Country List Without Signin

### Description

| Title | Description |
| -------: | :---- |
| URL | `system/country/list` |
| Method | `get` |
| Use | To get all countries in the system |
| Notice |  |


### Input Parameters

There is no parameters


> Return Success Parameters

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
| countries | array | Collection of country |

| country | Type | Description |
| -------: | :---- | :--- |
| id | integer | The country id |
| name | string | The country name |

<aside class="warning">
Failure
</aside>

There is no failure



## Upload Image

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/upload/image` |
| Method | `post` |
| Use | To upload image |
| Notice | |


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
| api_key | string | The identity token of user |
| image | string | The base64 encode image and Mime type. Image format require as jpg, jpeg, png, gif |


> Return Success Parameters

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
| file_name | string | The temporary filename |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not image: the type of MIME type is not image</li><li>invalid image format: the subtype of MIME type is not jpg, jpeg, png and gif</li></ul> |



## Delete Image

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/delete/image` |
| Method | `post` |
| Use | To delete image |
| Notice | |


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
| api_key | string | The identity token of user |
| file_name | string | The temporary filename after upload image |


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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li></ul> |
