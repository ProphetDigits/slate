# Order

## Order List

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.01.07 / Jianhua**

  * Modify Use Description
  * Modify Input Parameters:
    * api_key: modify description
  * Modify Success Parameters
    * remove italic style
    * modify create_at description
    * modify refund_at description
    * modify retailer description
    * modify agent description
    * add null type to refund_at field
  * Modify Failure Parameters:
    * Apply new structure
    * Remove "no permission" in error_name

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/list` |
| Method | `post` |
| Use | To get the order list of company |
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
| api_key | string | The identity token of user |

> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "orders": [{
        "number": "AAAA160401000002OD",
        "currency": "JPY",
        "total": 24288,
        "order_status": "Cancelled",
        "payment_status": "Closed",
        "transaction_id": "",
        "create_at": 1459491797,
        "refund_at": 1459491797,
        "retailer": {
            "id": 1,
            "name": "Company A"
        },
        "agent": {
            "id": 1,
            "given_name": "QQ",
            "family_name": "Wang",
            "email": "a@gamil.com"
        }
    },{
        "number": "AAAA160401000001OD",
        "currency": "CHF",
        "total": 284.04,
        "order_status": "Open",
        "payment_status": "Open",
        "create_at": 1459491797,
        "refund_at": 1459491797,
        "retailer": {
            "id": 1,
            "name": "Company A"
        },
        "agent": {
            "id": 1,
            "given_name": "QQ",
            "family_name": "Wang",
            "email": "a@gamil.com"
        }
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| number | string | order number |
| currency | string | payment currency |
| total | double | order total price |
| order_status | string | order status |
| payment_status | string | payment status |
| payment_method | string | payment method |
| transaction_id | string | transaction id  |
| create_at | timestamp | created time in the number of seconds |
| refund_at | timestamp / null | refunded time in the number of seconds |
| retailer | object | salesperson's company |
| agent | object | salesperson |

| retailer | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id |
| name | string | company name |

| agent | Type | Description |
| -------: | :---- | :--- |
| id | integer | user id |
| given_name | string | user given name |
| family_name | string | user family name |
| email | string | user email |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li></ul> |



## Create Order

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.01.07 / Jianhua**

  * Modify Use Description
  * Modify Input Parameters:
    * api_key: modify description
    * type: modify description
  * Modify Success Parameters:
    * Modify qrcode description
    * Add null type to qrcode field
  * Modify Failure Parameters:
    * Apply new structure
    * Remove "no permission" from error_name field
    * Add products, order_number, payment_method and qrcode

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/create` |
| Method | `post` |
| Use | To create order |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "cart_id": "C00001",
  "type": "credit_card"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| cart_id | integer | cart id |
| type | string | payment method<ul><li>cash</li><li>credit_card</li><li>PayPal</li><li>cash_consumer_app</li><li>credit_card_consumer_app</li></ul> |


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "order_number":"AAAA160509000001OD",
  "payment_method": "PayPal",
  "qrcode": ""
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| order_number | string | order number |
| payment_method | string | payment method<ul><li>cash</li><li>credit_card</li><li>PayPal</li><li>cash_consumer_app</li><li>credit_card_consumer_app</li></ul> |
| qrcode | string / null | a base64 string of qr-code image.<br/>It's null when payment method is credit_card or cash |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"product invalid",
    "products": [
      "AAAA0000000001",
      "AAAB0000000001"
    ]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>cart not exist: the cart id is invalid</li><li>repeat: order has be created by this cart</li><li>no products: there are no products in the cart</li><li>product invalid: some products which no option or item has been deleted or currency price has been deleted, but those still in the cart</li></ul> |
| products | array (option) | Collection of product number.<br/>It's show when error_name is product invalid |
| order_number | string (option) | order number.<br/>It's show when error_name is repeat |
| payment_method | string (option) | payment method.<br/>It's show when error_name is repeat<ul><li>cash</li><li>credit_card</li><li>PayPal</li><li>cash_consumer_app</li><li>credit_card_consumer_app</li></ul> |
| qrcode | string / null (option) | a base64 string of qr-code image.<br/>It's null when payment method is credit_card or cash.<br/>It's show when error_name is repeat |



