# Product

## Product List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product/list` |
| Method | `post` |
| Use | show product list |
| Notice |  |


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
| target_company_id | integer | company id which user want get product list |
| variant_id | integer | variant_id |


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
        "serail_number":"",
        "location":"CC Lee",
        "modify_by": {
            "user": {
                "id": 1,
                "given_name": "CC",
                "family_name": "Lee"
            },
            "company": {
                "id": 1,
                "name": "Bionicon"
            }
        },
        "deposit_by": {
            "comapny": {
                "id": 1,
                "name": "Bionicon"
            }
        },
        "purchase_order_number": "AAAA010120160000PO",
        "shipment_number": "AAAA010120160000SH"
    }, {
        "number": "1A01B021440012352",
        "short_number": "15002",
        "serail_number":"",
        "location":"Billy Yan",
        "modify_by": {
            "user": {
                "id": 1,
                "given_name": "CC",
                "family_name": "Lee"
            },
            "company": {
                "id": 1,
                "name": "Bionicon"
            }
        },
        "deposit_by": {
            "comapny": {
                "id": 1,
                "name": "Bionicon"
            }
        },
        "purchase_order_number": "AAAA010120160000PO",
        "shipment_number": "AAAA010120160000SH"
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **products** | array |  |
| number | string | product number |
| short_number | number | product short number |
| serail_number | string | product serial number |
| sold | boolean | product state **0:** normal **1:** sold |
| printed_at | timestamp | the last printed time of product |
| location | string | last location |
| **modify_by** | **object** | last action information |
| *user* | **object** | modify by whom |
| *id* | integer | user id |
| *given_name* | string | given name of user |
| *family_name* | string | family  name of user |
| *company* | **object** | The company which user selected when changed action |
| *id* | integer | company id |
| *name* | string | company name |
| **deposit_by** | **object** | The company which pay deposit for product |
| *company* | **object** | the company which paid deposit|
| *id* | integer | company id |
| *name* | string | company name |
| purchase_order_number | string | purchase order which product is assigned|
| shipment_number | string | shipment which product is assigned|

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
||| **not company member:** the user is not the company member |
||| **no permission:** |


## Generate Product

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product/create` |
| Method | `post` |
| Use | show generate product |
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
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| variant_id | number | variant_id |
| quantity | integer | quantity of product |


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
||| **lack of parameters:** some input parameters missing, not in the request |
||| **does not signin:** user does not signin |
||| **company not exist:** currenct company not exist |
||| **not company member:** the user is not the company member |
||| **no permission:** |


## Product Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product/detail` |
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
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| product_number | string | product’s number |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "number":"1A01B021440012345",
    "short_number":"15001",
    "serial_number": "EE123456",
    "qrcode": ".......",
    "sold": 0,
    "location":"CC Lee",
    "prices": {
        "EUR": "2,700",
        "USA": "2,900"
    },
    "company": {
        "id": 1,
        "name": "Bionicon"
    },
    "item": {
        "id": 1,
        "nmber": "Edison-Evo-1",
        "name": "Edison Evo"
    },
    "variant": {
        "id": 1,
        "name": "Edison Evo"
    },
    "histories":[{
        "location": "CC Lee",
        "type": "Check in",
        "modify_by": {
            "user": {
                "id": 1,
                "given_name": "CC",
                "family_name": "Lee"
            },
                "company": {
                "id": 1,
                "name": "Bionicon"
            }
        },
        "timestamp": "1447679405",
        "comment": "cc check in !"
    }, {
        "location": "Billy Yan",
        "type": "Check out",
        "modify_by": {
            "user": {
                "id": 1,
                "given_name": "CC",
                "family_name": "Lee"
            },
            "company": {
                "id": 1,
                "name": "Bionicon"
            }
        },
        "timestamp": "1447601052",
        "comment": "Billy check out !"
    }],
    "deposit_by": {
        "company": {
            "id": 1,
            "name": "Bionicon"
        }
    },
	"files": [{
		"id": 1,
		"name": "proforma.jpg",
		"date": 1498730137,
		"comment": "proforma invoice",
		"uploaded_by": {
			"id": 1,
			"given_name": "Abc",
			"family_name": "Hi",
			"company": {
				"id": 1,
				"name": "Bike"
			}
		},
		"download": "http:abc.abc.com"
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| number | integer | product number |
| short_number | number | product short number |
| serial_number | string | product serial  number |
| **company** | **object** | products belongs to which company |
| *id* | integer | company id |
| *name* | string | company name |
| **prices** | **object** | product prices |
| currency |  | price currency |
| price |  | price price |
| **item** | **object** | products belongs to which item |
| *id* | integer | item id |
| *number* | string | item number |
| *name* | string | item name |
| **variant** | **object** | products belongs to which variant |
| *id* | integer | variant id |
| *name* | string | variant name |
| sold | boolean | product state, **0:** normal **1:** sold |
| qrcode | string | product qrcode encoded by base64 |
| printed_at | timestamp | the last printed time of product |
| **histories** | **array** | product histories |
| location | string | the user who is the last check in |
| type | string | product check type |
||| param: |
||| **check in** |
||| **check out** |
| **modify_by** | **object** |  |
| *user* | **object** | modify by whom |
| *id* | integer | user id |
| *given_name* | string | given name of user |
| *family_name* | string | family  name of user |
| *company* | **object** | The company which user selected when changed action |
| *id* | integer | company id |
| *name* | string | company name |
| *create_at* | string | timestamp/second |
| *comment* | string | history comment |
| **deposit_by** | **object** | deposit information |
| *company* | **object** | deposit is paid by which company |
| *id* | integer | company id |
| *name* | string | company name |
| **files** | **array** | relative files of shipment |
| *id* | integer | file id |
| *name* | string | file name |
| *date* | timestamp | uploaded date |
| *comment* | string | file comment |
| *uploaded_by* | **object** | uploaded information |
| *id* | integer | user id |
| *given_name* | string | given name of user |
| *family_name* | string | family name of user |
| *company* | **object** | uploaded company information |
| *id* | integer | company id |
| *name* | string | company name |
| *download* | string | download link, need include Authorization header in the request |

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


## Edit Product

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product/edit` |
| Method | `post` |
| Use | edit product information |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "product_num": "1A01B021440012345",
    "serial_number": "1A01B021440012345",
    "added_files": [{
		"name": "proforma.jpg",
		"date": 1498730137,
		"comment": "proforma invoice",
		"resource": ""
	}],
    "deleted_files": [1, 2, 3]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| product_number | string | product’s number |
| serial_number | string (option) | product serial number |
| **added_files** | **array (option)** | uploaded files |
| *name* | string | file name |
| *date* | timestamp | uploaded date |
| *comment* | string | file comment |
| *resource* | string | uploaded data which is encrypted by base64, exclude mime type |
| **deleted_files** | array (option) | a set of file id |


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
||| **permission deny:** not product owner or shipment importer|
| *added_files* | **array (option)** | **invalid format:** required parameter not exist |
||| **invlid date format:** date not timestamp |
| *deleted_files* | **array (option)** | **invalid files:** file id not found |


## Change Product Location

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product/location/edit` |
| Method | `post` |
| Use | to edit product location |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "number":"1A01B021440012345",
    "product_number":"UX76K3NB9",
    "action": "checkin",
    "comment": "receive from Bionicon"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| product_number | string |  product’s number (from scan QR-Code or user keyin) |
| action | string |  "checkin" or "checkout" |
| comment | string |  product check in comment |

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
||| **duplicate check in:** the product is already checked in |
||| **product not exist:** cannot find the product from product number |


## Update Print State Of Products

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product/print` |
| Method | `post` |
| Use | update print state of products |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "products": ["UX76K3NB9", "UX77K3NB9"]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| products | string | a set of product number |

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
||| **lack of parameters:** some input parameters missing, not in the request |
||| **does not signin:** user does not signin |
||| **not select company yet:** user need change current company |
||| **company not exist:** currenct company not exist |
||| **not company member:** the user is not the company member |
||| **no permission:** cannot print |



## Product Detail To Public

### Description

| Title | Description |
| -------: | :---- |
| URL | `product/detail/{product_number}` |
| Method | `get` |
| Use | show particular product information |
| Notice ||


> Input Parameters

### Input Parameters

| Parameter | Type | Description |
| -------: | :---- | :--- |
| product_number | string | product number |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "website": ""
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| website | string | product website |

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
||| **product not found:** product not exist |
