
# User

## Sign in

### Description

|Title | Description |
| -------: | :---- |
| URL | `user/signin` | 
| Method | `post` | 
| Use | Let user sign in system from app |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"email": "cc@prophetdigit.com",
	"password": "12345678"
}
```

| Parameter | Type | Description |
| -------: | :----: | :--- |
| email | string | the user’s account |
| password | string | the user's password |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"user_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| user_id | integer | user id |

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
|||**does not match:** the user’s account or password does not match each other|


## Sign out

### Description

|Title | Description |
| -------: | :---- |
| URL | `user/signout` | 
| Method | `post` | 
| Use | Let user sign out system from app |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :----: | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |


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
| (Nothing return) | -- | -- |

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




## Sign up

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/signup` | 
| Method | `post` | 
| Use | Let user sign up an account from app |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"given_name": "CC",
	"family_name": "Lee",
	"title": 1,
	"email": "cc.lee@prophetdigits.com",
	"password": "12345678"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| given_name | string | user’s given name |
| family_name | string | user’s family name |
| title | number | 0: Mr. 1: Mrs. |
| email | string | user's email |
| password | string | user's password |


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

```
{
	"error_name": "illegal form input",
	"validation": {
		"given_name": ["required"],
		"password": ["word count"]
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty. **Valid Value:**| 
|||**lack of parameters:** some input parameters missing, not in the request|
|||**illegal format input:** form format does not pass validation|
| **validation** | object |  if the error_name is illegal form input, web backend should assign the name of the wrong type for each error input **Valid Value(option):**| 
| given_name | array | **required:** it’s necessary parameter for this api |
| family_name | array | **required:** it’s necessary parameter for this api |
| title | array | **required:** it’s necessary parameter for this api |
|||**invalid title:** the text need accord with boolean|
| email | array | **required:** it’s necessary parameter for this api |
|||**invalid email:** the text need accord with email format|
|||**dulicate:** the text has already been taken|
| password | array | **required:** it’s necessary parameter for this api |
|||**word count:** the word count too more or too less|



## Search User

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/search` | 
| Method | `post` | 
| Use |  |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"search_text":"Wang"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| search_text | string | key word about user name or user email |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"users": [{
		"id": 1,
		"email": "a@gmail.com",
		"given_name": "Jianhua",
		"family_name": "Wang"
	}, {
		"id": 2,
		"email": "b@gmail.com",
		"given_name": "Jianhua",
		"family_name": "Wang"
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **users** | array | users related to search text |
| id | integer | user's id |
| email | string | user's email |
| given_name | string | user's given name |
| family_name | string | user's family name |


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
|||**empty text:** search text can't be empty|
|||**does not signin:** user does not signin|


## My Profile

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/profile` | 
| Method | `post` | 
| Use | to get my profile |
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
	"id": 1,
	"email": "cc.lee@prophetdigits.com",
	"given_name": "CC",
	"family_name": "Lee",
	"picture": ""
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | user id |
| email | string | user email |
| given_name | string | user given name |
| family_name | string | user family name |
| picture | string | user image path |


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



## Upload Image

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/upload/image` | 
| Method | `post` | 
| Use | to upload image |
| Notice |  |


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
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
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
| file_name | string | file name which just uploaded  |


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
|||**not image:** type is not image|
|||**invalid image format:**|


## Delete Image

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/delete/image` | 
| Method | `post` | 
| Use | to delete image |
| Notice |  |


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
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| file_name | string | image name |


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

