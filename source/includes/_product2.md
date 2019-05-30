# Product2

## Generate Product

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/create` |
| Method | `post` |
| Use | generate products |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "variant_id": 1,
    "quantity": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The key will be returned by Sign In API |
| variant_id | integer | The id of variant |
| quantity | integer | The generated quantity for product |


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
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>variant_not_exist: The variant is not exist or not belongs to current company</li></ul> |


## Product2 List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/list` |
| Method | `post` |
| Use | show product list |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "target_company_id": 1,
    "item_id": 1,
    "variant_id": 1,
    "pagination": {
        "page": 2,
        "per_page": 50
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The key will be returned by Sign In API |
| target_company_id | integer | The company id of variant |
| item_id | integer | The id of item which variant belongs to |
| variant_id | integer | The id of variant<br />It's 0 will return all products |
| pagination | object | The setting of pagination |

| pagination | Type | Description |
| -------: | :---- | :--- |
| page | integer (option) | The specific page in the pagination <ol><li>The default is 1</li><li>The number is 1 when it less than 1</li><li>The number is max page when it more than max page</li></ol> |
| per_page | integer (option) | The quantity of per page<br /> The default is 50 |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "products": [{
        "number": "1A01B021440012345",
        "short_number": "",
        "serial_number":"",
        "sold": false,
        "variants": [],
        "last_holder": {
            "id": 1,
            "given_name": "CC",
            "family_name": "Lee",
            "operator": {
                "id": 1,
                "given_name": "CC",
                "family_name": "Lee",
                "company": {
                    "id": 1,
                    "name": "Bionicon"
                }
            }
        },
        "deposit_owner": {
            "id": 1,
            "name": "Bionicon"
        },
        "purchase_order_number": "AAAA010120160000PO",
        "shipment_number": "AAAA010120160000SH"
    }, {
        "number": "1A01B021440012345",
        "short_number": "",
        "serial_number":"",
        "sold": true,
        "variants": [{
            "id": 1,
            "name": "mutiply k1"
        }, {
            "id": 2,
            "name": "mutiply k2"
        }],
        "last_holder": {
            "id": 0,
            "given_name": "",
            "family_name": "",
            "operator": {
                "id": 1,
                "given_name": "CC",
                "family_name": "Lee",
                "company": {
                    "id": 1,
                    "name": "Bionicon"
                }
            }
        },
        "deposit_owner": {
            "id": 1,
            "name": "Bionicon"
        },
        "purchase_order_number": null,
        "shipment_number": null
    }],
    "pagination": {
        "total": 50,
        "per_page": 50,
        "current_page": 1,
        "last_page": 1
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| products | array | The products which spec same to variant combination |
| pagination | object | The page information |

| product | Type | Description |
| -------: | :---- | :--- |
| number | string | The number of product |
| short_number | string | The short number of product |
| serial_number | string | The serial number of product |
| sold | boolean | The status of product<ol><li>true: sold</li><li>false: unsold</li></ol> |
| printed_at | timestamp | The last printed time of product, the product is not printed will show null |
| last_holder | object | The last holder of product<br />It's null when product not checkin, checkout or sold |
| deposit_owner | object | The company which pay deposit for product |
| purchase_order_number | string | The purchase order number which product is assigned<br />It's null when product is not assigned to purchase order |
| shipment_number | string | The shipment number which product is assigned<br />It's null when product is not assigned to shipment |

| product.last_holder | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of user<br />It will be 0 if product is check out or sold |
| given_name | string | The given name of user<br />It will be empty if product is check out or sold |
| family_name | string | The family name of user<br />It will be empty if product is check out or sold |
| operator | object | The operator for check in or check out or sell |

| product.last_holder.operator | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of user |
| given_name | string | The given name of user |
| family_name | string | The family name of user |
| company | object | The current company when user check in or check out product or sell it |

| product.last_holder.operator.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of company |
| name | string | The name of company |

| product.deposit_owner | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of company |
| name | string | The name of company |

| pagination | Type | Description |
| -------: | :---- | :--- |
| total | integer | The total quantity of product of current variant |
| per_page | integer | The quantity of per page |
| current_page | integer | The current page |
| last_page | integer | The last page |


<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"variant_not_exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>item_not_exist: The item not exist or not belongs to target company</li><li>variant_not_exist: The variant not exist or not belongs to target company</li><li>no_option: The current company does not have option with target company</li></ul> |


## Product2 Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/detail` |
| Method | `post` |
| Use | show product detail information |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "product_number": "1A01B021440012345"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The key will be returned by Sign In API |
| product_number | string | The number of product |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 1836,
    "number": "AAAA01PD",
    "short_number": "00001",
    "serial_number": "",
    "qrcode": "xxxx",
    "sold": false,
    "printed_at": 1520479638,
    "company": {
        "id": 107,
        "name": "AAAA Corp."
    },
    "item": {
        "id": 131,
        "name": " Swift 7"
    },
    "variants": [{
        "id": 169,
        "name": "White",
        "number": "NX.GK6AA.001"
    }],
    "prices": [{
        "currency": "EUR",
        "value": 1000
    }, {
        "currency": "TWD",
        "value": 33602
    }],
    "specs": [{
        "id": 1,
        "name": "Movement",
        "display_name": "Movement",
        "part": true,
        "value": {
            "id": 1,
            "name": "K1-12 auto",
            "display_name": "K1-12 auto",
            "price": {
                "currency": "EUR",
                "value": 9.2
            }
        }
    }, {
        "id": 1,
        "name": "Strap",
        "display_name": "Strap",
        "part": true,
        "value": {
            "id": 0,
            "name": "",
            "display_name": "",
            "price": {
                "currency": "EUR",
                "value": 0
            }
        }
    }],
    "histories": [{
        "id": 1,
        "type": "change_spec",
        "operator": {
            "id": 82,
            "given_name": "Simon",
            "family_name": "Chang",
            "company": {
                "id": 107,
                "name": "AAAA Corp."
            }
        },
        "created_at": 1519713617,
        "spec": {
            "spec": {
                "id": 1,
                "name": "Movement",
                "display_name": "Movement"
            },
            "old_value": {
                "id": 1,
                "name": "Movement",
                "display_name": "Movement"
            },
            "new_value": {
                "id": 0,
                "name": "",
                "display_name": ""
            }
        }
    }],
    "deposit_owner": {
        "id": 107,
        "name": "AAAA Corp."
    },
    "files": [{
        "id": 79,
        "name": "ii.jpg",
        "date": 1517542365,
        "comment": "",
        "uploader": {
            "id": 82,
            "given_name": "Simon",
            "family_name": "Chang",
            "company": {
                "id": 107,
                "name": "AAAA Corp."
            }
        },
        "link": "http://xxx.com/xxx/download"
    }],
    "warranty": {
        "type": "Limited",
        "value": 2,
        "unit": "Years",
        "start_date": 1517542365,
        "end_date": 1517542365
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of product |
| number | string | The number of product |
| short_number | string | The short number of product |
| serial_number | string | The serial number of product |
| qrcode | string | The qrcode of product encoded by base64 |
| sold | boolean | The status of product. <ol><li>true: sold</li><li>false: unsold</li></ol> |
| printed_at | timestamp | The last printed time of product, the product is not printed will show null |
| company | object | The company which product belongs to |
| item | object | The item which product belongs to |
| variants | array | The variants which the spec same as product |
| prices | array | The prices of product in each currencies |
| specs | array | The specs of product |
| histories | array | The histories of product |
| deposit_owner | object | The company of paying deposit |
| files | array | The upload files of product |
| warranty | object | The warranty configuration of product |

| product.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of company |
| name | string | The name of company |

| product.item | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of item |
| number | string | The number of item |
| name | string | The name of item |

| product.variants | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of variant |
| name | string | The name of variant |
| number | string | The number of variant |

| product.prices | Type | Description |
| -------: | :---- | :--- |
| currency | string | The currency |
| value | numeric | The price of product in corresponding currency |

| product.specs | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| part | boolean | The spec is part or not<ol><li>true: It is part</li><li>false: It is not part</li></ol> |
| value | object | The setting of spec in the product |

| product.specs.value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec value |
| name | string | The name of spec value |
| display_name | string | The display name of spec value |
| price | object | The price information of spec value |

| product.specs.value.price | Type | Description |
| currency | string | The currency of price |
| value | numeric | The price of spec value<br /> It's zero if spec of variant not setting |

| product.histories | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of history
| type | string | The type of history <ul><li>add_spec</li><li>change_spec</li><li>delete_spec</li></ul> |
| operator | object | The operator of current action |
| created_at | timestamp | The create time of history |
| spec | object (option) | It's appear when type is add_spec, change_spec and delete_spec |

| product.histories.operator | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of user |
| given_name | string | The given name of user |
| family_name | string | The family name of user |
| company | object | The company of operator |

| product.histories.operator.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of company |
| name | string | The name of company |

| product.histories.spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| old_value | object | The old setting of spec in the product |
| new_value | object | The current setting of spec in the product |

| product.histories.spec.old_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec value |
| name | string | The name of spec value |
| display_name | string | The display name of spec value |

| product.histories.spec.new_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec value |
| name | string | The name of spec value |
| display_name | string | The display name of spec value |

| product.deposit_owner | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of company |
| name | string | The name of company |

| product.files | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of file |
| name | string | The name of file |
| date | timestamp | The uploaded date |
| comment | string | The comment of file |
| uploader | object | The use who uploading file |
| link | string | The download link of file, and it need add api_key to Authorization header in the request |

| product.files.uploader | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of user |
| given_name | string | The given name of user |
| family_name | string | The family name of user |
| company | object | The company of uploader |

| product.files.uploader.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of company |
| name | string | The name of company |

| product.warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type - Limited or Lifetime |
| value | positive integer | The duration of warranty |
| unit | string | The unit of duration - Years or Months |
| start_date | timestamp or null | The start date of warranty. The product not sold yet will be null |
| end_date | timestamp or null | The end date of warranty. The product not sold yet will be null |


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
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>product_not_exist: The product not exist</li><li>no_option: The current company does not have option with company of product</li></ul> |


## Edit Product

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/edit` |
| Method | `post` |
| Use | edit product information |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "product_number": "1A01B021440012345",
    "serial_number": "1A01B021440012345",
    "prices": [{
          "currency": "EUR",
          "value": 1000
    }, {
          "currency": "TWD",
          "value": 33602
    }],
    "specs": [{
        "id": 1,
        "value": 2
    }],
    "added_files": [{
        "name": "proforma.jpg",
        "date": 1498730137,
        "comment": "proforma invoice",
        "resource": ""
    }],
    "deleted_files": [1, 2, 3],
    "warranty": {
        "type": "Limited",
        "value": 2,
        "unit": "Years",
        "start_date": 1498730137,
        "end_date": 1498730137
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The key will be returned by Sign In API |
| product_number | string | The number of product |
| serial_number | string (option) | The serial number of product |
| prices | array (option) | The prices of each currency |
| specs | array (option) | The specs of prodcut |
| added_files | array (option) | The uploading files for product |
| deleted_files | array (option) | A set of file id |
| warranty | object (option) | The warranty configuration of product |

| prices | Type | Description |
| -------: | :---- | :--- |
| currency | integer | The name of currency |
| value | integer | The price of product for corresponding currency |

| specs | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| value | integer | The id of spec value |

| added_files | Type | Description |
| -------: | :---- | :--- |
| name | string | The name of file |
| date | timestamp | The uploading date of file |
| comment | string | The comment of file |
| resource | string | The file data which is encrypted by base64, but exclude mime type |

| warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type - Limited or Lifetime <br/>The parameter is unnecessary when type is Lifetime |
| value | positive integer (option) | The duration of warranty |
| unit | string (option) | The unit of duration - Years or Months |
| start_date | timestamp (option) | The start date of limited warranty for sold product |
| end_date | timestamp (option) | The end date of limited warranty for sold product |

> Return Parameters

### Return Parameters When Success

<aside class="success">
Success
</aside>

The return same to Get Product2 Detail API


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
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>product_not_exist: The product not exist</li><li>no_option: The current company does not have option with company of product</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| serial_number | array (option) | invalid: <ol><li>The data should be string</li></ol> |
| prices | array (option) | invalid: <ol><li>The data should be array</li></ol> |
| prices.(index).currency | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The currency not set in company</li></ol> |
| prices.(index).value | array (option) | required: <ol><li>The field is required</li></ol> invalid: <ol><li>The data should be numeric</li></ol> |
| specs | array (option) | invalid: <ol><li>The data should be array</li></ol> |
| specs.(index).id | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The id is not belongs to item or product </li></ol> |
| specs.(index).value | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>The data is not integer</li><li>The value is not belongs to spec </li></ol> |
| added_files | array (option) | invalid: <ol><li>The data should be array</li></ol> |
| deleted_files | array (option) | invalid: <ol><li>The data should be array</li></ol> |
| warranty.type | array (option) | required: <ol><li>The field is required</li></ol>invalid: <ol><li>Either the data should be Limited or Lifetime</li></ol> |
| warranty.value | array (option) | required: <ol><li>The field is required if type of warranty is Limited and product not sold</li></ol>invalid: <ol><li>The data is not positive integer</li></ol> |
| warranty.unit | array (option) | required: <ol><li>The field is required if type of warranty is Limited and product not sold</li></ol>invalid: <ol><li>Either the data should be Years or Months</li></ol> |
| warranty.start_date | array (option) | required: <ol><li>The field is required if type of warranty is Limited and product is sold</li></ol>invalid: <ol><li>The data is not timestamp</li></ol> |
| warranty.end_date | array (option) | required: <ol><li>The field is required if type of warranty is Limited and product is sold</li></ol>invalid: <ol><li>The data is not timestamp</li></ol> |


## Download Product File

### Description

| Title | Description |
| -------: | :---- |
| URL | it's given by system |
| Method | `get` |
| Use | download product file |
| Notice | |

> Input Headers

### Input Headers

```json
{
    "Authorization": "e4cbcdc2faff41a7e311"
}
```

| Headers | Type | Description |
| -------: | :---- | :--- |
| Authorization | string | The key will be returned by Sign In API |

<aside class="success">
Success
</aside>

The Content-Disposition is inline if file is pdf, others is attachment


### Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "no_authorization"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>no_authorization: The Authorization is invalid</li><li>product_not_exist: The product is not exist</li><li>no_option: The current company of user does not have option with company of product</li><li>file_not_found: The file is not exist</li></ul> |