## Order Payment

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.01.07 / Jianhua**

  * Modify Use Description
  * Modify Input Parameters:
    * api_key: modify description
  * Modify Success Parameters:
  * Remove Success Example:
  * Modify Failure Parameters:
    * Apply new structure
    * Remove "no permission" from error_name field
    * Remove "not retailer order" from error_name field
    * Remove "request timeout" from error_name field

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/payment/` |
| Method | `post` |
| Use | To set transaction_id make order paid by payworks completed |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "order_number": "C00001",
  "transaction_id": "UXI2KS784JOC9A0"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| order_number | string | order number |
| transaction_id | string | transaction id of payworks |


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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>order not exist: <ol><li>order number is invalid</li><li>user is not salesperson</li><li>currenct company not salesperson's company</li></ol></li><li>repeated: transaction id is exist</li><li>confirming: order is confirming</li><li>paid: order has been paid</li><li>closed: order has been closed</li><li>refunded: order has been refunded</li></ul> |



## Cancel Order

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.01.07 / Jianhua**

  * Modify Use Description
  * Modify Input Parameters:
    * api_key: modify description
  * Modify Success Parameters:
  * Remove Success Example:
  * Modify Failure Parameters:
    * Apply new structure
    * Remove "no permission" from error_name field

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/cancel` |
| Method | `post` |
| Use | to cancel order which not pay yet or error |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "order_number": "C00001"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| order_number | string | order number |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>order not exist: <ol><li>order number is invalid</li><li>user is not salesperson</li></ol></li><li>confirming: order is confirming</li><li>paid: order has been paid</li><li>closed: order has been closed</li><li>refunded: order has been refunded</li></ul> |



