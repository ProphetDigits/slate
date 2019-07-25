# Purchase Order

## Purchase Order List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/purchase/list` |
| Method | `post` |
| Use | to get the purchase order list in the company.  |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "purchase_orders_of_brand": [{
        "number": "AAAB160606000001PO",
        "order_status": "Open",
        "create_at": 16549832131,
        "delivery_at": 16949832131,
        "brand": {
            "id": 1,
            "name": "Company A"
        },
        "retailer": {
            "id": 2,
            "name": "Company B"
        }
    }],
    "purchase_orders_of_distributor": [{
        "number": "AAAB160606000002PO",
        "order_status": "Open",
        "create_at": 16549832131,
        "delivery_at": 16949832131,
        "brand": {
            "id": 1,
            "name": "Company C"
        },
        "retailer": {
            "id": 1,
            "name": "Company B"
        }
    }],
    "purchase_orders_of_retailer": [{
        "number": "AAAA160606000001PO",
        "order_status": "padding",
        "create_at": 16549832131,
        "delivery_at": 16949832131,
        "brand": {
            "id": 4,
            "name": "Company D"
        },
        "retailer": {
            "id": 1,
            "name": "Company A"
        }
    }],
    "purchase_orders_of_not_submmit": [{
        "number": "AAAA160606000002PO",
        "order_status": "padding",
        "create_at": 16549832131,
        "delivery_at": 16949832131,
        "brand": {
            "id": 4,
            "name": "Company D"
        },
        "retailer": {
            "id": 1,
            "name": "Company A"
        }
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| number | string | purchase order number |
| order_status | string | state of purchase order |
| create_at | timestamp | create time (s) |
| delivery_at | timestamp | expected delivery date (s) |
| submit_at | timestamp | submit date (s) |
| currency | string | currency name |
| total_deposit | numberic | total deposit of purchase order |
| deposit_status | string | the current deposit status of purchase order |
| **brand** | **object** |  |
| *id* | integer | company id |
| *name* | string | company name |
| **retailer** | **object** |  |
| *id* | integer | company id |
| *name* | string | company name |

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


## Purchase Order Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/purchase/detail` |
| Method | `post` |
| Use | to get the purchase order list in the company. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "order_number": "AAAA260621000001PO"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | number of purchase order |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "want_deposit": 1,
    "enable_assign": true,
    "number": "AAAA260621000001PO",
    "order_status": "Order Confirmed",
    "deposit_status": "",
    "create_at": 165698321,
    "delivery_at": 1651321561,
    "submit_at": null,
    "pay_deposit": 1,
    "total_deposit": 50,
    "brand": {
        "id": 1,
        "name": ""
    },
    "retailer": {
        "id": 2,
        "name": ""
    },
    "items": [{
        "id": 1,
        "name": "Basic",
        "quantity": 1,
        "specs": [{
        	"id": 1,
            "name": "Color",
            "display_name": "Color",
            "part": false,
            "value": {
        		"id": 1,
            	"name": "Red",
            	"display_name": "Red",
            }
        }],
        "deposit": 400,
        "assign_products": [],
        "item": {
            "id": 1,
            "name": "Bike",
            "number": "bike001",
            "cover_image": {
                "240p": "http://example/file_240p.png",
                "480p": "http://example/file_480p.png",
                "720p": "http://example/file_720p.png",
                "1080p": "http://example/file_1080p.png"
            }
        }
    }],
    "address": {
        "given_name": "",
        "family_name": "",
        "title": 0,
        "phone": "0321654987",
        "email": "",
        "street": "",
        "city": "",
        "state": "",
        "postal_code": "",
        "country": ""
    },
    "histories": [{
        "status": "",
        "comment": "",
        "create_at": 1466640000
    },{
        "status": "",
        "comment": "Order Confirmed",
        "create_at": 1466640111
    }],
    "deposit_histories": [{
        "status": "",
        "comment": "",
        "create_at": 1466640000
    },{
        "status": "",
        "comment": "Partly Paid",
        "create_at": 1466640111
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| want_deposit | boolean | the result that brand allow retailer to pay deposit |
| enable_assign | boolean | False means that exception case in this purchase order <ol><li>duplicate spec combination of variant</li><li>product of changing spec combination is assigned to item</li></ol> |
| number | string | purchase order number |
| order_status | string | state of purchase order |
| deposit_status | string | deposit state of purchase order |
| create_at | timestamp | create time(s) |
| delivery_at | timestamp | expected delivery date (s) |
| submit_at | timestamp | submit date (s) |
| pay_deposit | boolean | the result that whether retailer want to pay deposit or not |
| currency | string | currency name |
| total_deposit | numberic | the amount of deposit of items |
| brand | object | The brand company |
| retailer | object | The purchase company |
| purchaser | object | The purchaser in the purchase order |
| items | array | a set of items |
| address | object | |
| histories | array | a set of histories of purchase order |
| deposit_histories | array | a set of histories of purchase order |

| brand | Type | Description |
| -------: | :---- | :--- |
| id | integer | company  id |
| name | string | company name |

| retailer | Type | Description |
| -------: | :---- | :--- |
| id | integer | company  id |
| name | string | company name |

| purchaser | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of user |
| given_name | string | The given name |
| family_name | string | The family name |
| email | string | The email |

| items | Type | Description |
| -------: | :---- | :--- |
| id | integer | variant id  |
| name | string | variant name |
| specs | array | variant specs |
| quantity | integer | the purchasing quantity |
| deposit | numberic | item deposit |
| assign_products | array | a set of product number |
| item | object | item information |

| items.specs | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| part | boolean | The spec is part or not<ol><li>true: It is part</li><li>false: It is not part</li></ol> |
| value | object | The setting of spec in the product |

| items.specs.value | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of spec value |
| name | string | The name of spec value |
| display_name | string | The display name of spec value |

| items.item | Type | Description |
| -------: | :---- | :--- |
| id | integer | item id  |
| name | string | item name |
| number | string | item number |
| cover_img | object | item cover image it will be empty if no set sover image |

| items.item.cover_img | Type | Description |
| -------: | :---- | :--- |
| 240p | string | picture url of 240 resolution (426x240) |
| 480p | string | picture url of 240 resolution (854x480) |
| 720p | string | picture url of 240 resolution (1280x720) |
| 1080p | string | picture url of 240 resolution (1920x1080) |

| address | Type | Description |
| -------: | :---- | :--- |
| given_name | string | given name of receiver |
| family_name | string | family name of receiver |
| phone | string | phone number of recipients |
| title | integer | title of recipients (0=Mr. 1=Ms.) |
| email | string | email of recipients |
| street | string | street of recipients |
| city | string | city of recipients |
| state | string | state of recipients |
| postal_code | string | postal_code of recipients |
| country | string | country of recipients |

| histories | Type | Description |
| -------: | :---- | :--- |
| status | string | status of purchase order <ul><li>Empty</li><li>Order Confirmed</li><li>Delivery Date Confirmed</li><li>Delivering</li><li>Completed</li><li>Order Cancelled</li></ul> |
| comment | string | status comment |
| create_at | timestamp | |

| deposit_histories | Type | Description |
| -------: | :---- | :--- |
| status | string | deposit status of purchase order <ul><li>Empty</li><li>Confirmed</li><li>Paid</li><li>Partly Paid</li><li>Delayed</li><li>Unpaid</li><li>Ignored</li></ul> |
| comment | string | status comment |
| create_at | timestamp | |

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
||| **does not signin:** user does not signin |
||| **not select company yet:** user need change current company |
||| **company not exist:** currenct company not exist |
||| **not company member:** the user is not the company member |
||| **order not exist:** order number is incorrect |


## Create Purchase Order

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/purchase/create` |
| Method | `post` |
| Use | to create the purchase order in the company. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "company_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | integer | company id of brand |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "order_number": "AAAA160601000003PO"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| order_number | string | number of purchase order |

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
| error_name | string |the name of the wrong type. |
||| **lack of parameters:** the request does not include the necessary parameters |
||| **does not signin:** user does not signin |
||| **not select company yet:** user need change current company |
||| **company not exist:** currenct company not exist |
||| **not company member:** the user is not the company member |


## Submit Purchase Order

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/purchase/submit` |
| Method | `post` |
| Use | to submit the purchase order. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "order_number": "AAAA160601000003"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | number of purchase order |

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
||| **order not exis:**  order number is incorrect |


## Delete Purchase Order

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/purchase/delete` |
| Method | `post` |
| Use | to delete the purchase order which not submitted yet. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "order_number": "AAAA160601000003"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | number of purchase order |


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
||| **order not exist:** order number is incorrect |
||| **order submitted :** order submitted |


## Edit Purchase Order

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/purchase/edit` |
| Method | `post` |
| Use | to edit purchase order. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "order_number": "AAAA160601000003",
    "delivery_at": 1466640000,
    "pay_deposit": 1,
    "add_items": [],
    "edit_items": [],
    "address": {
        "given_name": "",
        "family_name": "",
        "phone": "",
        "title": "",
        "email": "",
        "street": "",
        "city": "",
        "state": "",
        "code": "",
        "country": ""
    },
    "histories": [{
      "status": "",
      "comment": "",
      "create_at": 1466640000
    }],
    "deposit_histories": [{
      "status": "",
      "comment": "",
      "create_at": 1466640000
    }],
    "assign_products": [],
    "cancel_products": [],
    "reassign_products": []
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | number of purchase order |
| pay_deposit | boolean (option) | the result that whether retailer want to pay deposit or not |
| delivery_at | timestamp (option) | the day which goods was delivered |
| pay_deposit | boolean (option) | the result that whether retailer want to pay deposit or not |
| **add_items** | **array (option)** | to add item to purchase order which not submitted yet. |
| *variant_id* | integer | variant id |
| *quantity* | integer | purchase quantity |
| **edit_items** | **array** | to edit item of purchase order which not submitted yet. |
| *variant_id* | integer | variant id |
| *quantity* | integer | purchase quantity |
| **address** | **object (option)** | to edit address of purchase order which not submitted yet. |
| *given_name* | string (option) | given name of receiver |
| *family_name* | string (option) | family name of receiver |
| *phone* | string (option) | recipient’s phone number |
| *title* | integer (option) | recipient’s title (0=Mr. 1=Ms.) |
| *email* | string (option) | recipient’s email |
| *street* | string (option) | recipient’s address |
| *city* | string (option) | recipient’s address |
| *state* | string (option) | recipient’s address |
| *code* | string (option) | recipient’s address |
| *country* | string (option) | recipient’s address |
| **histories** | **array (option)** |  |
| *status* | string | status of purchase order |
|||**Empty**|
|||**Order Confirmed**|
|||**Delivery Date Confirmed**|
|||**Delivering**|
|||**Completed**|
|||**Order Cancelled**|
| *comment* | string | status comment |
| *create_at* | timestamp | |
| **deposit_histories** | **array (option)** ||
| *status* | string | status of purchase order |
|||**Empty**|
|||**Confirmed**|
|||**Paid**|
|||**Partly  Paid**|
|||**Delayed**|
|||**Unpaid**|
|||**Ignored**|
| *comment* | string | status comment |
| *create_at* | timestamp ||
| assign_products | array (option) | a set of product number which assigned to purchase order |
| cancel_products | array (option) | a set of product number which remove-assigned from purchase order |
| reassign_products | array (option) | a set of product number which reassigned to purchase order from other purchase order |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
}
```

The return same to Get Purchase Order Detail API


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
||| **order not exist:** order number is incorrect |
||| **order submitted :** order submitted |
||| **variant not exist :** invalid variant id |
||| **importer not exist:** invalid importer id|
||| **illegal form input:** form format does not pass validation |
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. |
| *title* | string (option) | **invalid value:** value isn’t 0 or 1 |
