# Example

## Api Name

### Description

| Title | Description |
| -------: | :---- |
| URL | `company/{item_id}` |
| Method | `post` |
| Use |  |
| Notice |  |


### Url Parameters

| Parameter | Type | Description |
| -------: | :---- | :--- |
| item_id | integer | Item id |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "categories": [1, 2, 3],
    "specs": [{
        "id": 1,
        "image": {
            "name": "xxx.jpg",
            "cover": true
        }
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| categories | array | Collection of category id |
| specs | array | Collection of spec |

| spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | Spec id |
| image | object | Cover image of spec |

| spec.image | Type | Description |
| -------: | :---- | :--- |
| name | string | Filename |
| cover | boolean | Is cover image or not |


### Return Parameters

<aside class="success">
Success
</aside>

Nothing was returned

> Return Success Parameters

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

```json
{
    "error_name": "illegal_form_input",
    "validation": {
        "name": ["invalid"],
        "number": ["required"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: the api_key is invalid</li><li>not_select_company: the user has not select current company</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | If the error_name is 'illegal_form_input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| name | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> invalid: <ol><li>The data not string</li></ol> |
| number | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> |