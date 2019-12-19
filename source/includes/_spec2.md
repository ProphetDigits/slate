# Spec2

## Spec2 List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/list` |
| Method | `post` |
| Use | To get spec2 list |
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
    "specs": [{
        "id": 1,
        "name": "spec name",
        "display_name": "spec 1",
        "part": true,
        "values": [{
            "id": 1,
            "name": "value1"
        }]
    }, {
        "id": 2,
        "name": "spec name2",
        "display_name": "spec 1",
        "part": false,
        "values": []
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| specs | array | Collection of spec |

| spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| part | boolean | The tag that is it part or not |
| values | array | Collection of spec value |

| spec.value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of value |
| name | string | The name is for brand to identify spec value |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: the api_key is invalid</li><li>not_select_company: the user has not select current company</li></ul> |



## Spec2 Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/detail` |
| Method | `post` |
| Use | To get spec2 detail |
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
| api_key | string | The identity token of user |
| id | integer | The spec2 id |


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "spec": {
        "id": 1,
        "name": "Second hand",
        "display_name": "Second hand",
        "comment": "",
        "part": true,
        "categories": [{
            "id": 1,
            "name": "root"
        }],
        "compositions": [{
            "id": 2,
            "name": "color",
            "display_name": "color",
            "part": true
        }],
        "values": [{
            "id": 1,
            "name": "small multiply",
            "display_name": "Small Multiply",
            "price": 10,
            "part_number": "",
            "supplier_number": "",
            "description": "",
            "comment": "",
            "sofe_delete": false,
            "compositions": [{
                "id": 2,
                "name": "color",
            	"display_name": "color",
                "value": {
                    "id": 1,
                    "name": "red",
            		"display_name": "red"
                }
            }]
        }]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| spec | object | The spec detail |

| spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| comment | string | The comment of spec |
| part | boolean | The spec is part or not |
| categories | array | Collection of category |
| compositions | array | Collection of spec2 |
| values | array | Collection of spec2 value |

| spec.category | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of category |
| name | string | The name of category |

| spec.composition | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 |
| name | string | The name of spec2 |
| display_name | string | The display name of spec2 |
| part | boolean | The tag that is it part or not |

| spec.value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |
| name | string | The name of spec2 value |
| display_name | string | The display name of spec2 value |
| price | number | The price of value, the currency is default by company |
| part_number | string | The part number of spec2 value |
| supplier_number | string | The supplier number of spec2 value |
| description | string | The description of spec2 value |
| comment | string | The comment of spec2 value |
| sofe_delete | boolean | The tag that is it deleted |
| compositions | array | Collection of value composition of spec2 |

| spec.value.composition | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 |
| name | string | The name of spec2 |
| display_name | string | The display name of spec2 |
| value | object | The setting of composition value |

| spec.value.composition.value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |
| name | string | The name of spec2 value |
| display_name | string | The display name of spec2 value |


> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: the api_key is invalid</li><li>not_select_company: the user has not select current company</li><li>spec_not_exist: the spec is not exist</li><li>no_option: the current company of user does not have option with company of spec</li></ul> |



## Create Spec2

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/create` |
| Method | `post` |
| Use | To create spec |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "name": "Second hand",
    "display_name": "Second hand",
    "comment": "",
    "part": false,
    "categories": [1, 2, 3],
    "compositions": [2],
    "values": [{
        "name": "small multiply",
        "display_name": "Small Multiply",
        "price": 10,
        "part_number": "",
        "supplier_number": "",
        "description": "",
        "comment": "",
        "compositions": [{
            "id": 2,
            "value": 1
        }]
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| name | string | The name of spec2 |
| display_name | string | The display name of spec2 |
| comment | string | The comment of spec2 |
| part | boolean | The spec is part or not<br />Accepted input are true, false, 1, 0, "1", and "0" |
| categories | array | Collection of category id |
| compositions | array | Collection of spec2 id |
| values | array | Collection of spec2 value |

| value | Type | Description |
| -------: | :---- | :--- |
| name | string | The name of spec2 value |
| display_name | string | The display name of spec2 value |
| price | number | The price of value, the currency is default by company |
| part_number | string | The part number of spec2 value |
| supplier_number | string | The supplier number of spec2 value |
| description | string | The description of spec2 value |
| comment | string | The comment of spec2 value |
| compositions | array | Collection of value composition |

| value.composition | Type | Description |
| -------: | :---- | :--- |
| id | integer | The spec2 id |
| value | integer | The value id for current spec2 |


### Return Parameters

<aside class="success">
Success
</aside>

The return same to Spec2 Detail API

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: the api_key is invalid</li><li>not_select_company: the user has not select current company</li><li>illegal_form_input: the form format does not pass validation</li></ul> |
| validation | object (option) | If the error_name is 'illegal_form_input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| name | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| display_name | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| comment | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| part | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not boolean</li></ol> |
| categories | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li><li>The category id is not exist</li><li>The category is not belongs to the current company </li></ol> |
| compositions | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li><li>The spec2 id is not exist</li><li>The spec2 is not belongs to the current company </li></ol> |
| values | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| values.(index).name | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).display_name | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).price | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not number</li></ol> |
| values.(index).part_number | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).supplier_number | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).description | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).comment | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).compositions | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li><li>The number of data is differ to compositions of spec</li></ol> |
| values.(index).compositions.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id not in compositions of spec2 </li></ol> |
| values.(index).compositions.(index).value | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The value id of spec2 is not exist</li><li>The spec2 value is not belongs to the spec </li></ol> |



## Edit Spec2

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/spec2/edit` |
| Method | `post` |
| Use | To edit spec |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "id": 1,
    "name": "Second hand",
    "display_name": "Second hand",
    "categories": [1, 2, 3],
    "compositions": [2],
    "values": [{
        "id": 1,
        "name": "small multiply",
        "display_name": "Small Multiply",
        "price": 10,
        "part_number": "",
        "supplier_number": "",
        "description": "",
        "comment": "",
        "compositions": [{
            "id": 2,
            "value": 1
        }]
    }, {
        "id": 0,
        "name": "center multiply",
        "display_name": "Center Multiply",
        "price": 10,
        "part_number": "",
        "supplier_number": "",
        "description": "",
        "comment": "",
        "compositions": [{
            "id": 2,
            "value": 1
        }]
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| id | integer | The spec2 id |
| name | string (option) | The name of spec2 |
| display_name | string (option) | The display name of spec2 |
| comment | string (option) | The comment of spec2 |
| part | boolean (option) | The spec is part or not<br />Accepted input are true, false, 1, 0, "1", and "0" |
| categories | array (option) | Collection of category id |
| compositions | array (option) | Collection of spec2 id |
| values | array (option) | Collection of spec2 value |

| value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The value id <br />It indicate adding value if id is 0 |
| name | string | The name of spec2 value |
| display_name | string | The display name of spec2 value |
| price | number | The price of value, the currency is default by company |
| part_number | string | The part number of spec2 value |
| supplier_number | string | The supplier number of spec2 value |
| description | string | The description of spec2 value |
| comment | string | The comment of spec2 value |
| compositions | array | Collection of value composition |

| value.composition | Type | Description |
| -------: | :---- | :--- |
| id | integer | The spec2 id |
| value | integer | The value id for current spec2 <br />It indicate empty if value is 0 |

### Return Parameters

<aside class="success">
Success
</aside>

The return same to Spec2 Detail API

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "illegal_form_input",
    "validation": {
        "name": ["invalid"],
        "display_name": ["required"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: the api_key is invalid</li><li>not_select_company: the user has not select current company</li><li>spec_not_found:<ol><li>the spec is not exist</li><li>the spec does not belongs to current company</li></ol><li>illegal_form_input: the form format does not pass validation</li></ul> |
| validation | object (option) | If the error_name is 'illegal_form_input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| name | array (option) | required: <ol><li>The data is empty</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| display_name | array (option) | required: <ol><li>The data is empty</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| comment | array (option) | invalid: <ol><li>The data is not string</li></ol> |
| part | array (option) | invalid: <ol><li>The data is not boolean</li></ol> |
| categories | array (option) | invalid: <ol><li>The id of category is not exist</li><li>The category is not belongs to the current company </li></ol> |
| compositions | array (option) | invalid: <ol><li>The data is not array</li><li>The spec2 is not exist</li><li>The spec2 is not belongs to the current company </li></ol> |
| values | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| values.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id of value is not exist</li><li>The value is not belongs to the spec2 </li></ol> |
| values.(index).name | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).display_name | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).price | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not number</li></ol> |
| values.(index).part_number | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).supplier_number | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).description | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).comment | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not string</li></ol> |
| values.(index).compositions | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li><li>The number of data is differ to compositions of spec2</li></ol> |
| values.(index).compositions.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id not in compositions of spec2 </li></ol> |
| values.(index).compositions.(index).value | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The value id of spec2 is not exist</li><li>The spec2 value is not belongs to the spec2 </li></ol> |