# Bag

## Get Bag Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/bag/detail` |
| Method | `post` |
| Use | to get bag detail from Front Site Shopping Bag. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "company_id": "1"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | integer | The company id |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

> Empty Bag

```json
{
    "bag_id": null,
    "company": {
        "id": null,
        "name": null
    },
    "currency": null,
    "price": {
        "subtotal": 0,
        "total": 0
    },
    "variants": null,
    "badge_number": 0
}
```
| Parameter | Type | Description |
|   :---:   | :---:| :---        |
| bag_id    | integer | bag id   |
| **company** | **object** | bag belongs to which company |
| *id* | integer | company id |
| *name* | string | company name |
| currency | string | company default currency name |
| **price** | **object** | calculate prices of bag |
| *subtotal* | integer | order price in bag |
| *total* | integer | total price in bag |
| **variants** | **object** | variants in bag |
| badge_number | integer | total variant quantity in bag |

> Not Empty Bag

```json
{
    "bag_id": 1,
    "company": {
        "id": 1,
        "name": "CC SHOP"
    },
    "currency": "USD",
    "price": {
        "subtotal": 20,
        "total": 20
    },
    "variants": [
        {
            "id": 2,
            "item_name": "XO Wine Man",
            "images": [
                {
                    "name": "xxx.jpg",
                    "cover": 0,
                    "resource": {
                        "px240": "http://abc/xxx_240p.jpg",
                        "px480": "http://abc/xxx_480p.jpg",
                        "px720": "http://abc/xxx_720p.jpg",
                        "px1080": "http://abc/xxx_1080p.jpg"
                    }
                },{
                    "name": "yyy.jpg",
                    "cover": 1,
                    "resource": {
                        "px240": "http://abc/yyy_240p.jpg",
                        "px480": "http://abc/yyy_480p.jpg",
                        "px720": "http://abc/yyy_720p.jpg",
                        "px1080": "http://abc/yyy_1080p.jpg"
                    }
            ],
            "default_price": 10,
            "quantity": 2,
            "customizations": [
                {
                    "id": 1,
                    "name": "COLOR",
                    "value": {
                        "id": 3,
                        "name": "Red"
                    }
                },
                {
                    "id": 2,
                    "name": "SIZE",
                    "value": {
                        "id": 4,
                        "name": "Large"
                    }
                }
            ]
        }
    ],
    "badge_number": 2
}
```
| Parameter | Type | Description |
|   :---:   | :---:| :---        |
| bag_id    | integer | bag id   |
| **company** | **object** | bag belongs to which company |
| *id* | integer | company id |
| *name* | string | company name |
| currency | string | company default currency name |
| **price** | **object** | calculate prices of bag |
| *subtotal* | integer | order price in bag |
| *total* | integer | total price in bag |
| **variants** | **object** | variants in bag |
| *id* | integer |  variant’s id |
| *item_name* | string |  variant’s item name |
| **images** | **object** | It will get variant images first.If there's no variant images it will get item images. It will be empty if no item and variant image |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |
| *resource* | **object** | cover image tag |
| *px240* | string | picture url of 240 resolution (426x240) |
| *px480* | string | picture url of 480 resolution (854x480) |
| *px720* | string | picture url of 720 resolution (1280x720) |
| *px1080* | string | picture url of 1080 resolution (1920x1080) |
| default_price | integer | default price of variant |
| quantity | integer | the quantity of variant |
| **customizations** | **array** | customizations setting of variant |
| *id* | integer | customization’s id |
| *name* | string | customization name |
| *value* | **object** | customization value |
| *id* | integer |  id of customization value |
| *name* | string |  name of customization value |
| badge_number | integer | total variant quantity in bag |


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
| error_name | string | the name of the wrong type |
||| **lack of parameters:** the request does not include the necessary parameters |
||| **not_sign_in:** user does not signin |
||| **company_not_exist:** currenct company not exist |


## Add Variant To Bag

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/bag/variant/add` |
| Method | `post` |
| Use | to add variant into shopping bag. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "company_id": "1",
    "variant_id": "1",
    "quantity": "1"
}
```

