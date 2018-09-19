# Spec2

## Get Spec2 List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/list` |
| Method | `post` |
| Use | to get spec list |
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
| api_key | string | System gives it after user sign in |


> Return Parameters When Success

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "specs": [{
        "id": 1,
        "name": "spec name",
        "display_name": "spec 1",
        "part": true
    }, {
        "id": 2,
        "name": "spec name2",
        "display_name": "spec 1",
        "part": false
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| specs | array | The spec list |

| specs | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| part | boolean | The spec is part or not |


> Return Parameters When Failure

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
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li></ul> |



## Get Spec2 Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/detail` |
| Method | `post` |
| Use | to get spec detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | System gives it after user sign in |
| id | integer | The id of spec |


> Return Parameters When Success

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "spec": {
        "id": 1,
        "name": "color",
        "display_name": "color",
        "comment": "",
        "part": true,
        "categories": [{
            "id": 1,
            "name": "root"
        }],
        "values": [{
            "id": 1,
            "name": "red",
            "display_name": "Red",
            "price": 10,
            "part_number": "",
            "supplier_number": "",
            "description": "",
            "comment": ""
        }]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| spec | object | The spec detail |

| spec | | |
| -------: | :---- | :--- |
| Parameter | Type | Description |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| comment | string | The comment of spec |
| part | boolean | The spec is part or not |
| categories | array | The set of category |
| values | array | The set of value of spec |

| spec_category | | |
| -------: | :---- | :--- |
| id | integer | The id of category |
| name | string | The name of category |

| spec_value | | |
| -------: | :---- | :--- |
| id | integer | The id of value |
| name | string | The name is for brand to identify spec value |
| display_name | string | The display name is to displayed for consumer |
| price | number | The price of value, the currency is default by company |
| part_number | string | The part number of value |
| supplier_number | string | The supplier number of value |
| description | string | The description is to displayed for consumer |
| comment | string | The comment is a note for brand |


> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"not_sign_in"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>spec_not_found:<ol><li>The spec is not exist</li><li>The spec does not belongs to current company</li></ol></li></ul> |



## Create Spec2

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/create` |
| Method | `post` |
| Use | to create spec |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "name": "color",
    "display_name": "Color",
    "comment": "",
    "part": false,
    "categories": [1, 2, 3],
    "values": [{
        "name": "red",
        "display_name": "Red",
        "price": 10,
        "part_number": "",
        "supplier_number": "",
        "description": "",
        "comment": ""
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | System gives it after user sign in |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| comment | string | The comment of spec |
| part | boolean | The spec is part or not<br />Accepted input are true, false, 1, 0, "1", and "0" |
| categories | array | The set of id of category |
| values | array | The set of value of spec |

| spec_value | | |
| -------: | :---- | :--- |
| name | string | The name is for brand to identify spec value |
| display_name | string | The display name is to displayed for consumer |
| price | number | The price of value, the currency is default by company |
| part_number | string | The part number of value |
| supplier_number | string | The supplier number of value |
| description | string | The description is to displayed for consumer |
| comment | string | The comment is a note for brand |


> Return Parameters When Success

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "spec": {
        "id": 1
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **spec** | *object* | |
| id | integer | The id of spec |


> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "illegal_form_input",
    "validation": {
        "display_name": ["required"],
        "categories": ["invalid"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| **validation** | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |
| name | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| display_name | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| comment | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| part | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not boolean</li></ol> |
| categories | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not array</li><li>The id of category is not exist</li><li>The category is not belongs to the current company </li></ol> |
| values | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not array</li></ol> |
| values.*.name | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.*.display_name | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.*.price | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not number</li></ol> |
| values.*.part_number | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.*.supplier_number | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.*.description | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.*.comment | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |


## Edit Spec2

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/edit` |
| Method | `post` |
| Use | to edit spec |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "id": 1,
    "name": "color",
    "display_name": "Color",
    "categories": [1, 2, 3],
    "values": [{
        "id": 1,
        "name": "red",
        "display_name": "Red",
        "price": 10,
        "part_number": "",
        "supplier_number": "",
        "description": "",
        "comment": ""
    }, {
        "id": 0,
        "name": "blue",
        "display_name": "Blue",
        "price": 10,
        "part_number": "",
        "supplier_number": "",
        "description": "",
        "comment": ""
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | System gives it after user sign in |
| id | integer | The id of spec |
| name | string (option) | The name of spec |
| display_name | string (option) | The display name of spec |
| comment | string (option) | The comment of spec |
| part | boolean (option) | The spec is part or not<br />Accepted input are true, false, 1, 0, "1", and "0" |
| categories | array (option) | The set of id of category |
| values | array (option) | The set of value of spec |

| spec_value | | |
| -------: | :---- | :--- |
| id | integer | The id of value <br />It indicate adding value if id is 0 |
| name | string | The name is for brand to identify spec value |
| display_name | string | The display name is to displayed for consumer |
| price | number | The price of value, the currency is default by company |
| part_number | string | The part number of value |
| supplier_number | string | The supplier number of value |
| description | string | The description is to displayed for consumer |
| comment | string | The comment is a note for brand |


> Return Parameters When Success

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "spec": {
        "id": 1
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **spec** | *object* | |
| id | integer | The id of spec |


> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "illegal_form_input",
    "validation": {
        "name": ["dulicate"],
        "display_name": ["required"],
        "categories": ["not exist"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>spec_not_found:<ol><li>The spec is not exist</li><li>The spec does not belongs to current company</li></ol></li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| **validation** | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |
| name | array (option) | required: <ol><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| display_name | array (option) | required: <ol><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| comment | array (option) | invalid: <ol><li>The data is not string</li></ol> |
| part | array (option) | invalid: <ol><li>The data is not boolean</li></ol> |
| categories | array (option) | invalid: <ol><li>The id of category is not exist</li><li>The category is not belongs to the current company </li></ol> |
| values | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not array</li></ol> |
| values.*.name | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.*.display_name | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.*.price | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not number</li></ol> |
| values.*.part_number | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.*.supplier_number | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.*.description | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.*.comment | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |