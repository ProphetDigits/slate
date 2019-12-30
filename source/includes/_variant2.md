# Variant2

## Variant2 List

### Description

| Title | Description |
| -------: | :---- |
| URL | `company/item/variant2/list` |
| Method | `post` |
| Use | To get variant2 list |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "target_company_id": 1,
    "item_id": 1,
    "spec_values": [1, 2]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| target_company_id | integer | The company id of item |
| item_id | integer | The item id |
| spec_values | array (option) | Collection of id of spec value. It's to filter variants combine by those spec value |


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"variants": [{
		"id": 1,
		"name": "Multiply bl",
		"number": "mbl",
        "stock": 5,
        "currency": "EUR",
        "price": 100,
        "deposit": 20,
		"cover_image": {
			"px240": "http://abc/xxx_240p.jpg",
			"px480": "http://abc/xxx_480p.jpg",
			"px720": "http://abc/xxx_720p.jpg",
			"px1080": "http://abc/xxx_1080p.jpg"
		},
		"duplicate_combination": true,
		"company": {
			"id": 1
		}
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| variants | array | Collection of variant |

| variant | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of variant |
| name | string | The name of variant |
| number | string | The number of variant |
| stock | integer | The product amount of variant |
| currency | string | The default currency of company |
| price | numeric | The price of variant for default currency |
| deposit | numeric | The deposit of price for default currency |
| cover_image | object | The url of each resolution for cover image |
| duplicate_combination | boolean | The combination is duplicate with other variant2 |
| company | object | The company of variant |

| variant.cover_image | Type | Description |
| -------: | :---- | :--- |
| px240 | string | The picture url of 240 resolution (426x240)<br />It's empty string if no cover image |
| px480 | string | The picture url of 480 resolution (854x480)<br />It's empty string if no cover image |
| px720 | string | The picture url of 720 resolution (1280x720<br />It's empty string if no cover image |
| px1080 | string | The picture url of 1080 resolution (1920x1080)<br />It's empty string if no cover image |

| variant.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "item_not_exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>item_not_exist: The item is not exist or not belongs to target company</li></ul> |



## Variant2 Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `company/item/variant2/detail` |
| Method | `post` |
| Use | To show variant2 detail |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "target_company_id": 1,
    "id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| target_company_id | integer | The company id of variant2 |
| id | integer | The variant2 id |


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"variant": {
		"id": 1,
		"name": "Multiply bl",
		"number": "mbl",
        "taric_code": "1234567",
        "weblink": "",
        "item": {
        	"id": 1,
        	"name": "Multiply K1",
        	"number": "Mk1"
        },
        "prices": [{
        	"currency": "EUR",
        	"defualt_currency": true,
        	"value": 123.45
        }, {
        	"currency": "TWD",
        	"defualt_currency": false,
        	"value": 123
        }],
        "deposit": {
        	"currency": "EUR",
        	"value": 12.35
        },
        "specs": [{
        	"id": 1,
        	"name": "Movement",
        	"display_name": "Movement",
        	"part": true,
        	"value": {
        		"id": 1,
        		"name": "K1-11 auto",
        		"display_name": "K1-11",
        		"price": {
        			"currency": "EUR",
        			"value": 9.2
        		}
        	}
        }],
        "images":[{
			"name": "xxx.jpg",
			"cover": true,
			"resources": {
				"px240": "http://abc/xxx_240p.jpg",
				"px480": "http://abc/xxx_480p.jpg",
				"px720": "http://abc/xxx_720p.jpg",
				"px1080": "http://abc/xxx_1080p.jpg"
			}
		}, {
			"name": "yyy.jpg",
			"cover": false,
			"resources": {
				"px240": "http://abc/yyy_240p.jpg",
				"px480": "http://abc/yyy_480p.jpg",
				"px720": "http://abc/yyy_720p.jpg",
				"px1080": "http://abc/yyy_1080p.jpg"
			}
		}],
        "warranty": {
			"type": "Limited",
			"value": 2,
			"unit": "Years"
		},
		"variants_of_same_combinations": [{
			"id": 2,
			"name": "Multiply bk"
		}]
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| variant | object | The variant data |

| variant | Type | Description |
| -------: | :---- | :--- |
| id | integer | The variant2 id |
| name | string | The variant2 name |
| number | string | The variant2 number |
| weblink | string | The website URL of variant2 |
| taric_code | string | The taric code of variant2 |
| item | object | The item of variant2 |
| specs | array | Collection of spec configuration |
| prices | array | Collection of each currency price |
| deposit | object | The deposit of variant2 |
| images | array | Collection of image |
| warranty | object | The warranty configuration of variant2 |
| variants_of_same_combinations | array | Collection of variant2 with same combinations |

| variant.item | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of item |
| name | string | The name of item |
| number | string | The number of item |

| variant.price | Type | Description |
| -------: | :---- | :--- |
| currency | string | The currency name |
| defualt_currency | boolean | The tag that is default currency of company |
| value | numeric | The currency's price |

| variant.deposit | Type | Description |
| -------: | :---- | :--- |
| currency | string | The currency of deposit |
| value | numeric | The deposit of variant |

| variant.spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| part | boolean | The spec is part or not |
| value | object | The spec configuration |

| variant.spec.value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The value id of spec<br />It's zero if variant not setting spec |
| name | string | The value name of spec<br />It's empty string if variant not setting spec |
| display_name | string | The display name of spec value<br />It's empty string if variant not setting spec |
| price | object | The price of spec value |

| variant.spec.value.price | Type | Description |
| -------: | :---- | :--- |
| currency | string | The currency of price |
| value | numeric | The price of value of spec<br /> It's zero if spec of variant not setting |

| variant.image | Type | Description |
| -------: | :---- | :--- |
| name | string | The file name |
| cover | boolean | The tag of cover image |
| resources | object | The url of each resolution for cover image |

| variant.image.resource | Type | Description |
| -------: | :---- | :--- |
| px240 | string | The picture url of 240 resolution (426x240) |
| px480 | string | The picture url of 480 resolution (854x480) |
| px720 | string | The picture url of 720 resolution (1280x720 |
| px1080 | string | The picture url of 1080 resolution (1920x1080) |

| variant.warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type |
| value | integer | The duration of warranty |
| unit | string | The unit of duration |

| variant.variants_of_same_combination | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of variant |
| name | string | The name of variant |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "does not signin"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>variant_not_exist: The variant2 is not exist or not belongs to target company</li></ul> |



## Create Variant2

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/variant2/create` |
| Method | `post` |
| Use | to create variant |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "item_id": 1,
    "name": "Basic",
    "number": "autark-k1-ss-001",
    "weblink": "",
    "taric_code": "",
    "prices": [{
        "currency": "EUR",
        "value": 100
    }],
    "specs": [{
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
	}],
	"warranty": {
		"type": "Limited",
		"value": 2,
		"unit": "Years"
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | System gives it after user sign in |
| item_id | integer | The id of item |
| name | string | The name of variant |
| number | string | The number of variant |
| weblink | string | The website URL of variant |
| taric_code | string | The taric code of variant |
| specs | array | The spec configuration of variant |
| prices | array | The prices for each currency of variant |
| images | array | The images of variant |
| warranty | object | The warranty configuration of variant |

| price | Type | Description |
| -------: | :---- | :--- |
| currency | string | The currency of price |
| value | number | The price of currency of variant |

| spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| value | integer | The id of value of spec<br />It's zero indicate no setting |

| image | Type | Description |
| -------: | :---- | :--- |
| name | string | The name will be returned by Upload Image API |
| cover | boolean | The tag of cover image |

| warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type - Limited or Lifetime <br/>The parameter of value and unit is unnecessary when type is Lifetime |
| value | positive integer (option) | The duration of warranty |
| unit | string (option) | The unit of duration - Years or Months |

> Return Parameters

### Return Parameters When Success

<aside class="success">
Success
</aside>

The return same to Get Variant2 Detail API


### Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "validation": {
        "name": ["invalid"],
        "number": ["required"]
    },
    "error_name": "illegal_form_input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>item_not_exist: The item is not exist or not belongs to target company</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | | |
| -------: | :---- | :--- |
| item_id | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be integer</li></ol> |
| name | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> invalid: <ol><li>The data should be string</li></ol> |
| number | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be string</li></ol> |
| weblink | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be string</li></ol> |
| taric_code | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be string</li></ol> |
| prices | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be array</li></ol> |
| prices.(index).currency | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The currency not set in company</li></ol> |
| prices.(index).value | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be numeric</li></ol> |
| specs | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be array</li></ol> |
| spec2s.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not belongs to item </li></ol> |
| specs.(index).value | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not set in item </li></ol> |
| images | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be array</li></ol> |
| images.(index).name | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> invalid: <ol><li>The data should be string</li></ol> |
| images.(index).cover | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be boolean</li></ol> |
| warranty | array (option) | required: <ol><li>The field is required</li></ol> |
| warranty.type | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>Either the data should be Limited or Lifetime</li></ol> |
| warranty.value | array (option) | required: <ol><li>The field is required if type of warranty is Limited</li></ol>invalid: <ol><li>The data is not positive integer</li></ol> |
| warranty.unit | array (option) | required: <ol><li>The field is required if type of warranty is Limited</li></ol>invalid: <ol><li>Either the data should be Years or Months</li></ol> |


## Edit Variant2

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/variant2/edit` |
| Method | `post` |
| Use | to edit variant |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "id": 1,
    "name": "Basic",
    "number": "autark-k1-ss-001",
    "weblink": "",
    "taric_code": "",
    "prices": [{
        "currency": "EUR",
        "value": 100
    }],
    "specs": [{
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
	}],
	"warranty": {
		"type": "Limited",
		"value": 2,
		"unit": "Years"
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of variant |
| name | string (option) | The name of variant |
| number | string (option) | The number of variant |
| weblink | string (option) | The website URL of variant |
| taric_code | string (option) | The taric code of variant |
| specs | array (option) | The spec configuration of variant |
| prices | array (option) | The prices for each currency of variant |
| images | array (option) | The images of variant |
| warranty | object (option) | The warranty configuration of variant |

| price | Type | Description |
| -------: | :---- | :--- |
| currency | string | The currency of price |
| value | number | The price of currency of variant |

| spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| value | integer | The id of value of spec<br />It's zero indicate no setting |

| image | Type | Description |
| -------: | :---- | :--- |
| name | string | The name will be returned by Upload Image API |
| cover | boolean | The tag of cover image |

| warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type - Limited or Lifetime <br/>The parameter of value and unit is unnecessary when type is Lifetime |
| value | positive integer (option) | The duration of warranty |
| unit | string (option) | The unit of duration - Years or Months |

> Return Parameters

### Return Parameters When Success

<aside class="success">
Success
</aside>

The return same to Get Variant2 Detail API


### Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "validation": {
        "name": ["invalid"],
        "number": ["required"]
    },
    "error_name": "illegal_form_input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | | |
| -------: | :---- | :--- |
| name | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> invalid: <ol><li>The data should be string</li></ol> |
| number | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be string</li></ol> |
| weblink | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be string</li></ol> |
| taric_code | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be string</li></ol> |
| prices | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be array</li></ol> |
| prices.(index).currency | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The currency not set in company</li></ol> |
| prices.(index).value | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be numeric</li></ol> |
| specs | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be array</li></ol> |
| spec2s.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not belongs to item </li></ol> |
| specs.(index).value | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not set in item </li></ol> |
| images | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be array</li></ol> |
| images.(index).name | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> invalid: <ol><li>The data should be string</li></ol> |
| images.(index).cover | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be boolean</li></ol> |
| warranty | array (option) | required: <ol><li>The field is required</li></ol> |
| warranty.type | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>Either the data should be Limited or Lifetime</li></ol> |
| warranty.value | array (option) | required: <ol><li>The field is required if type of warranty is Limited</li></ol>invalid: <ol><li>The data is not positive integer</li></ol> |
| warranty.unit | array (option) | required: <ol><li>The field is required if type of warranty is Limited</li></ol>invalid: <ol><li>Either the data should be Years or Months</li></ol> |