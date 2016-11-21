
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