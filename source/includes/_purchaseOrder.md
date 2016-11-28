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
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:** cannot sell in the company|


## Purchase Order  Detail

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
  "number": "AAAA260621000001PO",
  "order_status": "Order Confirmed",
  "create_at": 165698321,
  "delivery_at": 1651321561,
  "brand": {
    "id": 1,
    "name": ""
  },
  "retailer": {
    "id": 2,
    "name": ""
  },
  "items": [],
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
| want_deposit | boolean |  the result that brand allow retailer to pay deposit |
| number | string | purchase order number |
| order_status | string | state of purchase order |
| deposit_status | string | deposit state of purchase order |
| create_at | timestamp | create time(s) |
| delivery_at | timestamp | expected delivery date (s) |
| submit_at | timestamp | submit date (s) |
| pay_deposit | boolean | the result that whether retailer want to pay deposit or not |
| total_deposit | numberic | the amount of deposit of items |
| **brand** | **object** | |
| *id* | integer | company  id |
| *name* | string | company name |
| **retailer** | **object** | |
| *id* | integer | company  id |
| *name* | string | company name |
| **purchaser** | **object** |  |
| *id* | integer | user id |
| *given_name* | - | sell agent’s given name |
| *family_name* | - | sell agent’s family name |
| *email* | - | email of purchaser |
| **items** | **array** | |
| *id* | integer | variant id  |
| *name* | string | variant name |
| **customizations** | **array** | variant customizations |
| *name* | string | customization name |
| *value* | string | name of cusotmization value |
| *quantity* | integer | buy number |
| *deposit* | numberic | item deposit |
| *assign_products* | array | a set of product number |
| **item** |  |  |
| *id* | integer | item id  |
| *name* | string | item name |
| *number* | string | item number |
| **cover_img** | **object** | item cover image it will be empty if no set sover image |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 240 resolution (854x480) |
| *720p* | string | picture url of 240 resolution (1280x720) |
| *1080p* | string | picture url of 240 resolution (1920x1080) |
| **address** | **object** | |
| *given_name* | string | given name of receiver |
| *family_name* | string | family name of receiver |
| *phone* | string | recipient’s phone number |
| *title* | integer | recipient’s title (0=Mr. 1=Ms.) |
| *email* | string | recipient’s email |
| *street* | string | recipient’s address |
| *city* | string | recipient’s address |
| *state* | string | recipient’s address |
| *code* | string | recipient’s address |
| *country* | string | recipient’s address |
| **histories** | **array** |  |
| *status* | string | status of purchase order |
|||**Empty**|
|||**Order Confirmed**|
|||**Delivery Date Confirmed**|
|||**Delivering**|
|||**Completed**|
|||**Order Cancelled**|
| *comment* | string | status comment |
| *create_at* | timestamp | |
| **deposit_histories** | **array** | |
| *status* | string | status of purchase order |
|||**Empty**|
|||**Confirmed**|
|||**Paid**|
|||**Partly  Paid**|
|||**Delayed**|
|||**Unpaid**|
|||**Ignored**|
| *comment* | string | status comment |
| *create_at* | timestamp | |

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
|||**no permission:** cannot sell in the company|
|||**order not exist:** order number is incorrect|


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
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:**  cannot purchase in the current company|


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
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:**  cannot purchase in the current company|
|||**order not exis:**  order number is incorrect|


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
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:**cannot purchase in the current company|
|||**order not exist:** order number is incorrect|
|||**order submitted :** order submitted|


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
  "add_items": [],
  "edit_items": [],
  "address": {},
  "histories": [{
    "status": "",
    "comment": "",
    "create_at": 1466640000
  }],
  "deposit_histories": [{
    "status": "",
    "comment": "",
    "create_at": 1466640000
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | number of purchase order |
| pay_deposit | boolean | the result that whether retailer want to pay deposit or not |
| delivery_at | timestamp | the day which goods was delivered |
| pay_deposit | boolean | the result that whether retailer want to pay deposit or not |
| **add_items** | **array** | to add item to purchase order which not submitted yet. |
| *order_number* | string | number of purchase order |
| *variant_id* | integer | variant id |
| *quantity* | integer | purchase quantity |
| **edit_items** | **array** | to edit item of purchase order which not submitted yet. |
| *order_number* | string | number of purchase order |
| *variant_id* | integer | variant id |
| *quantity* | integer | purchase quantity |
| **address** | **object** | to edit address of purchase order which not submitted yet. |
| *given_name* | string | given name of receiver |
| *family_name* | string | family name of receiver |
| *phone* | string | recipient’s phone number |
| *title* | integer | recipient’s title (0=Mr. 1=Ms.) |
| *email* | string | recipient’s email |
| *street* | string | recipient’s address |
| *city* | string | recipient’s address |
| *state* | string | recipient’s address |
| *code* | string | recipient’s address |
| *country* | string | recipient’s address |
| **histories** | **array** |  |
| *status* | string | status of purchase order |
|||**Empty**|
|||**Order Confirmed**|
|||**Delivery Date Confirmed**|
|||**Delivering**|
|||**Completed**|
|||**Order Cancelled**|
| *comment* | string | status comment |
| *create_at* | timestamp | |
| **deposit_histories** | **array** | |
| *status* | string | status of purchase order |
|||**Empty**|
|||**Confirmed**|
|||**Paid**|
|||**Partly  Paid**|
|||**Delayed**|
|||**Unpaid**|
|||**Ignored**|
| *comment* | string | status comment |
| *create_at* | timestamp | |

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
|||**lack of parameters:** some input parameters missing, not in the request |
|||**does not signin:** user does not signin |
|||**not select company yet:** user need change current company |
|||**company not exist:** currenct company not exist |
|||**not company member:** the user is not the company member |
|||**no permission:**|
|||**order not exist:** order number is incorrect |
|||**order submitted :** order submitted |
|||**variant not exist :** variant id error |
|||**illegal form input:** form format does not pass validation |
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):**|
| title |  | **invalid value:** value isn’t 0 or 1 |
