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
| Use | to create spec |
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
| api_key | string | System gives it after user sign in |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| comment | string | The comment of spec |
| part | boolean | The spec is part or not<br />Accepted input are true, false, 1, 0, "1", and "0" |
| categories | array | The set of id of category |
| compositions | array | The set of id of spec |
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
| compositions | array | The set of compositions |

| spec_value_composition | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| value | integer | The id of value of spec |


> Return Parameters When Success

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
            "compositions": [{
                "id": 2,
                "name": "color",
                "value": {
                    "id": 1,
                    "name": "red"
                }
            }]
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
| compositions | array | The compositions of spec |
| values | array | The set of value of spec |

| spec_category | | |
| -------: | :---- | :--- |
| id | integer | The id of category |
| name | string | The name of category |

| spec_composition | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| part | boolean | The spec is part or not |

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
| compositions | array | The set of compositions |

| spec_value_composition | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| value | object | The setting of value of composition |

| spec_value_composition_value | | |
| -------: | :---- | :--- |
| id | integer | The id of value of spec |
| name | string | The name of value of spec |


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
| compositions | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not array</li><li>The id of spec is not exist</li><li>The spec is not belongs to the current company </li></ol> |
| values | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not array</li></ol> |
| values.(index).name | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).display_name | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).price | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not number</li></ol> |
| values.(index).part_number | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).supplier_number | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).description | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).comment | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).compositions | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not array</li><li>The number of data is differ to compositions of spec</li></ol> |
| values.(index).compositions.(index).id | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not integer</li><li>The id not in compositions of spec </li></ol> |
| values.(index).compositions.(index).value | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not integer</li><li>The id of value of spec is not exist</li><li>The value of spec is not belongs to the spec </li></ol> |


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
| api_key | string | System gives it after user sign in |
| id | integer | The id of spec |
| name | string (option) | The name of spec |
| display_name | string (option) | The display name of spec |
| comment | string (option) | The comment of spec |
| part | boolean (option) | The spec is part or not<br />Accepted input are true, false, 1, 0, "1", and "0" |
| categories | array (option) | The set of id of category |
| compositions | array (option) | The set of id of spec |
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
| compositions | array | The set of compositions |

| spec_value_composition | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| value | integer | The id of value of spec <br />It indicate empty if value is 0 |


> Return Parameters When Success

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
            "compositions": [{
                "id": 2,
                "name": "color",
                "value": {
                    "id": 1,
                    "name": "red"
                }
            }]
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
| compositions | array | The compositions of spec |
| values | array | The set of value of spec |

| spec_category | | |
| -------: | :---- | :--- |
| id | integer | The id of category |
| name | string | The name of category |

| spec_composition | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| part | boolean | The spec is part or not |

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
| compositions | array | The set of compositions |

| spec_value_composition | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| value | object | The setting of value of composition |

| spec_value_composition_value | | |
| -------: | :---- | :--- |
| id | integer | The id of value of spec |
| name | string | The name of value of spec |


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
| compositions | array (option) | invalid: <ol><li>The data is not array</li><li>The id of spec is not exist</li><li>The spec is not belongs to the current company </li></ol> |
| values | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not array</li></ol> |
| values.(index).id | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not integer</li><li>The id of value is not exist</li><li>The value is not belongs to the spec </li></ol> |
| values.(index).name | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).display_name | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).price | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not number</li></ol> |
| values.(index).part_number | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).supplier_number | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).description | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).comment | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| values.(index).compositions | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not array</li><li>The number of data is differ to compositions of spec</li></ol> |
| values.(index).compositions.(index).id | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not integer</li><li>The id not in compositions of spec </li></ol> |
| values.(index).compositions.(index).value | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not integer</li><li>The id of value of spec is not exist</li><li>The value of spec is not belongs to the spec </li></ol> |