# Item

## Create Item

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/create` | 
| Method | `post` | 
| Use | to create item |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"name": "item name",
	"number": "item number",
	"categories": [1, 2, 3],
	"price": 123.456,
	"duscount": 30,
	"ean": "",
	"unit": "",
	"contain": "",
	"weblink": "",
	"description": "",
	"images": [{
		"name": "asdasdasd.jpg",
		"cover": true
	}, {
		"name": "qweqweq.jpg",
		"cover": false
	}],
	"videos": [{
		"weblink": "http://asdas.youtube.com",
		"description": ""
	}, {
		"weblink": "http://asda.youtube.com",
		"description": ""
	}],
	"specs": [{
		"id": 1,
		"value": 2
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
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| name | string |  item name |
| number | string | item number |
| categories | array | category id set |
| price | number | item default price |
| discount | integer | item max discount percent |
| deposit_ratio | integer | deposit ratio of item |
| ean | string | item ean |
| unit | string | item unit |
| contain | string | how many items per unit |
| weblink | string | item’s website URL |
| description | string | item description |
| **images** | **array** | item images |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |
| **videos** | **array** | item videos |
| *weblink* | video url |
| *description* | video description |
| **specs** | **array** | spec setting |
| *id* | spec id |
| *value* | value id of spec |
| **warranty** | **object** | warranty setting of item |
| *type* | string | warranty type - Limited or Lifetime |
| *value* | positive integer (option) | warranty value |
| *unit* | string (option) | value unit - Years or Months |



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
	"validation": {
		"name": ["dulicate"],
		"number": ["required"]
	},
	"error_name": "illegal form input"
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
|||**item not exist:** item number is incorrect|
|||**illegal form input:** form format does not pass validation|
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| name | array | **required:** it’s necessary parameter |
| number | array | **required:** it’s necessary parameter |
|||**dulicate:** the name has already been taken|
| categories | array | **required:** it’s necessary parameter |
|||**not exist:** category not exist|
| price | array | **required:** it’s necessary parameter |
|||**invaid value:** price need accord to number|
| discount | array | **required:** it’s necessary parameter |
|||**invaid value:** price need accord to integer and between 0 to 100|
| deposit_ratio | array | **invaid value:** price need accord to integer and between 0 to 100|


## Item Detail Without Login

### Description

| Title | Description |
| -------: | :---- |
| URL | `item/{item_id}/detail` | 
| Method | `get` | 
| Use | to create item |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"item_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| item_id | integer | item's id |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"id": 1,
	"name":"Edison Evo",
	"description":"Mit dem edison EVO ist uns ein weiterer Meilenstein gelungen:  Fahrwerksperformance und 	Rahmengeometrie sind in einer noch nie  dagewesenen Perfektion kombiniert.",
	"prices": {
		"EUR": {
			"min": 50,
			"basic": 100,
			"max": 150
		},
		"TWD": {
			"min": 50,
			"basic": 100,
			"max": 150
		}
	},
	"images":[{
		"name": "xxx.jpg",
		"cover": true,
		"resource": {
			"px240": "http://abc/xxx_240p.jpg",
			"px480": "http://abc/xxx_480p.jpg",
			"px720": "http://abc/xxx_720p.jpg",
			"px1080": "http://abc/xxx_1080p.jpg"
		}
	}, {
		"name": "yyy.jpg",
		"cover": false,
		"resource": {
			"px240": "http://abc/yyy_240p.jpg",
			"px480": "http://abc/yyy_480p.jpg",
			"px720": "http://abc/yyy_720p.jpg",
			"px1080": "http://abc/yyy_1080p.jpg"
		}
	}],

    "warranty": {
        "type": "Limited",
        "value": 0,
        "unit": "Years"
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer |  item id |
| name | string |  item name |
| **prices** | **object** |  item prices of currency |
| *min* | number | min price in all variants of item. value is null if item doesn’t own variant |
| *basic* | number | basic price which be set by user in the item |
| *max* | number | max price in all variants of item. value is null if item doesn’t own variant |
| description | string | item description |
| **images** | **array** | item images |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |
| *resource* | **object** | cover image tag |
| *px240* | string | picture url of 240 resolution (426x240) |
| *px480* | string | picture url of 480 resolution (854x480) |
| *px720* | string | picture url of 720 resolution (1280x720) |
| *px1080* | string | picture url of 1080 resolution (1920x1080) |
| **specs** | **array** | spec setting |
| *id* | integer | spec id |
| *name* | string | spec display name |
| *value* | **object** | value id of spec |
| *id* | integer | spec value id |
| *name* | string | spec value display name |



<aside class="warning">
Failure
</aside>

```json
{
	"error_name": "illegal form input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:| 
|||**item not exist:** item number is incorrect|


## Item Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/detail` | 
| Method | `post` | 
| Use | to create item |
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
| target_company_id | integer |  company id which user want get category detail |
| item_id | integer | item's id |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"id": 1,
	"name":"Edison Evo",
	"number": "xxxx",
	"description":"Mit dem edison EVO ist uns ein weiterer Meilenstein gelungen:  Fahrwerksperformance und 	Rahmengeometrie sind in einer noch nie  dagewesenen Perfektion kombiniert.",
	"weblink": "http://evo.bionicon.com/",
	"ean": "",
	"unit": "Set",
	"contain": 1,
	"prices": {
		"EUR": {
			"min": 50,
			"basic": 100,
			"max": 150
		},
		"TWD": {
			"min": 50,
			"basic": 100,
			"max": 150
		}
	},
	"discount": 50,
    "deposit_ratio": 30,	
	"company": {
		"id": 1,
		"name": "Bionicon"
	},
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
	"videos":[{
		"name": "",
		"hyperlink": "https://youtu.be/70ZkhewCDD8"
	}, {
		"name": "youtube",
		"hyperlink": "https://youtu.be/G2reQQUQ-Dc"
	}],
    "categories": [
        {
            "id": 1,
            "name": "xxx"
        },
        {
            "id": 2,
            "name": "yyy"
        }
    ],
    "specs": [
        {
            "id": 1,
            "name": "FIX1",
            "display_name": "FIX1",
            "value": {
                "id": 3,
                "name": "OPTION1"
            }
        },
        {
            "id": 2,
            "name": "FIX2",
            "display_name": "FIX2",
            "value": {
                "id": 4,
                "name": "OPTION2"
            }
        }
    ],
    "customizations": [
        {
            "id": 5,
            "name": "CUST1",
            "display_name": "CUST1",
            "values": [
                {
                    "id": 6,
                    "name": "WHITE",
                    "price": 5
                },
                {
                    "id": 7,
                    "name": "BLACK",
                    "price": 10
                },
                {
                    "id": 8,
                    "name": "GEMBLUE",
                    "price": 15
                }
            ]
        },
        {
            "id": 9,
            "name": "SIZE",
            "display_name": "SIZE",
            "values": []
        }
    ],
    "warranty": {
        "type": "Limited",
        "value": 0,
        "unit": "Years"
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer |  item id |
| name | string |  item name |
| number | string | item number |
| **categories** | **array** | category id set |
| id | integer |  category id |
| name | string |  category name |
| **prices** | **object** |  item prices of currency |
| *min* | number | min price in all variants of item. value is null if item doesn’t own variant |
| *basic* | number | basic price which be set by user in the item |
| *max* | number | max price in all variants of item. value is null if item doesn’t own variant |
| discount | integer | item max discount percent |
| deposit_ratio | integer | deposit ratio of item |
| ean | string | item ean |
| unit | string | item unit |
| contain | string | how many items per unit |
| weblink | string | item’s website URL |
| description | string | item description |
| **images** | **array** | item images |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |
| *resource* | **object** | cover image tag |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 480 resolution (854x480) |
| *720p* | string | picture url of 720 resolution (1280x720) |
| *1080p* | string | picture url of 1080 resolution (1920x1080) |
| **videos** | **array** | item videos |
| *hyperlink* | video url |
| *description* | video description |
| **specs** | **array** | spec setting |
| *id* | integer | spec id |
| *name* | string | spec display name |
| *value* | **object** | value id of spec |
| *id* | integer | spec value id |
| *name* | string | spec value display name |
| **customizations** | **array** | |
| *id* | integer | customization id |
| *name* | string | customization name |
| *display_name* | string | customization display name |
| *values* | **object** | |
| *id* | integer | customization value id |
| *name* | string | customization value name |
| *price* | number | extra price of customization value |
| **company** | **object** | the item belong to which company |
| *id* | integer | company id |
| *name* | string | company name |
| **warranty** | **object** | warranty setting of item |
| *type* | string | warranty type |
| *value* | integer | warranty value |
| *unit* | string | value unit |



<aside class="warning">
Failure
</aside>

```json
{
	"validation": {
		"name": ["dulicate"],
		"number": ["required"]
	},
	"error_name": "illegal form input"
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
|||**item not exist:** item number is incorrect|
|||**illegal form input:** form format does not pass validation|
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| name | array | **required:** it’s necessary parameter |
| number | array | **required:** it’s necessary parameter |
|||**dulicate:** the name has already been taken|
| categories | array | **required:** it’s necessary parameter |
|||**not exist:** category not exist|
| price | array | **required:** it’s necessary parameter |
|||**invaid value:** price need accord to number|
| discount | array | **required:** it’s necessary parameter |
|||**invaid value:** price need accord to integer and between 0 to 100|
| deposit_ratio | array | **invaid value:** price need accord to integer and between 0 to 100|



## Edit Item

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/edit` | 
| Method | `post` | 
| Use | to edit item |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"item_id": 1,
	"name": "item name",
	"number": "item number",
	"categories": [1, 2, 3],
	"price": 123.456,
	"duscount": 30,
	"ean": "",
	"unit": "",
	"contain": "",
	"weblink": "",
	"description": "",
	"images": [{
		"name": "asdasdasd.jpg",
		"cover": true
	}, {
		"name": "qweqweq.jpg",
		"cover": false
	}],
	"videos": [{
		"weblink": "http://asdas.youtube.com",
		"description": ""
	}, {
		"weblink": "http://asda.youtube.com",
		"description": ""
	}],
	"specs": [{
		"id": 1,
		"value": 2
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
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| item_id | integer |  item id |
| name | string |  item name |
| number | string | item number |
| categories | array | category id set |
| price | number | item default price |
| discount | integer | item max discount percent |
| deposit_ratio | integer | deposit ratio of item |
| ean | string | item ean |
| unit | string | item unit |
| contain | string | how many items per unit |
| weblink | string | item’s website URL |
| description | string | item description |
| **images** | **array** | item images |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |
| **videos** | **array** | item videos |
| *weblink* | video url |
| *description* | video description |
| **specs** | **array** | spec setting |
| *id* | spec id |
| *value* | value id of spec |
| **warranty** | **object** | warranty setting of item |
| *type* | string | warranty type - Limited or Lifetime |
| *value* | positive integer (option) | warranty value |
| *unit* | string (option) | value unit - Years or Months |


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
	"validation": {
		"name": ["dulicate"],
		"number": ["required"]
	},
	"error_name": "illegal form input"
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
|||**item not exist:** item number is incorrect|
|||**illegal form input:** form format does not pass validation|
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| name | array | **required:** it’s necessary parameter |
| number | array | **required:** it’s necessary parameter |
|||**dulicate:** the name has already been taken|
| categories | array | **required:** it’s necessary parameter |
|||**not exist:** category not exist|
| price | array | **required:** it’s necessary parameter |
|||**invaid value:** price need accord to number|
| discount | array | **required:** it’s necessary parameter |
|||**invaid value:** price need accord to integer and between 0 to 100|
| deposit_ratio | array | **invaid value:** price need accord to integer and between 0 to 100|



## Delete Item

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/delete` | 
| Method | `post` | 
| Use | to delete item |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"item_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| item_id | integer |  item id |


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
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:| 
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**item not exist:** item number is incorrect|


