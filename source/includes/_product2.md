# Product2

## Generate Product2

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/create` |
| Method | `post` |
| Use | Generate product2 with variant2 setting |
| Notice | |


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
| api_key | string | The identity token of user |
| variant_id | integer | The variant2 id |
| quantity | integer | The generated quantity |


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
    "error_name":"variant_not_exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>variant_not_exist: The variant2 is not exist or not belongs to current company</li></ul> |



## Product2 List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/list` |
| Method | `post` |
| Use | Show product2 list |
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
    },
    "filter": {
        "sold": true
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| target_company_id | integer | The company id of variant2 |
| item_id | integer | The item id of variant2 |
| variant_id | integer | The variant2 id<br />It's 0 will return all product2 of item |
| pagination | object (option) | The pagination setting <br /> It get all data if without pagination parameters |
| filter | object (option) | The filter setting |

| pagination | Type | Description |
| -------: | :---- | :--- |
| page | integer (option) | The specific page in the pagination <ol><li>The default is 1</li><li>The number is 1 when it less than 1</li><li>The number is max page when it more than max page</li></ol> |
| per_page | integer (option) | The quantity of per page<br /> The default is 50 |

| filter | Type | Description |
| -------: | :---- | :--- |
| sold | boolean (option) | <ol><li>(unuse): The produdcts contain sold and unsold product</li><li>true: Filter out unsold products </li><li>false: Filter out sold products </li></ol> |
| deposit_owner | integer (option) | The company id <br />It's 0 will get the products which deposit owner is not current company |
| holder | integer (option) | The user id <br />It's 0 will get the products which last holder is not current user |
| location | integer (option) | The company id <br />It's 0 will get the products which location is not current company |


> Return Success Parameters

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
        "qrcode": ".....",
        "sold": false,
        "printed_at": 1577635200,
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
        "qrcode": ".....",
        "sold": true,
        "printed_at": 1577635200,
        "variants": [{
            "id": 1,
            "name": "mutiply k1",
            "number": "mk1"
        }, {
            "id": 2,
            "name": "mutiply k2",
            "number": "mk2"
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
| products | array | Collection of product2 |
| pagination | object (option) | The page information <br /> The parameter will appear if you use pagination |

| product | Type | Description |
| -------: | :---- | :--- |
| number | string | The product2 number |
| short_number | string | The short number of product2 |
| serial_number | string | The serial number of product2 |
| qrcode | string | The product2 qrcode encoded by base64 |
| sold | boolean | The status of product2<ol><li>true: sold</li><li>false: unsold</li></ol> |
| printed_at | timestamp / null | The last printed time, the product is not printed will show null |
| last_holder | object / null | The last holder of product<br />It's null when product not checkin, checkout or sold |
| deposit_owner | object | The company of paying deposit |
| purchase_order_number | string / null | The purchase order number which product is assigned<br />It's null when product is not assigned to purchase order |
| shipment_number | string / null | The shipment number which product is assigned<br />It's null when product is not assigned to shipment |

| product.last_holder | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id<br />It's 0 if product is check out or sold |
| given_name | string | The given name of user<br />It will be empty if product is check out or sold |
| family_name | string | The family name of user<br />It will be empty if product is check out or sold |
| operator | object | The operator of check in or check out or sell |

| product.last_holder.operator | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| given_name | string | The given name of user |
| family_name | string | The family name of user |
| company | object | The company when user check in or check out product or sell it |

| product.last_holder.operator.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

| product.deposit_owner | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

| pagination | Type | Description |
| -------: | :---- | :--- |
| total | integer | The total quantity of product2 |
| per_page | integer | The quantity of per page |
| current_page | integer | The current page |
| last_page | integer | The last page |

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>item_not_exist: The item not exist or not belongs to target company</li><li>variant_not_exist: The variant not exist or not belongs to target company</li><li>target_company_not_exist: target company is not exist</li><li>no_option: The current company does not have option with target company</li></ul> |



## Product2 Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/detail` |
| Method | `post` |
| Use | Show product2 detail |
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
| api_key | string | The identity token of user |
| product_number | string | The product2 number |


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
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
        "name": "White"
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
            "id": 1,
            "name": "Movement",
            "display_name": "Movement",
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
    }, {
        "id": 1,
        "type": "checkin",
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
        "comment": ""
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
| number | string | The product2 number |
| short_number | string | The short number of product2 |
| serial_number | string | The serial number of product2 |
| qrcode | string | The product2 qrcode encoded by base64 |
| sold | boolean | The status of product2<ol><li>true: sold</li><li>false: unsold</li></ol> |
| printed_at | timestamp / null | The last printed time, the product is not printed will show null |
| company | object | The company of product2 |
| item | object | The item of product2 |
| variants | array | Collection of variant2 with same spec2 |
| prices | array | Each currency's price |
| specs | array | Collection of spec2 |
| last_holder | object / null | The current holder<br/>It's null when product2 is new and no one uses |
| histories | array | The history logs of product2 |
| deposit_owner | object | The company of paying deposit |
| files | array | Collection of file |
| warranty | object | The warranty configuration of product2 |

| product.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

| product.item | Type | Description |
| -------: | :---- | :--- |
| id | integer | The item id |
| name | string | The item name |

| product.variant | Type | Description |
| -------: | :---- | :--- |
| id | integer | The variant2 id |
| name | string | The variant2 name |

| product.price | Type | Description |
| -------: | :---- | :--- |
| currency | string | The currency name |
| value | numeric | The currency's price |

| product.spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 |
| name | string | The name of spec2 |
| display_name | string | The display name of spec2 |
| part | boolean | The spec2 is part or not<ol><li>true: It is part</li><li>false: It is not part</li></ol> |
| value | object | The spec2 setting of product2 |

| product.spec.value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |
| name | string | The name of spec2 value |
| display_name | string | The display name of spec2 value |
| price | object | The price of spec2 value |

| product.spec.value.price | Type | Description |
| -------: | :---- | :--- |
| currency | string | The currency name |
| value | numeric | The currency's price of spec value<br /> It's zero if spec2 of product2 not setting |

| product.last_holder | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id<br />It's 0 if product is check out or sold |
| given_name | string | The given name of user<br />It's' empty if product is check out or sold |
| family_name | string | The family name of user<br />It's' empty if product is check out or sold |
| operator | object | The operator for check in or check out or sell |

| product.last_holder.operator | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| given_name | string | The given name of user |
| family_name | string | The family name of user |
| company | object | The company when user check in or check out product or sell it |

| product.last_holder.operator.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

| product.history | Type | Description |
| -------: | :---- | :--- |
| id | integer | The history id |
| type | string | The history type <ul><li>checkin</li><li>checkout</li><li>sell</li><li>assign_to_purchase_order</li><li>unassign_from_purchase_order</li><li>assign_to_shipment</li><li>unassign_from_shipment</li><li>add_spec</li><li>change_spec</li><li>delete_spec</li></ul> |
| operator | object | The operator |
| created_at | timestamp | The created time |
| comment | string (option) | The history comment<br />It's exist when type is checkin, checkout, sell, assign_to_purchase_order, unassign_from_purchase_order, assign_to_shipment and unassign_from_shipment |
| spec | object (option) | It's exist when type is add_spec, change_spec and delete_spec |

| product.history.operator | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| given_name | string | The given name of user |
| family_name | string | The family name of user |
| company | object | The company of operator |

| product.history.operator.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

| product.history.spec | Type | Description |
| -------: | :---- | :--- |
| id | integer | The spec2 id |
| name | string | The spec2 name |
| display_name | string | The display name of spec2 |
| old_value | object | The old spec2 setting |
| new_value | object | The current spec2 setting |

| product.history.spec.old_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |
| name | string | The name of spec2 value |
| display_name | string | The display name of spec2 value |

| product.history.spec.new_value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec2 value |
| name | string | The name of spec2 value |
| display_name | string | The display name of spec2 value |

| product.deposit_owner | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

| product.file | Type | Description |
| -------: | :---- | :--- |
| id | integer | The file id |
| name | string | The file name |
| date | timestamp | The uploaded date |
| comment | string | The uploaded comment |
| uploader | object | The user who uploading file |
| link | string | The download link of file, and it need add api_key to Authorization header in the request |

| product.file.uploader | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| given_name | string | The given name of user |
| family_name | string | The family name of user |
| company | object | The company of uploader |

| product.file.uploader.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

| product.warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type - Limited or Lifetime |
| value | positive integer | The duration of warranty |
| unit | string | The unit of duration - Years or Months |
| start_date | timestamp / null | The start date of warranty<br/>It's null when product unsold |
| end_date | timestamp / null | The end date of warranty<br/>It's null when product unsold |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"product_not_exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>product_not_exist: The product not exist</li><li>no_option: The current company does not have option with company of product</li></ul> |



## Edit Product

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/edit` |
| Method | `post` |
| Use | Edit product2 |
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
| api_key | string | The identity token of user |
| product_number | string | The product2 number |
| serial_number | string (option) | The serial number of product2<br/>Only company member can edit |
| prices | array (option) | Each currency's price<br/>Only company member can edit |
| specs | array (option) | Collection of spec2<br/>Only company member can edit |
| added_files | array (option) | Collection of uploading files |
| deleted_files | array (option) | Collection of file id |
| warranty | object (option) | The warranty configuration of product<br/>Only company member can edit |

| prices | Type | Description |
| -------: | :---- | :--- |
| currency | integer | The currency name |
| value | integer | The currency's price |

| specs | Type | Description |
| -------: | :---- | :--- |
| id | integer | The spec2 id |
| value | integer | The id of spec2 value |

| added_files | Type | Description |
| -------: | :---- | :--- |
| name | string | The filename |
| date | timestamp | The uploading date |
| comment | string | The comment |
| resource | string | The file encrypted by base64, but exclude mime type |

| warranty | Type | Description |
| -------: | :---- | :--- |
| type | string | The warranty type - Limited or Lifetime <br/>The parameter is unnecessary when type is Lifetime |
| value | positive integer (option) | The duration of warranty |
| unit | string (option) | The unit of duration - Years or Months |
| start_date | timestamp (option) | The start date of limited warranty for sold product |
| end_date | timestamp (option) | The end date of limited warranty for sold product |


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
    "error_name": "not_sign_in",
    "validation": {
        "serial_number": ["invalid"],
        "prices.0.currency": ["required"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>product_not_exist: The product not exist</li><li>no_option: The current company does not have option with company of product</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | If the error_name is 'illegal_form_input', system will show reasons for each error input |

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



## Checkin Product

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/checkin` |
| Method | `post` |
| Use | Checkin product2 |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "product_number": "1A01B021440012345",
    "comment": ""
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| product_number | string | The product2 number |
| comment | string | The comment for checkin |

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
    "error_name": "illegal_form_input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>product_not_exist: The product not exist</li><li>no_option: The current company does not have option with company of product</li><li>duplicate_action: The product has been checkin by user of this company</li></ul> |



## Checkout Product

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/checkout` |
| Method | `post` |
| Use | Checkout product2 |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "product_number": "1A01B021440012345",
    "comment": ""
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| product_number | string | The product2 number |
| comment | string | The comment for checkout |

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
    "error_name": "not_sign_in"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>product_not_exist: The product not exist</li><li>no_option: The current company does not have option with company of product</li><li>not_checkin_yet: This product is not checkin</li><li>duplicate_action: This product is checkout</li><li>not_your_product: The checkin company is not current company</li></ul> |



## Update Print Date

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product2/print` |
| Method | `post` |
| Use | update print date to multiple products |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "product_number": ["1A01B021440012345", "1A01B021440012346"]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The key will be returned by Sign In API |
| product_number | array | The set of product number |

> Return Parameters

### Return Parameters When Success

<aside class="success">
Success
</aside>

```json
{
}
```


### Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "illegal_form_input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>product_not_exist: <ol><li>The product not exist</li><li>The item of product not exist</li><li>The product not belongs to current company</li></ol></li></ul> |


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