| Parameter | Type | Description |
| :-------: | :---: | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | integer | company id |
| variant_id | integer | variant id |
| quantity | integer | user use it want to add quantity with variant  |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "bag_id": 1,
    "variants": {
        "id": 2,
        "images": {
            "px240": "http://abc/xxx_240p.jpg",
            "px480": "http://abc/xxx_480p.jpg",
            "px720": "http://abc/xxx_720p.jpg",
            "px1080": "http://abc/xxx_1080p.jpg"
        },
        "item_name": "XO Wine Man",
        "name": "XO X Wine",
        "price": 10
    },
    "currency": "USD",
    "badge_number": 2
}
```

| Parameter | Type | Description |
|   :---:   | :---:| :---        |
| bag_id    | integer | bag id   |
| **variants** | **object** | variants in bag |
| *id* | integer |  variant’s id |
| **images** | **object** | It will get variant images first.If there's no variant images it will get item images. It will be empty if no item and variant image |
| *px240* | string | picture url of 240 resolution (426x240) |
| *px480* | string | picture url of 480 resolution (854x480) |
| *px720* | string | picture url of 720 resolution (1280x720) |
| *px1080* | string | picture url of 1080 resolution (1920x1080) |
| *item_name* | string |  variant’s item name |
| *name* | string | variant name |
| *price* | integer | default price of variant |
| currency | string | company default currency name |
| badge_number | integer | total variant quantity in bag |

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
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| **validation** | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |
| company_id | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not integer</li></ol> |
| variant_id | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not integer</li></ol> |
| quantity | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not integer</li></ol> |


## Remove Variant From Bag

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/bag/variant/remove` |
| Method | `post` |
| Use | to remove variant from shopping bag. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "bag_id": "1",
    "variant_id": "2"
}
```

| Parameter | Type | Description |
| :-------: | :---: | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| bag_id | integer | bag id |
| variant_id | integer | variant id |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

> Empty Bag

```json
{
    "bag_id": null,
    "company": {
        "id": null,
        "name": null
    },
    "currency": null,
    "price": {
        "subtotal": 0,
        "total": 0
    },
    "variants": null,
    "badge_number": 0
}
```

| Parameter | Type | Description |
|   :---:   | :---:| :---        |
| bag_id    | integer | bag id   |
| **company** | **object** | bag belongs to which company |
| *id* | integer | company id |
| *name* | string | company name |
| currency | string | company default currency name |
| **price** | **object** | calculate prices of bag |
| *subtotal* | integer | order price in bag |
| *total* | integer | total price in bag |
| **variants** | **object** | variants in bag |
| badge_number | integer | total variant quantity in bag |

> Not Empty Bag

```json
{
    "bag_id": 1,
    "company": {
        "id": 1,
        "name": "CC SHOP"
    },
    "currency": "USD",
    "price": {
        "subtotal": 40,
        "total": 40
    },
    "variants": [
        {
            "id": 2,
            "item_name": "XO Wine Man",
            "images": [
                {
                    "name": "xxx.jpg",
                    "cover": 0,
                    "resource": {
                        "px240": "http://abc/xxx_240p.jpg",
                        "px480": "http://abc/xxx_480p.jpg",
                        "px720": "http://abc/xxx_720p.jpg",
                        "px1080": "http://abc/xxx_1080p.jpg"
                    }
                },
                {
                    "name": "yyy.jpg",
                    "cover": 1,
                    "resource": {
                        "px240": "http://abc/yyy_240p.jpg",
                        "px480": "http://abc/yyy_480p.jpg",
                        "px720": "http://abc/yyy_720p.jpg",
                        "px1080": "http://abc/yyy_1080p.jpg"
                    }
                }
            ],
            "default_price": 10,
            "quantity": 4,
            "customizations": [
                {
                    "id": 1,
                    "name": "COLOR",
                    "value": {
                        "id": 3,
                        "name": "BLACK"
                    }
                },
                {
                    "id": 2,
                    "name": "SIZE",
                    "value": {
                        "id": 4,
                        "name": "Large"
                    }
                }
            ]
        }
    ],
    "badge_number": 4
}
```

| Parameter | Type | Description |
|   :---:   | :---:| :---        |
| bag_id    | integer | bag id   |
| **company** | **object** | bag belongs to which company |
| *id* | integer | company id |
| *name* | string | company name |
| currency | string | company default currency name |
| **price** | **object** | calculate prices of bag |
| *subtotal* | integer | order price in bag |
| *total* | integer | total price in bag |
| **variants** | **object** | variants in bag |
| *id* | integer |  variant’s id |
| *item_name* | string |  variant’s item name |
| **images** | **object** | It will get variant images first.If there's no variant images it will get item images. It will be empty if no item and variant image |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |
| *resource* | **object** | cover image tag |
| *px240* | string | picture url of 240 resolution (426x240) |
| *px480* | string | picture url of 480 resolution (854x480) |
| *px720* | string | picture url of 720 resolution (1280x720) |
| *px1080* | string | picture url of 1080 resolution (1920x1080) |
| default_price | integer | default price of variant |
| quantity | integer | the quantity of variant |
| **customizations** | **array** | customizations setting of variant |
| *id* | integer | customization’s id |
| *name* | string | customization name |
| *value* | **object** | customization value |
| *id* | integer |  id of customization value |
| *name* | string |  name of customization value |
| badge_number | integer | total variant quantity in bag |

<aside class="warning">
Failure
</aside>


```json
{
    "error_name": "illegal_form_input",
    "validation": {
        "bag_id": ["required"],
        "variant_id": ["invalid"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>bag_not_exist: The bag_id is invalid</li><li>variant_not_exist: The variant_id is invalid</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| **validation** | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |
| bag_id | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not integer</li></ol> |
| variant_id | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not integer</li></ol> |


## Adjust Variant Quantity from Bag

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/variant/quantity/plus` |
| URL | `user/variant/quantity/minus` |
| Method | `post` |
| Use | to adjust variant quantity from shopping bag. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "bag_id": "1",
    "variant_id": "2"
}
```

| Parameter | Type | Description |
| :-------: | :---: | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| bag_id | integer | bag id |
| variant_id | integer | variant id |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "variant": {
        "id": 2,
        "quantity": 1,
        "total": 10
    },
    "price": {
        "subtotal": 30,
        "total": 30
    },
    "badge_number": 3
}
```

| Parameter | Type | Description |
|   :---:   | :---:| :---        |
| **variants** | **object** | variants in bag |
| *id* | integer | variant id |
| *quantity* | integer | the variant quantity in bag |
| *total* | integer | total variant price in bag |
| **price** | **object** | calculate prices of bag |
| *subtotal* | integer | order price in bag |
| *total* | integer | total price in bag |
| badge_number | integer | total variant quantity in bag |


<aside class="warning">
Failure
</aside>


```json
{
    "error_name": "illegal_form_input",
    "validation": {
        "bag_id": ["required"],
        "variant_id": ["invalid"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>bag_not_exist: The bag_id is invalid</li><li>variant_not_exist: The variant_id is invalid</li><li>variant_not_in_bag: The variant is not in bag</li><li>quantity_has_reached_the_minimum: The variant quantity has reached the minimum one</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| **validation** | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |
| bag_id | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not integer</li></ol> |
| variant_id | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not integer</li></ol> |