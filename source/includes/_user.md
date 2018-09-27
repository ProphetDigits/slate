
# User

## Sign in

### Description

|Title | Description |
| -------: | :---- |
| URL | `user/signin` |
| Method | `post` |
| Use | Let user sign in and get it api key |
| Notice ||


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
| email | string | The user’s account |
| password | string | The user's password |


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
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| user_id | integer | The user id |

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
|||**lack of parameters:** Some required parameters missing in the request |
|||**does not match:** The account does not sign up yet or the password not match the account |



## Sign out

### Description

|Title | Description |
| -------: | :---- |
| URL | `user/signout` |
| Method | `post` |
| Use | Let user sign out system and deactivated the api key |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :----: | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |


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
| error_name | string | The failed reason which HTTP code is 403 |
|||**lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |


## Sign up with Email only

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/signupwithemailonly` |
| Method | `post` |
| Use | Let user sign up an account with email only in payment |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"email": "cc.lee@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| email | string | The user email |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "api_key": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |


<aside class="warning">
Failure
</aside>

```
{
	"error_name": "illegal form input",
	"validation": {
        "email": ["required"]
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |
| *email* | array | **required:** The data cannot be empty or null |
|||**invalid email:** The data need accord with email format |
|||**dulicate:** The data has already been used |



## Sign up

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/signup` |
| Method | `post` |
| Use | Let user sign up an account |
| Notice ||


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
| given_name | string | The user given name |
| family_name | string | The user family name |
| title | integer | The user gender - 0: Mr. 1: Mrs. |
| email | string | The user email |
| password | string | The user password |


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
| error_name | string | The failed reason which HTTP code is 403 |
|||**lack of parameters:** Some required parameters missing in the request |
|||**illegal form input:** The data validation failed |
| **validation** | **object** | The validation parameter will appear if the error_name is illegal form input |
| *given_name* | array | **required:** The data cannot be empty or null |
| *family_name* | array | **required:** The data cannot be empty or null |
| *title* | array | **required:** The data cannot be empty or null |
|||**invalid title:** The data only can be 0 or 1 |
| *email* | array | **required:** The data cannot be empty or null |
|||**invalid email:** The data need accord with email format |
|||**dulicate:** The data has already been used |
| *password* | array | **required:** The data cannot be empty or null |
|||**word count:** The data need more than 7 words and less than 21 words |



## Search Users

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/search` |
| Method | `post` |
| Use | To search other users |
| Notice | The search data change to full user email from part user email or user name |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"search_text":"test@test.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| search_text | string | The data need input a full user email |


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
| id | integer | The user id |
| email | string | The user email |
| given_name | string | The user given name |
| family_name | string | The user family name |


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
||| **empty text:** The search text cannot be empty |



## Get My Profile

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/profile` |
| Method | `post` |
| Use | To get my profile |
| Notice ||


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
	"id": 1,
	"email": "cc.lee@prophetdigits.com",
	"given_name": "CC",
	"family_name": "Lee",
	"picture": ""
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| email | string | The user email |
| given_name | string | The user given name |
| family_name | string | The user family name |
| picture | string | The user image path |


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



## Forget Password

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/password/forget` |
| Method | `post` |
| Use | To send validation code to user by email |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"email": "cc@b-labs.org"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| email | string | the user account |

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
| error_name | string | The failed reason which HTTP code is 403 |
||| **email not exist:** The email is not signed up yet |



## Resett Password

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/password/cover` |
| Method | `post` |
| Use | To reset user password |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"email": "cc@b-labs.org",
	"passward": "123456",
	"validation_code": "123456"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| email | string | The user account |
| password | string | The user new passward |
| validation_code | string | The validation code which gets from email |

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
| error_name | string | The failed reason which HTTP code is 403 |
|||**illegal form input:** The data validation failed |
|||**email not exist:** The email is not signed up yet |
|||**validation code not match:** The validation code is invalid |
|||**timeout:** The validation code has been expired |
| **validation** | **object** | The validation parameter will appear if the error_name is illegal form input |
| *password* | array | **required:** The data cannot be empty or null |
|||**word count:** The data need more than 7 words and less than 21 words |