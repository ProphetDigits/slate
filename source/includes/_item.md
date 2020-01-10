# Item

## Item Detail Without signin

### Description

| Title | Description |
| -------: | :---- |
| URL | `item/{item_id}/detail` |
| Method | `get` |
| Use | To get item detail without signin |
| Notice | |


### Url Parameters

| Parameter | Type | Description |
| -------: | :---- | :--- |
| item_id | integer | The item id |


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "name":"Edison Evo",
    "description":"Mit dem edison EVO .....",
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
    "specs": [{
        "id": 1,
        "name": "son EVO ist ",
        "display_name": "son EVO ist",
        "value": {
            "id": 206,
            "name": "EVO"
        }
    }, {
        "id": 87,
        "name": "son EVO 2st ",
        "display_name": "son EVO ist",
        "value": {
            "id": 210,
            "name": "SON"
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
| id | integer | The item id |
| name | string | The item name |
| description | string | The description of item |
| prices | object | The prices for each currency |
| images | array | Collection of item image |
| specs | array | The configurations of specs |
| warranty | object | The warranty of item |

| price | Type | Description |
| -------: | :---- | :--- |
| min | number | The min price in all variants. value is null if item doesn’t own variant |
| basic | number | The price of item |
| max | number | The max price in all variants. value is null if item doesn’t own variant |

| image | Type | Description |
| -------: | :---- | :--- |
| name | string | The filename |
| cover | boolean | The tag that decide image is cover or not <ul><li>true: cover image</li><li>false: normal image </li></ul> |
| resource | ojbect | The urls of each resolution |

| image.resource | Type | Description |
| -------: | :---- | :--- |
| px240 | string | The picture url of 240 resolution (426x240) |
| px480 | string | The picture url of 480 resolution (854x480) |
| px720 | string | The picture url of 720 resolution (1280x720) |
| px1080 | string | The picture url of 1080 resolution (1920x1080) |

| spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| value | object | Collection of spec value |

| spec.value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec value |
| name | string | The name of spec value |

| warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type |
| value | integer | The duration of warranty |
| unit | string | The unit of duration |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "item not exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>item not exist: the item id is incorrect</li></ul> |



## Item Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/detail` |
| Method | `post` |
| Use | To get item detail |
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
| api_key | string | The key will be returned by Sign In API |
| target_company_id | integer | The company id of item |
| item_id | integer | The item id |


> Return Success Parameters

### Return Parameters When Success

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "name":"Edison Evo",
    "number": "xxxx",
    "description":"Mit dem edison EVO ist uns ein weiterer...",
    "weblink": "http://evo.bionicon.com/",
    "ean": "",
    "unit": "Set",
    "contain": 1,
    "prices": {
        "EUR": [{
            "min": 50,
            "basic": 100,
            "max": 150
        }],
        "TWD": [{
            "min": 50,
            "basic": 100,
            "max": 150
        }]
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
        "description": "",
        "weblink": "https://youtu.be/70ZkhewCDD8"
    }, {
        "description": "youtube",
        "weblink": "https://youtu.be/G2reQQUQ-Dc"
    }],
    "categories": [{
        "id": 1,
        "name": "xxx"
    }, {
        "id": 2,
        "name": "yyy"
    }],
    "specs": [{
        "id": 1,
        "name": "FIX1",
        "display_name": "FIX1",
        "value": {
            "id": 3,
            "name": "OPTION1"
        }
    }, {
        "id": 2,
        "name": "FIX2",
        "display_name": "FIX2",
        "value": {
            "id": 4,
            "name": "OPTION2"
        }
    }],
    "customizations": [{
        "id": 5,
        "name": "CUST1",
        "display_name": "CUST1",
        "values": [{
            "id": 6,
            "name": "WHITE",
            "price": 5
        }, {
            "id": 7,
            "name": "BLACK",
            "price": 10
        }, {
            "id": 8,
            "name": "GEMBLUE",
            "price": 15
        }]
    }, {
        "id": 9,
        "name": "SIZE",
        "display_name": "SIZE",
        "values": []
    }],
    "spec2s": [{
        "id": 1,
        "name": "Movement",
        "display_name": "Function",
        "comment": "A comment...",
        "part": true,
        "configurable_values": [{
            "id": 1,
            "name": "K1-11 auto",
            "display_name": "K1-11 Auto",
            "part_number": "PK1011",
            "supplier_number": "SK1011",
            "description": "description",
            "comment": "comment....",
            "price": {
                "currency": "EUR",
                "value": 9.2
            }
        }]
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
| id | integer | The id of item |
| name | string | The name of item |
| number | string | The number of item |
| description | string | The item description |
| weblink | string | The website uri of item |
| ean | string | The European Article Number |
| unit | string | The unit of amount |
| contain | string | The amount contained in this item |
| prices | array | The prices of item |
| discount | integer | The max discount percent of item |
| deposit_ratio | integer | The deposit ratio of item |
| company | object | The company of item |
| categories | array | Collection of category |
| images | array | Collection of item image |
| videos | array | Collection of item video |
| specs | array | Collection of spec |
| spec2s | array | Collection of spec2 |
| warranty | object | warranty setting of item |

| price | Type | Description |
| -------: | :---- | :--- |
| min | number or null | The min price in all variants<br/>The value is null indicate no variant of item |
| basic | number | The price of item |
| max | number or null | The max price in all variants<br/>The value is null indicate no variant of item |

| company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

| category | Type | Description |
| -------: | :---- | :--- |
| id | integer | The category id |
| name | string | The category name |

| image | Type | Description |
| -------: | :---- | :--- |
| name | string | The filename |
| cover | boolean | The tag that decide image is cover or not <ul><li>true: cover image</li><li>false: normal image </li></ul> |
| resource | ojbect | The urls of each resolution |

| image.resource | Type | Description |
| -------: | :---- | :--- |
| 240p | string | The picture url of 240 resolution (426x240) |
| 480p | string | The picture url of 480 resolution (854x480) |
| 720p | string | The picture url of 720 resolution (1280x720) |
| 1080p | string | The picture url of 1080 resolution (1920x1080) |

| video | Type | Description |
| -------: | :---- | :--- |
| weblink |string | The url of video |
| description |string | The description of video |

| spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| value | object | Collection of spec value |

| spec.value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec value |
| name | string | The name of spec value |

| customization | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of customization |
| name | string | The name of customization |
| display_name | string | The display name of customization |
| values | array | Collection of customization value |

| customization.value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of customization value |
| name | string | The name of customization value |
| price | number | The extra price of customization value |

| spec2 | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 |
| name | string | The name of spec2 |
| display_name | string | The display name of spec2 |
| comment | string | The comment of spec2 |
| part | boolean | The part of spec2 |
| configurable_values | array | Collection of configurable value |

| spec2.configurable_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |
| name | string | The name of spec2 value |
| display_name | string | The display name of spec2 value |
| part_number | string | The part number of spec2 value |
| supplier_number | string | The supplier number of spec2 value |
| description | string | The description of spec2 value |
| comment | string | The comment of spec2 value |
| price | object | The price information of spec2 value |

| spec2.configurable_value.price | Type | Description |
| -------: | :---- | :--- |
| currency | string | The default currency of company |
| value | numeric | The price of spec value |

| item_warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type |
| value | integer | The duration of warranty |
| unit | string | The unit of duration |

### Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: some input parameters missing, not in the request</li><li>does not signin: The api_key is invalid</li><li>company not exist: target company not exist</li><li>not select company yet: user has not select current company</li><li>not company member: the user is not the company member</li><li>item not exist: item id is incorrect or item not belongs to target company</li></ul> |



## Create Item

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/create` |
| Method | `post` |
| Use | To create item |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "name": "item name",
    "number": "item number",
    "categories": [1, 2, 3],
    "price": 123.456,
    "discount": 30,
    "deposit_ratio": 50,
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
    "spec2s": [{
        "id": 1,
        "configurable_values": [{
            "id": 1
        }, {
            "id": 2
        }]
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
| api_key | string | The key will be returned by Sign In API |
| name | string | The name of item |
| number | string | The number of item |
| categories | array | Collection of category id |
| price | number | The price of item |
| discount | integer | The max discount precent of item |
| deposit_ratio | integer | The deposit ratio of item |
| ean | string | The European Article Number |
| unit | string | The unit of amount |
| contain | string | The amount contained in this item |
| weblink | string | The outside website of item |
| description | string | The description of item |
| images | array | Collection of item image |
| videos | array | Collection of item video |
| specs | array | Collection of spec |
| spec2s | array | Collection of spec2 |
| warranty | object | The warranty configuration of item |

| image | Type | Description |
| -------: | :---- | :--- |
| name | string | The name will be returned by Upload Image API |
| cover | boolean | The tag that decide image is cover or not <ul><li>true: cover image</li><li>false: normal image </li></ul> |

| video | Type | Description |
| -------: | :---- | :--- |
| weblink | string | The url of vedio |
| description | string | The description of vedio |

| spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| value | integer | The id of spec value |

| spec2 | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 |
| configurable_values | array | Collection of configurable_value |

| spec2.configurable_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |

| warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type - Limited or Lifetime <br/>The parameter of value and unit is unnecessary when type is Lifetime |
| value | positive integer (option) | The duration of warranty |
| unit | string (option) | The unit of duration - Years or Months |


### Return Parameters

<aside class="success">
Success
</aside>

The return same to Item Detail API

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "illegal_form_input",
    "validation": {
        "name": ["required"],
        "number": ["required"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: the api_key is invalid</li><li>not_select_company: the user has not select current company</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | If the error_name is 'illegal_form_input', system will show reasons for each error input |

| validation | | |
| -------: | :---- | :--- |
| name | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> |
| number | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> |
| categories | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li><li>The id of category is not exist</li><li>The category is not belongs to the current company </li></ol> |
| price | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not number</li></ol> |
| discount | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The data need between 0 to 100</li></ol> |
| deposit_ratio | array (option) | invalid value: <ol><li>The data is not integer</li><li>The data need between 0 to 100</li></ol> |
| ean | array (option) | required: <ol><li>The field is required</li></ol> |
| unit | array (option) | required: <ol><li>The field is required</li></ol> |
| contain | array (option) | required: <ol><li>The field is required</li></ol> |
| weblink | array (option) | required: <ol><li>The field is required</li></ol> |
| description | array (option) | required: <ol><li>The field is required</li></ol> |
| images | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| videos | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| videos.(index).weblink | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> |
| videos.(index).description | array (option) | required: <ol><li>The field is required</li></ol> |
| specs | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| spec2s | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| spec2s.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not belongs to categories </li></ol> |
| spec2s.(index).id.configurable_values | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| spec2s.(index).id.configurable_values.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not belongs to the spec </li></ol> |
| warranty | array (option) | required: <ol><li>The field is required</li></ol> |
| warranty.type | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>Either the data should be Limited or Lifetime</li></ol> |
| warranty.value | array (option) | required: <ol><li>The field is required if type of warranty is Limited</li></ol>invalid: <ol><li>The data is not positive integer</li></ol> |
| warranty.unit | array (option) | required: <ol><li>The field is required if type of warranty is Limited</li></ol>invalid: <ol><li>Either the data should be Years or Months</li></ol> |



## Edit Item

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/edit` |
| Method | `post` |
| Use | To edit item |
| Notice | |


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
    "discount": 30,
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
    "spec2s": [{
        "id": 1,
        "configurable_values": [{
            "id": 1
        }, {
            "id": 2
        }]
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
| api_key | string | The identity token of user |
| item_id | integer | The item id |
| name | string (option) | The name of item |
| number | string (option) | The number of item |
| categories | array (option) | Collection of category id |
| price | number (option) | The price of item |
| discount | integer (option) | The max discount precent of item |
| deposit_ratio | integer (option) | The deposit ratio of item |
| ean | string (option) | The European Article Number |
| unit | string (option) | The unit of amount |
| contain | string (option) | The amount contained in this item |
| weblink | string (option) | The outside website of item |
| description | string (option) | The description of item |
| images | array (option) | Collection of item image |
| videos | array (option) | Collection of item video |
| specs | array (option) | Collection of spec |
| spec2s | array (option) | Collection of spec2 |
| warranty | object (option) | The warranty configuration of item |

| image | Type | Description |
| -------: | :---- | :--- |
| name | string | The name will be returned by Upload Image API |
| cover | boolean | The tag that decide image is cover or not <ul><li>true: cover image</li><li>false: normal image </li></ul> |

| video | Type | Description |
| -------: | :---- | :--- |
| weblink | string | The url of vedio |
| description | string | The description of vedio |

| spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| value | integer | The id of spec value |

| spec2 | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 |
| configurable_values | array | Collection of configurable_value |

| spec2.configurable_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |

| warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type - Limited or Lifetime <br/>The parameter of value and unit is unnecessary when type is Lifetime |
| value | positive integer (option) | The duration of warranty |
| unit | string (option) | The unit of duration - Years or Months |


### Return Parameters

<aside class="success">
Success
</aside>

Nothing was returned

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "illegal_form_input",
    "validation": {
        "name": ["required"],
        "number": ["required"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: the api_key is invalid</li><li>not_select_company: the user has not select current company</li><li>item not exist: item id is incorrect</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | If the error_name is 'illegal_form_input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| name | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> |
| number | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> |
| categories | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li><li>The id of category is not exist</li><li>The category is not belongs to the current company </li></ol> |
| price | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not number</li></ol> |
| discount | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The data need between 0 to 100</li></ol> |
| deposit_ratio | array (option) | invalid value: <ol><li>The data is not integer</li><li>The data need between 0 to 100</li></ol> |
| ean | array (option) | required: <ol><li>The field is required</li></ol> |
| unit | array (option) | required: <ol><li>The field is required</li></ol> |
| contain | array (option) | required: <ol><li>The field is required</li></ol> |
| weblink | array (option) | required: <ol><li>The field is required</li></ol> |
| description | array (option) | required: <ol><li>The field is required</li></ol> |
| images | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| videos | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| videos.(index).weblink | array (option) | required: <ol><li>The field is required</li><li>The data should not be empty</li></ol> |
| videos.(index).description | array (option) | required: <ol><li>The field is required</li></ol> |
| specs | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| spec2s | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| spec2s.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not belongs to categories </li></ol> |
| spec2s.(index).id.configurable_values | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| spec2s.(index).id.configurable_values.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not belongs to the spec </li></ol> |
| warranty | array (option) | required: <ol><li>The field is required</li></ol> |
| warranty.type | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>Either the data should be Limited or Lifetime</li></ol> |
| warranty.value | array (option) | required: <ol><li>The field is required if type of warranty is Limited</li></ol>invalid: <ol><li>The data is not positive integer</li></ol> |
| warranty.unit | array (option) | required: <ol><li>The field is required if type of warranty is Limited</li></ol>invalid: <ol><li>Either the data should be Years or Months</li></ol> |



## Delete Item

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/delete` |
| Method | `post` |
| Use | To delete item |
| Notice | |


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
| api_key | string | The identity token of user |
| item_id | integer | The item id |


### Return Parameters

<aside class="success">
Success
</aside>

Nothing was returned

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: current company not select</li><li>company not exist: current company not exist</li><li>not company member: user is not member in current company</li></ul> |


