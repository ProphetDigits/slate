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
| categories | array | The set of category id |
| price | number | The price of item |
| discount | integer | The max discount of item |
| deposit_ratio | integer | The deposit ratio of item |
| ean | string | The European Article Number |
| unit | string | The unit of amount |
| contain | string | The amount contained in this item |
| weblink | string | The outside website of item |
| description | string | The description of item |
| images | array | The images of item |
| videos | array | The videos of item |
| specs | array | The spec configurations of item |
| spec2s | array | The configurable values of spec2 of item |
| warranty | object | The warranty configuration of item |

| item_image | Type | Description |
| -------: | :---- | :--- |
| name | string | The name will be returned by Upload Image API |
| cover | boolean | The tag of cover image |

| item_video | Type | Description |
| -------: | :---- | :--- |
| weblink | string | The url of vedio |
| description | string | The description of vedio |

| item_spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| value | integer | The id of spec value |

| item_spec2 | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 |
| configurable_values | array | The configurable values of spec2 |

| item_spec2_configurable_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |

| item_warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type - Limited or Lifetime <br/>The parameter of value and unit is unnecessary when type is Lifetime |
| value | positive integer (option) | The duration of warranty |
| unit | string (option) | The unit of duration - Years or Months |


> Return Parameters

### Return Parameters When Success

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


### Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "validation": {
        "name": ["dulicate"],
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
| specs | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| spec2s | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| spec2s.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not belongs to categories </li></ol> |
| spec2s.(index).id.configurable_values | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| spec2s.(index).id.configurable_values.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not belongs to the spec </li></ol> |
| warranty | array (option) | required: <ol><li>The field is required</li></ol> |
| warranty.type | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>Either the data should be Limited or Lifetime</li></ol> |
| warranty.value | array (option) | required: <ol><li>The field is required if type of warranty is Limited</li></ol>invalid: <ol><li>The data is not positive integer</li></ol> |
| warranty.unit | array (option) | required: <ol><li>The field is required if type of warranty is Limited</li></ol>invalid: <ol><li>Either the data should be Years or Months</li></ol> |


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
    "description":"Mit dem edison EVO ist uns ein weiterer Meilenstein gelungen:  Fahrwerksperformance und  Rahmengeometrie sind in einer noch nie  dagewesenen Perfektion kombiniert.",
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
    "specs": [
        {
            "id": 1,
            "name": "son EVO ist ",
            "display_name": "son EVO ist ",
            "value": {
                "id": 206,
                "name": "EVO"
            }
        },{
            "id": 87,
            "name": "son EVO 2st ",
            "display_name": "son EVO ist ",
            "value": {
                "id": 210,
                "name": "SON"
            }
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
| **specs** | **array** | The spec list |
| *id* | integer | spec id |
| *name* | string | spec name |
| *display_name* | string | spec display name |
| *value* | **object** | value id of spec |
| *id* | integer | spec value id |
| *name* | string | spec value display name |
| **warranty** | **object** | warranty setting of item |
| *type* | string | warranty type |
| *value* | integer | warranty value |
| *unit* | string | value unit |


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
| api_key | string | The key will be returned by Sign In API |
| target_company_id | integer | The company id of item |
| item_id | integer | The id of item |


> Return Parameters

### Return Parameters When Success

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "name":"Edison Evo",
    "number": "xxxx",
    "description":"Mit dem edison EVO ist uns ein weiterer Meilenstein gelungen:  Fahrwerksperformance und  Rahmengeometrie sind in einer noch nie  dagewesenen Perfektion kombiniert.",
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
            "compositions": [{
                "id": 2,
                "name": "Second Hands",
                "value": {
                    "id": 2,
                    "name": "Multiply Center Silver",
                    "display_name": "Center Silver",
                    "part_number": "MCS0001",
                    "supplier_number": "SKMCS0001",
                    "description": "description",
                    "comment": "comment....",
                    "compositions": []
                }
            }]
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
| categories | array | The set of category of item |
| prices | object | The prices of item |
| discount | integer | The max discount percent of item |
| deposit_ratio | integer | The deposit ratio of item |
| ean | string | The European Article Number |
| unit | string | The unit of amount |
| contain | string | The amount contained in this item |
| weblink | string | item’s website URL |
| description | string | item description |
| images | array | item images |
| videos | array | item videos |
| specs | array | The configurations of specs |
| customizations | array | The customizable specs of item |
| spec2s | array | The configurations of spec2s |
| company | object | the item belong to which company |
| warranty | object | warranty setting of item |

| item_category | Type | Description |
| -------: | :---- | :--- |
| id | integer |  category id |
| name | string |  category name |

| item_price | Type | Description |
| -------: | :---- | :--- |
| min | number<br/>null | The min price in all variants of item<br/>The value is null indicate no variant of item |
| basic | number | The basic price which be set in the item |
| max | number<br/>null | The max price in all variants of item<br/>The value is null indicate no variant of item |

| item_image | Type | Description |
| -------: | :---- | :--- |
| name | string | The file name |
| cover | boolean | The tag of cover image |
| resource | object | The url of each image resolution |

| item_image_resource | Type | Description |
| -------: | :---- | :--- |
| 240p | string | The picture url of 240 resolution (426x240) |
| 480p | string | The picture url of 480 resolution (854x480) |
| 720p | string | The picture url of 720 resolution (1280x720) |
| 1080p | string | The picture url of 1080 resolution (1920x1080) |

| item_video | Type | Description |
| -------: | :---- | :--- |
| weblink | The url of video |
| description | The description of video |

| item_spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The display name of spec |
| value | object | The value of spec |

| item_spec_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec value |
| name | string | The display name of spec value |

| item_customization | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of customization |
| name | string | The name of customization |
| display_name | string | The display name of customization |
| values | array | The values of customization |

| item_customization_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of customization value |
| name | string | The name of customization value |
| price | number | The extra price of customization value |

| item_spec2 | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 |
| name | string | The name of spec2 |
| display_name | string | The display name of spec2 |
| comment | string | The comment of spec2 |
| part | boolean | The part of spec2 |
| configurable_values | array | The configurable values of spec2 |

| item_spec2_configurable_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |
| name | string | The name of spec2 value |
| display_name | string | The display name of spec2 value |
| part_number | string | The part number of spec2 value |
| supplier_number | string | The supplier number of spec2 value |
| description | string | The description of spec2 value |
| comment | string | The comment of spec2 value |
| compositions | array | The compositions of spec2 value |

| item_spec2_configurable_value_composition | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 |
| name | string | The name of spec2 |
| display_name | string | The display name of spec2 |
| value | object | The configuration of relative spec value<br/>The structure same to item_spec2_configurable_value |

| item_company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of company |
| name | string | The name of company |

| item_company | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type |
| value | integer | The duration of warranty |
| unit | string | The unit of duration |


### Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "validation": {
        "name": ["dulicate"],
        "number": ["required"]
    },
    "error_name": "does not signin"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>lack of parameters: some input parameters missing, not in the request</li><li>does not signin: The api_key is invalid</li><li>not select company yet: The user has not select current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>item not exist: item number is incorrect</li></ul> |



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
| item_id | integer | The id id item |
| name | string | The name of item |
| number | string | The number of item |
| categories | array | The set of category id |
| price | number | The price of item |
| discount | integer | The max discount of item |
| deposit_ratio | integer | The deposit ratio of item |
| ean | string | The European Article Number |
| unit | string | The unit of amount |
| contain | string | The amount contained in this item |
| weblink | string | The outside website of item |
| description | string | The description of item |
| images | array | The images of item |
| videos | array | The videos of item |
| specs | array | The spec configurations of item |
| spec2s | array (option) | The configurable values of spec2 of item |
| warranty | object (option) | The warranty configuration of item |

| item_image | Type | Description |
| -------: | :---- | :--- |
| name | string | The name will be returned by Upload Image API |
| cover | boolean | The tag of cover image |

| item_video | Type | Description |
| -------: | :---- | :--- |
| weblink | string | The url of vedio |
| description | string | The description of vedio |

| item_spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| value | integer | The id of spec value |

| item_spec2 | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 |
| configurable_values | array | The configurable values of spec2 |

| item_spec2_configurable_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |

| item_warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type - Limited or Lifetime <br/>The value and unit is unnecessary when type is Lifetime |
| value | positive integer (option) | The duration of warranty |
| unit | string (option) | The unit of duration - Years or Months |


> Return Parameters

### Return Parameters When Success

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


### Return Parameters When Failure

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
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>illegal_form_input: The form format does not pass validation</li><li>lack of parameters: some input parameters missing, not in the request</li></ul> |
| validation | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | | |
| -------: | :---- | :--- |
| name | array (option) | required: <ol><li>The field is required</li></ol> |
| number | array (option) | required: <ol><li>The field is required</li></ol>duplicate: <ol><li>The data has already been taken</li></ol> |
| categories | array (option) | required: <ol><li>The field is required</li></ol>not exist: <ol><li>The category is not belongs to the current company</li></ol> |
| price | array (option) | required: <ol><li>The field is required</li></ol>invalid value: <ol><li>The data is not number</li></ol> |
| discount | array (option) | required: <ol><li>The field is required</li></ol>invalid value: <ol><li>The data is not number</li><li>The data need between 0 to 100</li></ol> |
| deposit_ratio | array (option) | invalid value: <ol><li>The data is not number</li><li>The data need between 0 to 100</li></ol> |
| ean | array (option) | required: <ol><li>The field is required</li></ol>invalid value: <ol><li>The data is not string</li></ol> |
| unit | array (option) | required: <ol><li>The field is required</li></ol>invalid value: <ol><li>The data is not string</li></ol> |
| contain | array (option) | required: <ol><li>The field is required</li></ol>invalid value: <ol><li>The data is not string</li></ol> |
| weblink | array (option) | required: <ol><li>The field is required</li></ol>invalid value: <ol><li>The data is not string</li></ol> |
| description | array (option) | required: <ol><li>The field is required</li></ol>invalid value: <ol><li>The data is not string</li></ol> |
| images | array (option) | required: <ol><li>The field is required</li></ol> |
| videos | array (option) | required: <ol><li>The field is required</li></ol> |
| specs | array (option) | required: <ol><li>The field is required</li></ol> |
| spec2s | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not array</li></ol> |
| spec2s.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id not in compositions of spec2 </li></ol> |
| spec2s.(index).id.configurable_values.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id not in compositions of spec2 value </li></ol> |
| warranty | array (option) | required: <ol><li>The field is required</li></ol> |



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


