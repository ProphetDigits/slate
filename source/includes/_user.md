# User

## Sign in

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/signin` |
| Method | `post` |
| Use | Let user sign in and get it api key |
| Notice | |


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


> Return Success Parameters

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
| api_key | string | The identity token of user |
| user_id | integer | The user id |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not match: the account has not exist or the password not match the account</li></ul> |



## Sign out

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/signout` |
| Method | `post` |
| Use | Let user sign out system and deactivated the api key |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :----: | :--- |
| api_key | string | The identity token of user |


### Return Parameters

<aside class="success">
Success
</aside>

Nothing was returned

<aside class="warning">
Failure
</aside>

There is no failure



## Sign up with Email only

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/signupwithemailonly` |
| Method | `post` |
| Use | Let user sign up with email only |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"email": "tester@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| email | string | The user email |


> Return Success Parameters

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
| api_key | string | The identity token of user |

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>illegal_form_input: the input does not pass validation</li></ul> |
| validation | object (option) | If the err_name is 'illegal_form_input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| email | array (option) | required: <ol><li>The email cannot be empty or null</li></ol> invalid email: <ol><li>The data need accord with email format</li></ol> duplicate: <ol><li>The email has already been used</li></ol> |



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
	"given_name": "Tester",
	"family_name": "Prophetdigit",
	"title": 1,
	"email": "tester@prophetdigits.com",
	"password": "12345678"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| given_name | string | The user given name |
| family_name | string | The user family name |
| title | integer | The user gender <ul><li>0: Mr.</li><li>1: Mrs.</li></ul> |
| email | string | The user email |
| password | string | The user password |


### Return Parameters

<aside class="success">
Success
</aside>

Nothing was returned

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>illegal_form_input: the input does not pass validation</li></ul> |
| validation | object (option) | If the err_name is 'illegal_form_input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| given_name | array (option) | required: <ol><li>The given_name cannot be empty or null</li></ol> |
| family_name | array (option) | required: <ol><li>The family_name cannot be empty or null</li></ol> |
| title | array (option) | required: <ol><li>The title cannot be empty or null</li></ol> invalid title: <ol><li>The title only can be 0 or 1</li></ol> |
| email | array (option) | required: <ol><li>The email cannot be empty or null</li></ol> invalid email: <ol><li>The data need accord with email format</li></ol> duplicate: <ol><li>The email has already been used</li></ol> |
| password | array (option) | required: <ol><li>The family_name cannot be empty or null</li></ol> word count: <ol><li>The password need more than 7 words and less than 21 words</li></ol> |



## Search Users

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/search` |
| Method | `post` |
| Use | To search user |
| Notice | Searching user should input full email |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"search_text":"tester@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| search_text | string | The user email |


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"users": [{
		"id": 1,
		"email": "tester@prophetdigits.com",
		"given_name": "Tester",
		"family_name": "Prophet"
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| users | array | Collection of user |

| user | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user's id |
| email | string | The user's email |
| given_name | string | The user's given name |
| family_name | string | The user's family name |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: The user does not signin</li><li>empty text: The search text cannot be empty</li></ul> |



## Get My Profile

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/profile` |
| Method | `post` |
| Use | To get my profile |
| Notice | |


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
	"id": 1,
	"email": "tester@prophetdigits.com",
	"given_name": "Tester",
	"family_name": "Prophet",
	"picture": ""
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user's id |
| email | string | The user's email |
| given_name | string | The user's given name |
| family_name | string | The user's family name |
| picture | string | The user's image path |

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



## Forget Password

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/password/forget` |
| Method | `post` |
| Use | To send validation code to user by email |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
	"email": "tester@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| email | string | The user's email |


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
	"error_name": "email not exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>email not exist: the email is not signed up yet</li></ul> |



## Reset Password

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/password/cover` |
| Method | `post` |
| Use | To reset user password |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
	"email": "tester@prophetdigits.com",
	"password": "123456",
	"validation_code": "123456"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| email | string | The user's account |
| password | string | The user's new password |
| validation_code | string | The validation code which takes from email |


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
	"error_name": "illegal form input",
	"validation": {
		"password": ["required"]
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>email not exist: the email is not signed up yet</li><li>validation code not match: the validation_code is invalid</li><li>timeout: the validation code has been expired</li><li>illegal form input: the input does not pass validation</li></ul> |
| validation | object (option) | If the err_name is 'illegal_form_input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| password | array (option) | required: <ol><li>The password cannot be empty or null</li></ol> word count: <ol><li>The password need more than 7 words and less than 21 words</li></ol> |
| validation_code | array (option) | required: <ol><li>The validation_code cannot be empty or null</li></ol> |