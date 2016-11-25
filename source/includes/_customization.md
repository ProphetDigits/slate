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
