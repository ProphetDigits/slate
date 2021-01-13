# Voucher
## Voucher List

<details>
  <summary>Change Log</summary>
  <div class="summary-content">
  
  **2020.12.29 / CC**

  * Modify Return Failure Parameters
  
  **2020.12.17 / Jonas**

  * Add New API


</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/voucher/list` |
| Method | `post` |
| Use |To get the voucher list of company  |
| Notice | |


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
    "vouchers": [{
        "number": "IKEA0000000001VC",
        "currency": "JPY",
        "total": 24288,
        "item": {
            "id": 1,
            "name": "Array k1"
        },
        "variant": {
            "id": 1,
            "name": "Black"
        },
        "voucher_status": "Done",
        "payment_status": "Collecting",
        "created_at": 1459491797,
        "refund_at": null,
        "retailer": {
            "id": 1,
            "name": "Company A"
        },
        "agent": {
            "id": 1,
            "given_name": "QQ",
            "family_name": "Wang"
        },
        "consumer": {
            "given_name": "Andy", 
            "family_name": "Lee"
        }
    },{
       "number": "IKEA0000000002VC",
        "currency": "CHF",
        "total": 3000,
        "item": {
            "id": 1,
            "name": "Autark k1"
        },
        "variant": {
            "id": 1,
            "name": "White"
        },
        "voucher_status": "Done",
        "payment_status": "Refunded",
        "created_at": 1459491797,
        "refund_at": 1459498797,
        "retailer": {
            "id": 1,
            "name": "Company B"
        },
        "agent": {
            "id": 1,
            "given_name": "QQ",
            "family_name": "Wang"
        },
         "consumer": {
            "given_name": "CC",
            "family_name": "Lee"
        }
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| number | string | voucher number |
| currency | string | payment currency |
| total | double | voucher total price |
| item | object | The item of voucher |
| variant | object | The variant of voucher |
| voucher_status | string | The status of voucher |
| payment_status | string | The status of payment |
| created_at | timestamp | created time in the number of seconds |
| refund_at | timestamp/null | refunded time in the number of seconds |
| retailer | object | The retailer that sold the voucher |
| agent | object | sales agent |
| consumer | object | consumer who bought the voucher |


| item | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of item |
| name | string | The name of item |

| variant | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of variant |
| name | string | The name of variant |

| retailer | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of copmany |
| name | string | The name of copmany |

| agent | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of agent |
| given_name | string | The given_name of sales agent |
| family_name | string | The family_name of sales agent |

| consumer | Type | Description |
| -------: | :---- | :--- |
| given_name | string/null | The given_name of consumer |
| family_name | string/null | The family_name of consumer |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does_not_signin: the user does not signin</li><li>not_select_company_yet: user need change current company</li><li>company_not_exist: currenct company not exist</li><li>not_company_member: the user is not the company member</li></ul> |


## Create Voucher

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.12.02 / Lyon**

  * Add New Api

  **2020.12.14 / Lyon**

  * Modify discount_amount type

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/voucher/create` |
| Method | `post` |
| Use | To create voucher |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "variant_id": 1,
    "currency": "EUR",
    "discount_amount": 100,
    "billing_address": { 
      "given_name": "Andy", 
      "family_name": "Lee",
      "phone": "+886 912345678",
      "title": 1,
      "email": "abc@abc.com",
      "street": "ABC st.",
      "city": "Taichung",
      "state": "",
      "code": "30123",
      "country": "Taiwan"
    },
    "shipping_address": {
      "given_name": "Andy",
      "family_name": "Lee",
      "phone": "+886 912345678",
      "title": 1,
      "email": "abc@abc.com",
      "street": "ABC st.",
      "city": "Taichung",
      "state": "",
      "code": "30123",
      "country": "Taiwan"
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| variant_id | integer | The id of variant |
| currency | string | The currency name |
| discount_amount | float | product discount amount |
| billing_address | object (option) | billing address information |
| shipping_address | object (option) | shipping address information |


| billing_address | Type | Description |
| -------: | :---- | :--- |
| given_name | string (option) | recipient’s given_name |
| family_name | string (option) | recipient’s family_name |
| phone | string (option) | recipient’s phone number |
| title | integer (option) | recipient’s title (0=Mr. 1=Ms.) |
| email | string (option) | recipient’s email |
| street | string (option) | recipient’s address |
| city | string (option) | recipient’s address |
| state | string (option) | recipient’s address |
| code | string (option) | recipient’s address |
| country | string (option) | recipient’s address |

| shipping_address | Type | Description |
| -------: | :---- | :--- |
| given_name | string (option) | shipping_address's given_name |
| family_name | string (option) | shipping_address's family_name |
| phone | string (option) | shipping_address's phone number |
| title | integer (option) | shipping_address's title (0=Mr. 1=Ms.) |
| email | string (option) | shipping_address's email |
| street | string (option) | shipping_address's address |
| city | string (option) | shipping_address's address |
| state | string (option) | shipping_address's address |
| code | string (option) | shipping_address's address |
| country | string (option) | shipping_address's address |

> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"voucher":{
		"number": "IKEA0000000001VC"
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| voucher | object | Collection of voucher |

| voucher | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of voucher |


> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "illegal_form_input",
     "validation": {
        "variant_id": ["required"],
        "currency": ["required"],
        "discount_amount": ["required"],
        "billing_address": ["required"],
        "shipping_address": ["required"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>variant_not_exist: The variant2 is not exist or not belongs to target company</li><li>currency_not_exist: Product company delete the currency</li><li>invalid_discount: Discount amount should more than 0 and less than max discount which setting by product company</li><li>no_permission : Sales company is not a brand or a retailer</li><li>no_option : Sales company has no option with brand</li></ul> |
| validation | object (option) | If the error_name is 'illegal_form_input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| variant_id | integer | required: <ol><li>The field is required</li></ol>  |
| currency | string | required: <ol><li>The field is required</li></ol>  |
| discount_amount | numeric | required: <ol><li>The field is required</li></ol>  |
| billing_address | object | required: <ol><li>The field is required</li></ol>  |
| shipping_address | object | required: <ol><li>The field is required</li></ol>  |


## Voucher Detail

<details>
  <summary>Change Log</summary>
  <div class="summary-content">
  
  **2021.01.13 / CC**
  
  * Add Success Parameter
    * assigned_product
    * voucher.payment.history.transaction_id
  * Modify Title Of Success Parameter

  **2020.12.30 / CC**
  
  * Add Success Parameter
    * created_at

  **2020.12.29 / CC**
  
  * Add New Api

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/voucher/detail` |
| Method | `post` |
| Use | to get the voucher detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "number": "HORA001VC"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| number | string | voucher number |

> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "number": "HORA001VC",
    "brand": {
        "id": 107,
        "name": "HORAGE"
    },
    "retailer": {
        "id": 1,
        "name": "Company A"
    },
    "agent": {
            "id": 1,
            "given_name": "QQ",
            "family_name": "Wang"
    },
    "item": {
        "id": 131,
        "name": "AUTARK"
    },
    "variant": {
        "id": 169,
        "name": "White"
    },
    "created_at": 1519713617,
    "pre_sell_rule": "xxxxx",
    "assigned_product": "HORA001PD",
    "payment": {
        "status": "Collecting",
        "currency": "EUR",
        "price": 1000,
        "discount": 100,
        "total": 900,
        "paid": 500,
        "unpaid": 400,
        "histories": [{
            "id": 1,
            "type": "Paid",
            "created_at": 1519713617,
            "payment_method": "wxpay",
            "transaction_id": "xxxxx_001",            
            "amount": 100,
            "sales": {
                "id": 82,
                "given_name": "Billy",
                "family_name": "Yan",
                "company": {
                    "id": 107,
                    "name": "Company A"
                }
            }
        }]
    },
    "billing_address": {
        "title": 0,
        "given_name": "",
        "family_name": "",
        "phone": "",
        "email": "",
        "street": "",
        "city": "",
        "state": "",
        "code": "",
        "country": ""
    },
    "shipping_address": {
        "title": 0,
        "given_name": "",
        "family_name": "",
        "phone": "",
        "email": "",
        "street": "",
        "city": "",
        "state": "",
        "code": "",
        "country": ""
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| number | string | voucher number |
| brand | object | The brand of the voucher |
| retailer | object | The reatiler of the voucher |
| agent | object | The creator of the voucher |
| item | object | The item of the voucher |
| variant | object | The variant of the voucher |
| created_at | timestamp | created time in the number of seconds |
| pre_sell_rule | string | The pre sell rule of the voucher (copy from variant's  pre_sell.description) |
| assigned_product | string | The assigned product number |
| payment | object | The payment information of the voucher |
| billing_address | object | The billing address of the voucher |
| shipping_address | object | The shipping address of the voucher |

| voucher.brand | Type | Description |
| -------: | :---- | :--- |
| id | integer | The brand's company id |
| name | string | The brand's company name |

| voucher.retailer | Type | Description |
| -------: | :---- | :--- |
| id | integer | The retailer's company  id |
| name | string | The retailer's company name |

| voucher.agent | Type | Description |
| -------: | :---- | :--- |
| id | integer | user id |
| given_name | string | The sales agent’s given name |
| family_name | string | The sales agent’s family name |

| voucher.item | Type | Description |
| -------: | :---- | :--- |
| id | integer | The item id |
| name | string | The item name |

| voucher.variant | Type | Description |
| -------: | :---- | :--- |
| id | integer | The variant2 id |
| name | string | The variant2 name |

| voucher.payment | Type | Description |
| -------: | :---- | :--- |
| status | string | The current payment status of the voucher <ul><li>Collecting</li><li>Paid</li><li>Refund Requested</li><li>Refunded</li></ul> |
| currency | string | The currency name |
| price | double | The original price of the voucher (copy from variant's price) |
| discount | double | The discount amount of the voucher |
| total | double | The total amount of the voucher (price - discount) |
| paid | double | The total paid amount of the voucher |
| unpaid | double | The unpaid amount of the voucher (total - paid) |
| histories | array | The payment logs of the voucher |

| voucher.payment.history | Type | Description |
| -------: | :---- | :--- |
| id | integer | The history id |
| type | string | The history type <ul><li>Paid</li><li>Refunded</li></ul> |
| created_at | timestamp | created time in the number of seconds |
| payment_method | string | payment method <ul><li>cash</li><li>wxpay</li></ul> |
| transaction_id | string | The transaction_id returns "null" when payment_method is <ul><li>cash</li></ul> |
| amount | double | The paid amount of the payment |
| sales | object | The salesperson who handled the payment |

| voucher.payment.history.sales | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| given_name | string | The given name of the salesperson |
| family_name | string | The family name of the salesperson |
| company | object | The company of the salesperson |

| voucher.payment.history.sales.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The salesperson's company id |
| name | string | The salesperson's company name |

| voucher.billing_address | Type | Description |
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

| voucher.shipping_address | Type | Description |
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


> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"voucher_not_exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>no_option: The current company of user does not have option with  company of the voucher</li><li>does_not_signin: the user does not signin</li><li>not_select_company_yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not_company_member: the user is not the company member</li><li>voucher_not_exist: <ol><li>voucher number is invalid</li><li>currenct company is not salesperson's company</li></ol></li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| api_key | array (option) | <ul><li>required: api_key is required</li></ul> |
| number | array (option) | <ul><li>required: number is required</li></ul> |



## Voucher Payment

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.12.29 / CC**
  
  * Add New Api

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/voucher/payment` |
| Method | `post` |
| Use | to pay for the voucher, voucher supports multiple payment |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "number": "HORA001VC",
  "payment_method":"cash",
  "amount": 500
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| number | string | The voucher number |
| payment_method | string | The payment method <ul><li>cash</li><li>wxpay</li></ul>|
| amount | double | The payment amount |

> Return Success Parameters

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
  "error_name":"voucher_not_exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>no_option: The current company of user does not have option with  company of the voucher</li><li>does_not_signin: the user does not signin</li><li>not_select_company_yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not_company_member: the user is not the company member</li><li>voucher_not_exist: <ol><li>voucher number is invalid</li><li>currenct company is not salesperson's company</li></ol></li><li>exceed_unpaid_amount: The amount exceeds vocuher unpaid amount</li><li>refunded: The voucher has been refunded</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| api_key | array (option) | <ul><li>required: The api_key is required</li></ul> |
| number | array (option) | <ul><li>required: The number is required</li></ul> |
| amount | array (option) | <ul><li>required: The amount is required</li><li>invalid: The amount is invalid</li></ul> |
| payment_method | array (option) | <ul><li>required: The payment_method is required</li><li>invalid: The payment_method is invalid</li></ul> |
