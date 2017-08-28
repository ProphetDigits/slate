# Variant

## Variant List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/variant/list` |
| Method | `post` |
| Use | to get variant list |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "target_company_id": 1,
    "item_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| target_company_id | integer | company id which user want get variant  list |
| item_id | integer | item’s id |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "variants": [{
        "variant_id": 1,
        "name": "Color",
        "number": "autark-k1-ss-001",
        "stock": 5,
        "default_price": 100,
        "default_deposit": 20,
        "company_id": 1,
        "cover_img": {
			"name": "xxx.jpg",
			"cover": true,
			"resource": {
				"240p": "http://abc/xxx_240p.jpg",
				"480p": "http://abc/xxx_480p.jpg",
				"720p": "http://abc/xxx_720p.jpg",
				"1080p": "http://abc/xxx_1080p.jpg"
			}
		}
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **variants** | **array** | a set of variant object |
| id | integer |  variant’s id |
| name | string |  variant’s name |
| number | string |  variant’s number |
| stock | integer | product number of variant |
| default_price | numeric | default price of variant |
| default_deposit | numeric | default deposit of variant |
| company_id | integer | variant belongs to which company |
| **cover_img** | **object** | variant cover image. It will be empty if no set cover image |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |
| *resource* | **object** | cover image tag |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 480 resolution (854x480) |
| *720p* | string | picture url of 720 resolution (1280x720) |
| *1080p* | string | picture url of 1080 resolution (1920x1080) |

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
| error_name | string | the name of the wrong type. |
||| **lack of parameters:** the request does not include the necessary parameters |
||| **does not signin:** user does not signin |
||| **not select company yet:** user need change current company |
||| **company not exist:** currenct company not exist |
||| **not company member:** the user is not the company member |
||| **no permission:** |


## Create Variant

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/variant/create` |
| Method | `post` |
| Use | to create variant |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "item_id": 1,
    "name": "Basic",
    "number": "autark-k1-ss-001",
    "website": "",
    "taric_code": "",
    "prices": [{
        "currency_id": 1,
        "price": 100
    }],
    "customizations": [{
        "id": 1,
        "value": 2
    }, {
        "id": 3,
        "value": 10
    }],
    "images": [{
		"name": "asdasdasd.jpg",
		"cover": true
	}, {
		"name": "qweqweq.jpg",
		"cover": false
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| item_id | integer | item’s id |
| name | string | variant’s name |
| number | string | variant’s number |
| website | string | variant’s website |
| taric_code | string | variant’s taric code |
| **prices** | **array** | variant’s prices in the each currency |
| *currency_id* | integer | currency  id |
| *price* | number |  price of corresponding currency |
| **customizations** | **array** | customization settings of variant |
| *id* | integer | customization’s id |
| *value* | integer | id of customization value |
| **images** | **array** | variant images |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |

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
    "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | the name of the wrong type. |
||| **lack of parameters:** the request does not include the necessary parameters |
||| **does not signin:** user does not signin |
||| **not select company yet:** user need change current company |
||| **company not exist:** currenct company not exist |
||| **not company member:** the user is not the company member |
||| **no permission:** |
||| **illegal form input:** form format does not pass validation |
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):** |
| *name* | array | **required:** it’s necessary column for this api |
| *customizations* | array | **required:** it’s necessary parameter |
||| **duplicate:**  this customization setting has been used |


## Variant  Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/variant/detail` |
| Method | `post` |
| Use | to show variant  detail |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "target_company_id": 1,
    "variant_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| target_company_id | integer | company id which user want get variant list |
| variant_id | integer | variant’s  id |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "name": "Basic",
    "number": "autark-k1-ss-001",
    "website": "",
    "taric_code": "",
    "item": [{
        "id": 1,
        "number":"NoteBook-1",
        "name": "NoteBookl",
    "company_id":1
    }],
    "prices": {
        "EUR": 100,
        "TWD": 3300
    },
    "default_deposit": 20,
    "customizations": [{
        "id": 1,
        "name": "Backgroud Color",
        "display_name": "Color",
        "value": {
            "id": 1,
            "name": "Red"
        }
    }, {
        "id": 2,
        "name": "Color",
        "display_name": "Color",
        "value": {
            "id":2,
            "name": "Red"
        }
    }],
    "images":[{
		"name": "xxx.jpg",
		"cover": true,
		"resource": {
			"240p": "http://abc/xxx_240p.jpg",
			"480p": "http://abc/xxx_480p.jpg",
			"720p": "http://abc/xxx_720p.jpg",
			"1080p": "http://abc/xxx_1080p.jpg"
		}
	}, {
		"name": "yyy.jpg",
		"cover": false,
		"resource": {
			"240p": "http://abc/yyy_240p.jpg",
			"480p": "http://abc/yyy_480p.jpg",
			"720p": "http://abc/yyy_720p.jpg",
			"1080p": "http://abc/yyy_1080p.jpg"
		}
	}],
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | variant’s  id |
| name | string | variant’s  name |
| number | string | variant’s number |
| website | string | variant’s website |
| taric_code | string | variant’s taric code |
| **item** | **object** | item which variant belongs |
| *id* | integer | item’s id |
| *number* | string | item’s number |
| *name* | string | item’s name |
| **prices** | **object** | variant’s price in the each currency |
| *currency_name* | numeric | price of variant in this currency |
| default_deposit | numeric | default deposit of variant |
| **customizations** | **array** | customizations setting of variant |
| *id* | integer | customization’s id |
| *name* | string | customization name |
| *display_name* | string | customization display name |
| *value* | **object** | customization value |
| *id* | integer |  id of customization value |
| *name* | string |  name of customization value |
| **images** | **array** | variant images |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |
| *resource* | **object** | cover image tag |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 480 resolution (854x480) |
| *720p* | string | picture url of 720 resolution (1280x720) |
| *1080p* | string | picture url of 1080 resolution (1920x1080) |

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
| error_name | string | the name of the wrong type. |
||| **lack of parameters:** some input parameters missing, not in the request |
||| **does not signin:** user does not signin |
||| **not select company yet:** user need change current company |
||| **company not exist:** currenct company not exist |
||| **not company member:** the user is not the company member |
||| **no permission:** |
||| **variant not exist:** |


## Edit Variant

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/variant/edit` |
| Method | `post` |
| Use | to edit variant |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "variant_id": 1,
    "name": "Basic",
    "number": "autark-k1-ss-001",
    "website": "",
    "taric_code": "",
    "prices": [{
        "currency_id": 1,
        "price": 100
    }],
    "customizations": [{
        "id": 1,
        "value": 2
    }, {
        "id": 3 ,
        "value": 10
    }],
    "images": [{
		"name": "asdasdasd.jpg",
		"cover": true
	}, {
		"name": "qweqweq.jpg",
		"cover": false
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| variant_id | integer |  item id |
| name | string | variant’s name |
| number | string | variant’s number |
| website | string | variant’s website |
| taric_code | string | variant’s taric code |
| **prices** | **array** |  variant’s prices in the each currency |
| *currency_id* | integer | currency id |
| *price* | numeric | price of corresponding currency |
| **customizations** | **array** | customization settings of variant |
| *id* | integer | customization’s id |
| *value* | integer |  id of customization value  |
| **images** | **array** | variant images |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |


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
    "error_name":""
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | the name of the wrong type. |
||| **lack of parameters:** some input parameters missing, not in the request |
||| **does not signin:** user does not signin |
||| **not company member:**  user are not member in this company |
||| **invalid customization:** customization is not include this value(value of vustomization error) |
||| **illegal form input:** validate unsuccess, the exact error message will in validation of data |
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| *name* | array | **required:** it’s necessary column for this api |
|||**dulicate:** the name has already been taken|
| *price* | array | **required:** it’s necessary column for this api |
| *customizations* | array | **required:**  it’s necessary column for this api |
|||**dulicate:**  this customization style has been used|
