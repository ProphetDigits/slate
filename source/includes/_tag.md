# Tag

## Get Tag list 

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.05.05 /Joey Huang**

  * Move Get Tag list to Tag
  * Modify the error_name messages

  **2020.04.29 /Balder**

  * Add Success Parameter
    * tags

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/tag/list |
| Method | `post` |
| Use | To get tag list of company |
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
	"tags": [{
		"id": "1",
		"name": "Sample"	
	}, {
		"id": "2",
		"name": "Prototype"	
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| tags | array | Collection of tag, order by A-Z |

| tag | Type | Description |
| -------: | :---- | :--- |
| id | integer | the tag id |
| name | string | The tag name |

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: the user does not signin</li><li>not_select_company: current company not select</li></ul> |
