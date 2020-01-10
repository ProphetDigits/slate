# Purchase Order

## Purchase Order List

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.10 / Joey Huang**

  * Modify Fail Parameters:
    * Apply new structure
    * modify descriptions of error messages

  **2019.12.31 / CC**

  * Add Success Example:
    * submit_at
    * currency
    * total_deposit
    * deposit_status

</details>

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


### Return Parameters

> Return Success Parameters

<aside class="success">
Success
</aside>

```json
{
    "purchase_orders_of_brand": [{
        "number": "AAAB160606000001PO",
        "order_status": "Order Confirmed",
        "create_at": 16549832131,
        "delivery_at": 16949832131,
        "submit_at": 1505380536,
        "brand": {
            "id": 1,
            "name": "Company A"
        },
        "retailer": {
            "id": 2,
            "name": "Company B"
        },
        "currency": "CHF",
        "total_deposit": 10,
        "deposit_status": "Paid"
    }],
    "purchase_orders_of_distributor": [{
        "number": "AAAB160606000002PO",
        "order_status": "Open",
        "create_at": 16549832131,
        "delivery_at": 16949832131,
        "submit_at": 1505380536,
        "brand": {
            "id": 1,
            "name": "Company C"
        },
        "retailer": {
            "id": 1,
            "name": "Company B"
        },
        "currency": "CHF",
        "total_deposit": 10,
        "deposit_status": "Paid"
    }],
    "purchase_orders_of_retailer": [{
        "number": "AAAA160606000001PO",
        "order_status": "padding",
        "create_at": 16549832131,
        "delivery_at": 16949832131,
        "submit_at": 1505380536,
        "brand": {
            "id": 4,
            "name": "Company D"
        },
        "retailer": {
            "id": 1,
            "name": "Company A"
        },
        "currency": "CHF",
        "total_deposit": 0,
        "deposit_status": null
    }],
    "purchase_orders_of_not_submmit": [{
        "number": "AAAA160606000002PO",
        "order_status": "Open",
        "create_at": 16549832131,
        "delivery_at": null,
        "submit_at": null,
        "brand": {
            "id": 4,
            "name": "Company D"
        },
        "retailer": {
            "id": 1,
            "name": "Company A"
        },
        "currency": "CHF",
        "total_deposit": 0,
        "deposit_status": null
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| purchase_orders_of_brand | array | The purchase orders from brand point of view |
| purchase_orders_of_distributor | array | (not implements)The purchase orders from distributor point of view |
| purchase_orders_of_retailer | array | The purchase orders from retailer point of view |
| purchase_orders_of_not_submmit | array | The not submitted purchase orders from user point of view |

| purchase_orders | Type | Description |
| -------: | :---- | :--- |
| number | string | purchase order number |
| order_status | string | state of purchase order |
| deposit_status | string | the current deposit status of purchase order |
| currency | string | currency name |
| total_deposit | numberic | total deposit of purchase order |
| create_at | timestamp | create time. Timestamp in seconds |
| delivery_at | timestamp | expected delivery date. Timestamp in seconds |
| submit_at | timestamp | submit date. Timestamp in seconds |
| brand | object | The brand company |
| retailer | object | The purchase company |

| purchase_orders.brand | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id |
| name | string | company name |

| purchase_orders.retailer | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id |
| name | string | company name |


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
| error_name | string |  The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: the request does not include the api_key parameter</li><li>does not signin: the api_key of user does not signin</li><li>not select company yet: the api_key of user need change current company</li><li>company not exist: the api_key of currenct company is not exist</li><li>not company member: the api_key of the user is not the company member</li></ul> |

## Purchase Order Detail

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.10 / Joey Huang**

  * Modify Fail Parameters:
    * Apply new structure
    * modify descriptions of error messages

  **2019.12.31 / CC**

  * Add Success Parameter:
    * deposit_sharing
  * Add Success Example:
    * deposit_sharing
    * currency
  * Modify Success Parameter:
    * items.item.cover_image

</details>

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


### Return Parameters

> Return Success Parameters

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
    "deposit_sharing": 10,
    "currency": "CHF",
    "total_deposit": 50,    
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
            	"display_name": "Red"
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
    "brand": {
        "id": 1,
        "name": ""
    },
    "retailer": {
        "id": 2,
        "name": ""
    },
    "purchaser": {
        "id": 78,
        "given_name": "Hannah",
        "family_name": "Tang",
        "email": "ikea.taichung@gmail.com"
    },
    "importers": [
        {
            "id": 95,
            "name": "IKEA Taiwan"
        }
    ]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| want_deposit | boolean | the result that brand allow retailer to pay deposit |
| enable_assign | boolean | The false means that exception case in this purchase order <ol><li>duplicate spec combination of variant</li><li>product of changing spec combination is assigned to item</li></ol> |
| number | string | purchase order number |
| order_status | string | state of purchase order |
| deposit_status | string | deposit state of purchase order |
| create_at | timestamp | create time(s) |
| delivery_at | timestamp | expected delivery date (s) |
| submit_at | timestamp | submit date (s) |
| pay_deposit | boolean | the retailer want to pay deposit or not |
| deposit_sharing | boolean | deposit sharing percentage for the retailer |
| currency | string | currency name |
| total_deposit | numberic | the amount of deposit of items |
| brand | object | The brand company |
| retailer | object | The purchase company |
| purchaser | object | The purchaser in the purchase order |
| items | array | a set of items |
| address | object | recipient address |
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
| cover_image | object | item cover image it will be empty if no set sover image |

| items.item.cover_image | Type | Description |
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
| error_name | string |  The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: the request does not include the api_key or order_number parameter</li><li>does not signin: the api_key of user does not signin</li><li>not select company yet: the api_key of user need change current company</li><li>company not exist: the api_key of currenct company is not exist</li><li>not company member: the api_key of the user is not the company member</li><li>order not exist: the order_number is incorrect</li></ul> |

## Create Purchase Order

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.10 / Joey Huang**

  * Modify Fail Parameters:
    * Apply new structure
    * modify descriptions of error messages

</details>

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

### Return Parameters

> Return Success Parameters

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
| error_name | string |  The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: the request does not include the api_key parameter</li><li>does not signin: the api_key of user does not signin</li><li>not select company yet: the api_key of user need change current company</li><li>company not exist: the api_key of currenct company is not exist</li><li>not company member: the api_key of the user is not the company member</li><li>brand company not exist: the company_id of company is not exist</li></ul> |

## Submit Purchase Order

<details>
  <summary>Change Log</summary>
  <div class="summary-content">
  
  **2019.12.31 / CC**

  * Modify Success Parameter:
    * Apply new structure

</details>

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
| error_name | string | The name of wrong type <br/><ul><li>lack of parameters: the request does not include the necessary parameters</li><li>does not signin: user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>order not exist: order number is incorrect</li><li>no item: The items of purchase order should more than 0</li><li>invalid address: all column of address is required</li><li>no option: The option is expired or stop</li></ul> |


## Delete Purchase Order

<details>
  <summary>Change Log</summary>
  <div class="summary-content">
  
  **2019.12.31 / CC**

  * Modify Success Parameter:
    * Apply new structure

</details>

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
| error_name | string | The name of wrong type <br/><ul><li>lack of parameters: the request does not include the necessary parameters</li><li>does not signin: user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>order not exist: order number is incorrect</li><li>order submitted : order submitted</li></ul> |


## Edit Purchase Order

<details>
  <summary>Change Log</summary>
  <div class="summary-content">
  
  **2019.12.31 / CC**

  * Modify Input Example:
    * add_items
    * edit_items
    * address
    * histories
    * deposit_histories
    * assign_products
    * cancel_products
    * reassign_products
  * Modify Input Parameter:
    * edit_items: modify description
    * address: modify description
    * assign_products: modify description
    * cancel_products: modify description
    * reassign_products: modify description
    * add_items.variant_id: modify description
    * edit_items.quantity: modify description
    * address.given_name: modify description
    * address.family_name: modify description
  * Modify Success Parameter:
    * Add link
    * Modify description
</details>

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
    "delivery_at": 1577862094,
    "pay_deposit": 1,
    "add_items": [{
      "variant_id": 1266,
  	  "quantity": 1
    }],
    "edit_items": [{
      "variant_id": 1265,
  	  "quantity": 2
    }],
    "address": {
      "given_name": "CC",
      "family_name": "Lee",
      "phone": "0912345678",
      "title": 1,
      "email": "cc@abc.cc",
      "street": "xxx",
      "city": "Taichung",
      "state": "",
      "postal_code": "123",
      "country": "Taiwan"
    },
    "histories": [{
      "status": "Order Confirmed",
      "comment": "test",
      "create_at": 1577775408
    }],
    "deposit_histories": [{
      "status": "Confirmed",
      "comment": "",
      "create_at": 1577775408
    }],
    "assign_products": ["IKEA0000000345PD", "IKEA0000000277PD"],
    "cancel_products": ["IKEA0000000277PD"],
    "reassign_products": ["IKEA0000000276PD"]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | number of purchase order |
| delivery_at | timestamp (option) | expected delivery date. |
| pay_deposit | boolean (option) | the result that whether retailer want to pay deposit or not |
| add_items | array (option) | to add variant to purchase order as item when order not submitted yet |
| edit_items | array (option) | to edit requirement quantity of item when order not submitted yet |
| address | object (option) | to edit address of recipient when order not submitted yet |
| histories | array (option) | a set of histories of purchase order |
| deposit_histories | array (option) | a set of deposit histories of purchase order |
| assign_products | array (option) | a set of product number which should be assigned to purchase order |
| cancel_products | array (option) | a set of product number which should be removed from purchase order |
| reassign_products | array (option) | a set of product number which should be reassigned to purchase order from other purchase order |

| add_items | Type | Description |
| -------: | :---- | :--- |
| variant_id | integer | variant id<br />If the item has been in the purchase order, the quantity will be added to the existing item |
| quantity | integer | purchase quantity |

| edit_items | Type | Description |
| -------: | :---- | :--- |
| variant_id | integer | variant id |
| quantity | integer | purchase quantity<br />If quantity is 0, the item will be removed from purchase order  |

| address | Type | Description |
| -------: | :---- | :--- |
| given_name | string (option) | given name of recipient |
| family_name | string (option) | family name of recipient |
| phone | string (option) | recipient’s phone number |
| title | integer (option) | recipient’s title (0=Mr. 1=Ms.) |
| email | string (option) | recipient’s email |
| street | string (option) | recipient’s address |
| city | string (option) | recipient’s address |
| state | string (option) | recipient’s address |
| postal_code | string (option) | recipient’s address |
| country | string (option) | recipient’s address |

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


### Return Parameters

<aside class="success">
Success
</aside>

The result is the same as [Get Purchase Order Detail](#purchase-order-detail)

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
| error_name | string | The name of wrong type <br/><ul><li>lack of parameters: the request does not include the necessary parameters</li><li>does not signin: user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>order not exist: order number is incorrect</li><li>order submitted: order submitted</li><li>variant not exist: invalid variant id</li><li>invalid item: variant id not exist in brand</li><li>invalid histories: The quantity of histories should more than 0</li><li>product sold: It's forbidden to change sold product</li><li>product not belong to order: the spec combination of product is not same as item </li></ul> |
