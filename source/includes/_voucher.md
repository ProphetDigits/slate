# Voucher
## Voucher List

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li></ul> |


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