## Refund

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.01.07 / Jianhua**

  * Modify Use Description
  * Modify Input Parameters:
    * api_key: modify description
    * transaction_id: modify description
  * Modify Success Parameters:
  * Remove Success Example:
  * Modify Failure Parameters:
    * Apply new structure
    * Remove "no permission" from error_name field
    * Remove "timeout" from error_name field

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/refund` |
| Method | `post` |
| Use | To refund order |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "transaction_id": "UXI2KS784JOC9A0",
  "order_number": "C00001"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| transaction_id | string | refund transaction id of payworks, other payment method is empty |
| order_number | string | order number |


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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>order not exist: <ol><li>order number is invalid</li><li>user is not salesperson</li></ol></li><li>not reatiler order: only order of salesperson's company can refund </li><li>open: order just open state</li><li>confirming: order is confirming</li><li>closed: order has been closed</li><li>refunded: order has been refunded</li><li>refund expired: payment has been exceeded 30 days</li><li>repeated: refunded transaction id is exist</li><li>transaction not found: refund transaction id is invalid</li><li>invalid transaction id: refund transaction id does not match order</li></ul> |



## Order Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/detail` |
| Method | `post` |
| Use | to get the order detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "order_number": "AAAA160401000001OD"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | order number |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "number": "AAAA160401000003OD",
  "currency": "JPY",
  "total": 24414,
  "order_status": "Open",
  "payment_status": "Open",
  "payment_method": null,
  "transaction_id": null,
  "create_at": 1459491885,
  "refund_at": 1459491885,
  "retailer": {
    "id": 1,
    "name": "Company A"
  },
  "agent": {
    "id": 1,
    "given_name": "QQ",
    "family_name": "Wang",
    "email": "a@gmail.com"
  },
  "products": [{
    "number": "AAAA0000000004PD",
    "company": {
      "id": 1,
      "name": "Company Test"
    },
    "item": {
      "id": 1,
      "number": "Test-Item-1",
      "name": "Test Item 1"
    },
    "variants": [{
        "id": 1,
        "name": "mutiply k1"
    }, {
        "id": 2,
        "name": "mutiply k2"
    }],
    "price": 100,
    "discount_price": 85,
    "product_status": "initial"
  },{
    "number": "AAAA0000000005PD",
    "company": {
      "id": 1,
      "name": "Company Test"
    },
    "item": {
      "id": 1,
      "number": "Test-Item-1",
      "name": "Test Item 1"
    },
    "variants": [{
      "id": 2,
      "name": "Variant Test"
    }],
    "price": 100,
    "discount_price": 85,
    "product_status": "initial"
  }],
  "histories": [{
    "order_status": "Open",
    "payment_status": "Open",
    "comment": "",
    "create_at": 1461312001,
    "user": {
      "id": 1,
      "given_name": "QQ",
      "family_name": "Wang"
    }
  },{
    "order_status": "Error",
    "payment_status": "Closed",
    "comment": "request timeout",
    "create_at": 1461312055,
    "user": {
      "id": 1,
      "given_name": "QQ",
      "family_name": "Wang"
    }
  }],
  "shipping_address": {
    "title": null,
    "given_name": null,
    "family_name": null,
    "phone": null,
    "email": null,
    "street": null,
    "city": null,
    "state": null,
    "code": null,
    "country": null
  },
  "billing_address": {
    "title": null,
    "given_name": null,
    "family_name": null,
    "phone": null,
    "email": null,
    "street": null,
    "city": null,
    "state": null,
    "code": null,
    "country": null
  },
  "invoices": [{
    "number": "AAAA170329000006IN",
    "brand": {
      "id": 1,
      "name": "Company A"
    },
    "create_at": 1490776038,
    "comment": "AAAA170329000001OD",
    "download": "http://192.168.1.116/BrandCloud/order/AAAA170329000001OD/invoice/AAAA170329000006IN/download"
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| number | string | order number |
| currency | string | payment currency |
| total | double | order total price |
| order_status | string | order status |
| payment_status | string | payment status |
| payment_method | string | payment method |
| transaction_id | string | transaction id |
| create_at | timestamp | create time |
| refund_at | timestamp | refund time |
| retailer | object | The reatiler of order |
| agent | object | The creator of order |
| billing_address | object | The billing address of order |
| shipping_address | object | The shipping address of order |
| products | array | The order products |
| histories | array | The order histories |
| invoices | array | The order invoices |

| order.retailer | Type | Description |
| -------: | :---- | :--- |
| id | integer | company  id |
| name | string | company name |

| order.agent | Type | Description |
| -------: | :---- | :--- |
| id | integer | user id |
| given_name | string | sell agent’s given name |
| family_name | string | sell agent’s family name |

| order.billing_address | Type | Description |
| -------: | :---- | :--- |
| given_name | string | The recipient’s given_name |
| family_name | string | The recipient’s family_name |
| phone | string | The recipient’s phone number |
| title | integer | The recipient’s title (0=Mr. 1=Ms.) |
| email | string | The recipient’s email |
| street | string | The recipient’s street |
| city | string | The recipient’s city |
| state | string | The recipient’s state |
| code | string | The recipient’s code |
| country | string | The recipient’s country |

| order.shipping_address | Type | Description |
| -------: | :---- | :--- |
| given_name | string | The recipient’s given_name |
| family_name | string | The recipient’s family_name |
| phone | string | The recipient’s phone number |
| title | integer | The recipient’s title (0=Mr. 1=Ms.) |
| email | string | The recipient’s email |
| street | string | The recipient’s street |
| city | string | The recipient’s city |
| state | string | The recipient’s state |
| code | string | The recipient’s code |
| country | string | The recipient’s country |

| order.product | Type | Description |
| -------: | :---- | :--- |
| number | string | The product number |
| company | object | The company of product |
| item | object | The item of product |
| variants | array | The variants of product |

| order.product.company | Type | Description |
| -------: | :---- | :--- |
| id | string | company id of product |
| name | string | company name of product |

| order.product.item | Type | Description |
| -------: | :---- | :--- |
| id | integer | item id of products |
| number | string | item number of product |
| name | string | item name of product |

| order.product.variant | Type | Description |
| -------: | :---- | :--- |
| id | string | variant id of product |
| name | string | variant name of product |
| price | double | product price |
| discount_price | double | product discount price |
| product_status | string | the location of work flow of product |

| order.history | Type | Description |
| -------: | :---- | :--- |
| order_status | string | order status |
| payment_status | string | payment status |
| comment | string | The comment of action |
| create_at | timestamp | order status changed time |
| user | object | The operator of action |

| order.history.user | Type | Description |
| -------: | :---- | :--- |
| id | integer | user id |
| given_name | string | user’s given name |
| family_name | string |  user’s family name |

| order.invoice | Type | Description |
| -------: | :---- | :--- |
| number | string | invoice number|
| brand | object | invoice creator |
| create_at | timestamp | creating time of invoice |
| comment | string | order number |
| download | string | The url of invoice for download, visit the url need to add header Authorization and value is api_key |

| order.invoice.brand | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id |
| name| string | company name |

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


## Send PayPal Payment Link

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/paypal/send` |
| Method | `post` |
| Use | to send PayPal Payment link to consumer. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "email": "a@gmail.com",
    "order_number": "AAAA0000000789OD"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| email | string | consumer email |
| order_number | string | order number which consumer want to pay by PayPal buy no scanner |

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
| error_name | string | the name of the wrong type |
||| **does not signin:** user does not signin |
||| **order not exist:** invalid order number |
||| **invalid email:** invalid email |
||| **invalid payment:** only PayPal can use this api |
||| **paid:** order has been paid |
||| **confirming:**  order is confirming |
||| **closed :** order has been closed |
||| **refunded:** order has been refunded |


## Transaction Result

### Description

| Title | Description |
| -------: | :---- |
| URL | `transaction/{token}/result` |
| Method | `get` |
| Use | to get the information for PayPal payment. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "token": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| token | string | a temporary token for payment. |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "date": 1459491797,
    "status": "success",
    "order": {
        "number": "AAAA170329000001OD",
        "payment_method": "PayPal",
        "transaction": "123546876",
        "currency": "EUR",
        "total": 100,
        "retailer": "TW Shop",
        "payer": "a@gmail.com"
    }
}
```

```json
{
    "date": 1459491797,
    "status": "fail",
    "fail": {
        "refused_by": "PayPal",
        "code": "012",
        "description": "card expired"
    }
}
```

```json
{
    "date": 1459491797,
    "status": "info"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| date | timestamp | payment date |
| status | string | payment status, success or fail or info <br /> the order parameter will appear if the status is success otherwise, the fail parameter will appear |
| odrer | object |  |
| fail | object |  |

| odrer | Type | Description |
| -------: | :---- | :--- |
| *number* | string | order number |
| *payment_method* | string | payment method of order |
| *transaction* | string | transaction id of order |
| *currency* | string | payment currency |
| *total* | number | total price of payment |
| *retailer* | string | seller's company name |
| *payer* | string | payer email |

| fail | Type | Description |
| -------: | :---- | :--- |
| *refused_by* | string | By whom was this action refused, Server or PayPal |
| *code* | string | fail code of PayPal |
| *description* | string | fail description |


<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"log expired"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | the name of the wrong type |
||| **result not exist:** order number invalid |


## Query Refund Requirement Of Order

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/refund/query` |
| Method | `post` |
| Use | To check the order meets refund requirement |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "order_number": "C00001"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | Order number |

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
| error_name | string | The failed reason which HTTP code is 403 |
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**order not exist:**  order is not exist|
|||**refund expired:** after the order has been created over 30 days, it can't refund|
|||**confirming:**  order is confirming|
|||**closed :** order has been closed|
|||**refunded:** order has been refunded|
|||**open:**  initial order status|


## Partial  Order  Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `order/{order_number}/detail` |
| Method | `get` |
| Use | to get the partial order detail |
| Notice |  |

> Header Parameters

### Header Parameters

```json
{
    "Authorization": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| Authorization | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |


> Input Parameters

### Input Parameters

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "number": "AAAA160401000003OD",
  "currency": "JPY",
  "subtotal": 25300,
  "total_discount": 886,
  "total": 24414,
  "order_status": "Open",
  "payment_status": "Open",
  "payment_method": null,
  "retailer": {
    "id": 1,
    "name": "Company A",
    "cover_img": {
        "resource": {
            "px240": "http://xxxx_240p.jpeg",
            "px480": "http://xxxx_480p.jpeg",
            "px720": "http://xxxx_720p.jpeg",
            "px1080": "http://xxxx_1080p.jpeg"
        }
    },
    "address": {
        "street": "333 West San Carlos Street Suite 1500",
        "city": " San Jose",
        "state": "CA",
        "postal_code": "95110",
        "country": "United States"
    }
  },
  "products": [{
    "number": "AAAA0000000004PD",
    "company": {
      "id": 1,
      "name": "Company Test"
    },
    "item": {
      "id": 1,
      "number": "Test-Item-1",
      "name": "Test Item 1"
    },
    "variant": {
      "id": 2,
      "name": "Variant Test",
      "cover_img": {
          "resource": {
              "px240": "http://xxxx_240p.png",
              "px480": "http://xxxx_480p.png",
              "px720": "http://xxxx_720p.png",
              "px1080": "http://xxxx_1080p.png"
          }
      }
    },
    "price": 100,
    "discount_price": 85,
    "selling_price": 15
  },{
    "number": "AAAA0000000005PD",
    "company": {
      "id": 1,
      "name": "Company Test"
    },
    "item": {
      "id": 1,
      "number": "Test-Item-1",
      "name": "Test Item 1"
    },
    "variant": {
      "id": 2,
      "name": "Variant Test",
        "cover_img": {
            "resource": {
                "px240": "http://xxxx_240p.png",
                "px480": "http://xxxx_480p.png",
                "px720": "http://xxxx_720p.png",
                "px1080": "http://xxxx_1080p.png"
            }
        }
    },
    "price": 1358.85,
    "discount_price": 289.38,
    "selling_price": 1069.47
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| number | string | order number |
| currency | string | payment currency |
| subtotal | double | order subtotal price |
| total_discount | double | order total discount price |
| total | double | order total price |
| order_status | string | order status |
| payment_status | string | payment status |
| payment_method | string | payment method |
| retailer | object |  |
| products | array |  |
| *discount_price* | double | product discount price |
| *selling_price* | double | product selling price |


| retailer | Type | Description |
| -------: | :---- | :--- |
| *id* | integer | company  id |
| *name* | string | company name |
| *cover_img* | object | item cover image. It will be empty if no set cover image |
| *address* | object | retailer's address |

| retailer.cover_img | Type | Description |
| -------: | :---- | :--- |
| *resource* | object | item cover image. It will be empty if no set cover image |

| retailer.cover_img.resource | Type | Description |
| -------: | :---- | :--- |
| *px240* | string | picture url of 240 resolution (426x240) |
| *px480* | string | picture url of 480 resolution (854x480) |
| *px720* | string | picture url of 720 resolution (1280x720) |
| *px1080* | string | picture url of 1080 resolution (1920x1080) |

| address | Type | Description |
| -------: | :---- | :--- |
| *street* | string | retailer's street  |
| *city* | string |  retailer's city  |
| *state* | string |  retailer's state  |
| *post_code* | string |  retailer's post code  |
| *country* | string |  retailer's country  |

| product | Type | Description |
| -------: | :---- | :--- |
| *number* | string | product number |
| company | object | company of product |
| item | object | item of product |
| variant | object | variant of product |

| product.company | Type | Description |
| -------: | :---- | :--- |
| *id* | string | company id of product |
| *name* | string | company name of product |

| product.item | Type | Description |
| -------: | :---- | :--- |
| *id* | integer | item id of products |
| *number* | string | item number of product |
| *name* | string | item name of product |

| product.variant | Type | Description |
| -------: | :---- | :--- |
| *id* | string | variant id of product |
| *name* | string | variant name of product |
| *cover_img* | object | item cover image. It will be empty if no set cover image |

| product.variant.cover_img | Type | Description |
| -------: | :---- | :--- |
| *resource* | object | item cover image. It will be empty if no set cover image |

| product.variant.cover_img.resource | Type | Description |
| -------: | :---- | :--- |
| *px240* | string | picture url of 240 resolution (426x240) |
| *px480* | string | picture url of 480 resolution (854x480) |
| *px720* | string | picture url of 720 resolution (1280x720) |
| *px1080* | string | picture url of 1080 resolution (1920x1080) |
| *price* | double | product price |

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
| error_name | String | The name of wrong type |
| | | <ul><li>not_sign_in: The api_key is invalid</li></ul>|
| | | <ul><li>order_not_bound_same_user: order has been bound with another user</li></ul> |
| | | <ul><li>order_not_exist: order number is incorrect</li></ul> |
| | | <ul><li>order_is_finished: order is finished</li></ul> |
| | | <ul><li>order_is_aborted: order is aborted</li></ul> |
| | | <ul><li>order_is_timeout: order is timeout</li></ul> |


## Confirm Purchase

### Description

| Title | Description |
| -------: | :---- |
| URL | `order/confirmpurchase` |
| Method | `post` |
| Use | to bind the order with current user |
| Notice |  |

> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "order_number": "AAAA160401000001OD"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | order number |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "profile" : {
        "given_name": "CC",
        "family_name": "Lee",
        "title": 1,
        "phone": "0912345678"
    },
    "default_address" : {
        "street":"ABC st.",
        "city":"Taichung",
        "state":"Taiwan",
        "code":"30123",
        "country":"R.O.C."
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| profile | object | |
| default_address | object | |


| profile | Type | Description |
| -------: | :---- | :--- |
| *given_name* | string | given_name |
| *family_name* | string | family_name |
| *title* | integer | title (0=Mr. 1=Ms.) |
| *phone* | string | phone number |

| default_address | Type | Description |
| -------: | :---- | :--- |
| *street* | string | recipient’s address |
| *city* | string | recipient’s address |
| *state* | string | recipient’s address |
| *code* | string | recipient’s address |
| *country* | string | recipient’s address |

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
| error_name | String | The name of wrong type |
| | | <ul><li>not_sign_in: The api_key is invalid</li></ul>|
| | | <ul><li>order_not_bound_same_user: order has been bound with another user</li></ul> |
| | | <ul><li>order_not_exist: order number is incorrect</li></ul> |



## Edit Order

### Description

| Title | Description |
| -------: | :---- |
| URL | `order/edit` |
| Method | `post` |
| Use | to edit the order's billing address with current user |
| Notice |  |

> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "order_number": "AAAA160401000001OD",
    "billing_address": {
      "given_name":"Lee",
      "family_name":"CC",
      "title": 0,    
      "phone":"0912345678",
      "street":"ABC st.",
      "street2":"ABC st.",
      "city":"Taichung",
      "state":"Taiwan",
      "code":"30123",
      "country":"R.O.C."
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | order number |
| billing_address | object | order's billing address |
| *given_name* | string | recipient’s given_name |
| *family_name* | string | recipient’s family_name |
| *phone* | string | recipient’s phone number |
| *title* | integer | recipient’s title (0=Mr. 1=Ms.) |
| *street* | string | recipient’s address |
| *street2* | string | recipient’s address |
| *city* | string | recipient’s address |
| *state* | string | recipient’s address |
| *code* | string | recipient’s address |
| *country* | string | recipient’s address |

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


<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"illegal_form_input",
  "validation": {
      "given_name": ["required"],
      "family_name": ["required"],
      "title": ["invalid"]
  }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type|
| | | <ul><li>not_sign_in: The api_key is invalid</li></ul>|
| | | <ul><li>order_not_bound_same_user: The order is bounded by another user</li></ul>|
| | | <ul><li>order_not_exist: The order is not exist</li></ul>|
| | | <ul><li>order_is_timeout: The order is expired(order timeout 15 minutes)</li></ul>|
| | | <ul><li>illegal_form_input: The form format does not pass validation</li></ul>|
| validation | object (option) | if the error_name is 'illegal_form_input’, system should assign the name of wrong type for each error input |
| given_name | array (option) | required: <ol><li>The data is empty</li></ol> |
| family_name | array (option) | required: <ol><li>The data is empty</li></ol> |
| title | array (option) | required: <ol><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not a number</li></ol> |


