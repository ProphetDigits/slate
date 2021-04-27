# Voucher
## Voucher List

<details>
  <summary>Change Log</summary>
  <div class="summary-content">
  
  **2021.04.13 / Jonas**

  * Add Return Success Parameters

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
        },
        "tags":[{
            "id": 1,
            "name":"tag1"
        },{
            "id": 2,
            "name": "tag2"
        }]
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
        },
        "tags":[{
            "id": 1,
            "name":"tag1"
        }]
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
| payment_status | string | The status of payment <ul><li>Collecting</li><li>Paid</li><li>Refund Requested</li><li>Refunded</li></ul>|
| created_at | timestamp | created time in the number of seconds |
| refund_at | timestamp/null | refunded time in the number of seconds |
| retailer | object | The retailer that sold the voucher |
| agent | object | sales agent |
| consumer | object | consumer who bought the voucher |
| tags | array | Collection of tag, order by Old to New (adding time) |


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

| tags | Type | Description |
| -------: | :---- | :--- |
| id | integer | The tag id |
| name | string | The tag name |

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



## Edit Voucher

<details>
  <summary>Change Log</summary>
  <div class="summary-content">
  
  **2021.04.27 / CC**

  * Add Input Parameters
    * added_files
    * deleted_files
    
  **2021.04.13 / Jonas**

  * Add Input Parameters
    * tags

  **2021.3.31 / Jonas**

  * Add Input Parameters
    * added_notes
    * deleted_notes
    * edited_notes

  * Add Success Parameter
    * same as Get voucher Detail
  * Modify Input Parameter
    * importer(required) =>importer(optional)
  * Add Failure Parameter
    * error_name
      * note_not_exist 

  * Modify Failure Parameter Description
    * error_name 
      * no_permission
        * Only brand member can edit voucher => The permission deny

  **2021.3.22 / Lynn**

  * remove send_invoice parameters
  
 **2021.03.11 / Jonas**

  * Add Input Parameters
    * importer
    * send_invoice

  **2021.01.13 / CC**

  * Add New API

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/voucher/edit` |
| Method | `post` |
| Use | To edit the voucher  |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "number": "HORA001VC",
  "assign_product": "HORA001PD",
  "importer": {
    "name": "scott",
    "website":"www.xxxx.com",
    "phone":"0912345678",
    "email":"xxx@xxx.com",
    "address":""
  },
  "added_notes": ["note 1", "note 2"],
  "deleted_notes": [1, 2, 3],
  "edited_notes": [{
    "id":1,
    "content":"modify note"
  }],
  "tags":["tag1","tag2"],
  "added_files": [{
      "name": "broken.jpg",
      "date": 1498730137,
      "comment": "the product was broken",
      "resource": ""
  }],
  "deleted_files": [1, 2, 3]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| number | string | The voucher number |
| assign_product | string (option) | The product number which is going to assign <ul><li>Without assign_product param, backend will do nothing</li><li>When assign_product is empty string "", backend will unassign current assigned product</li><li>When assign_product is "HORA001PD", backend will unassign the old one and assign the new product HORA001PD</li></ul> |
| importer | object(option) | The importer of voucher |
| added_notes | array (option) | Collection of note content<br/> It is order by adding time from new to old |
| deleted_notes | array (option) | Collection of note id <br/>Only company member can edit |
| edited_notes | array (option) | Collection of edited notes <br/>Users can only edit notes added by the same user account |
| tags | array (option) | Collection of tag name <br/>Only company member can edit |
| added_files | array (option) | Collection of uploading files |
| deleted_files | array (option) | Collection of file id |


| importer | Type | Description |
| -------: | :---- | :--- |
| name | string | The importer name |
| website | string | The importer website  |
| phone | string | The importer phone |
| email | string | The importer email |
| address | string | The importer address |

| edited_notes | Type | Description |
| -------: | :---- | :--- |
| id | integer | The note id |
| content | string | The note content |

| added_files | Type | Description |
| -------: | :---- | :--- |
| name | string | The filename |
| date | timestamp | The uploading date |
| comment | string | The comment |
| resource | string | The file encrypted by base64, but exclude mime type |

> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>
The result is the same as [Get Voucher Detail](#voucher-detail)

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
  "error_name": "product_sold"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>no_option: The current company of user does not have option with  company of the voucher</li><li>does_not_signin: the user does not signin</li><li>not_select_company_yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not_company_member: the user is not the company member</li><li>voucher_not_exist: <ol><li>voucher number is invalid</li><li>currenct company is not salesperson's company</li></ol></li><li>product_sold: The assigned product has been sold</li><li>invalid_product: The assigned product doesn't belong to voucher's variant</li><li>no_permission: The permission deny</li><li>illegal_form_input: The form format does not pass validation</li><li>note_not_exist:The note does not exist anymore</li></ul> |
| validation | object (option) | if the error_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| api_key | array (option) | <ul><li>required: api_key is required</li></ul> |
| number | array (option) | <ul><li>required: number is required</li></ul> |
| importer | array (option) | <ul><li>required: importer is required</li></ul> |
| added_notes | array (option) | invalid: <ol><li>The data should be array</li></ol> |
| added_notes.(index) | string (option) | invalid: <ol><li>The data is not string</li></ol> |
| added_files | array (option) | invalid: <ol><li>The data should be array</li></ol> |
| added_files.(index).name | array (option) | required: <ol><li>The field is required</li></ol> |
| added_files.(index).date | array (option) | required: <ol><li>The field is required</li></ol> |
| added_files.(index).comment | array (option) | required: <ol><li>The field is required</li></ol> |
| added_files.(index).resource | array (option) | required: <ol><li>The field is required</li></ol> |
| deleted_files | array (option) | invalid: <ol><li>The data should be array</li></ol> |

## Voucher Detail

<details>
  <summary>Change Log</summary>
  <div class="summary-content">
  
  **2021.04.27 / CC**

   * Add Success Parameter
       * files
       
 **2021.04.13 / Jonas**

  * Add Success Parameter
      * tags

  **2021.03.31 / Jonas**

  * Add Success Parameter
      * notes

  **2021.03.17 / Jonas**

  * Modify Success Parameter
      * invoice
        * sent(parameter type change to string)

  **2021.03.11 / Jonas**

  * Add Success Parameter
      * importer

  **2021.02.18 / Jonas**
  
  * Modify Success Parameter
    * payment => add refund, request_refund_reason Parameter
    * payment.histories => add Refunded, Refund Declined, Refund Requested
    * payment.histories => sales change to operator
  * Add Success Parameter
    * invoices

  **2021.01.13 / CC**
  
  * Add Success Parameter
    * assigned_product
    * voucher.payment.histories.transaction_id
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
    "importer": {
        "name": "scott",
        "website":"www.xxxx.com",
        "phone":"0912345678",
        "email":"xxx@xxx.com",
        "address":""
    },
    "invoices": [{
      "type": "receipt",
      "number": "AAAA170329000006RC",
      "created_at": 1490776038,
      "download": "http://..../voucher/AAAAVC/invoice/AAAARC/download",
      "sent" : "success"
    },{
      "type": "invoice", 
      "number": "AAAA170329000006IN",
      "created_at": 1490776038,
      "download": "http://..../voucher/AAAAVC/invoice/AAAARC/download",
      "sent" : "failed"
    },{
      "type": "invoice", 
      "number": "AAAA170329000007IN",
      "created_at": 1490776100,
      "download": "http://..../voucher/AAAAVC/invoice/AAAARC/download",
      "sent" : "pending"
    }],
    "payment": {
        "status": "Collecting",
        "request_refund_reason": "The watch is broken",
        "currency": "EUR",
        "price": 1000,
        "discount": 100,
        "total": 900,
        "paid": 500,
        "unpaid": 400,
        "refund": 2000,
        "histories": [{
            "id": 1,
            "type": "Paid",
            "created_at": 1519713617,
            "payment_method": "wxpay",
            "transaction_id": "xxxxx_001",            
            "amount": 100,
            "operator": {
                "id": 82,
                "given_name": "Billy",
                "family_name": "Yan",
                "company": {
                    "id": 107,
                    "name": "Company A"
                }
            }
        },{
          "id": 2,
          "type": "Refunded",
          "created_at": 1519713617,
          "payment_method": null,      
          "transaction_id": null,              
          "amount": 100,
          "comment": "The watch is broken",
          "operator": {
            "id": 82,
            "given_name": "Billy",
            "family_name": "Yan",
            "company": {
              "id": 107,
              "name": "Company A"
            }
          }
        },{
          "id": 3,
          "type": "Declined",
          "created_at": 1519713617,
          "payment_method": null,      
          "transaction_id": null,              
          "amount": null,
          "comment": "The watch is broken",
          "operator": {
            "id": 82,
            "given_name": "Billy",
            "family_name": "Yan",
            "company": {
              "id": 107,
              "name": "Company A"
            }
          }
        },{
          "id": 3,
          "type": "Refund Requested",
          "created_at": 1519713617,
          "payment_method": null,      
          "transaction_id": null,              
          "amount": null,
          "comment": "The watch is broken",
          "operator": {
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
    },
    "notes": [{
        "id": 1,
        "content": "something wrong",
        "operator": {
            "id": 1,
            "given_name": "Jianhua",
            "family_name": "Wang",
            "company": {
                "id": 1,
                "name": "Prophet Digits"
            }
        },
        "created_at": 1517542365
    }],
    "tags":[{
      "id": 1,
      "name":"tag1"
    },{
      "id": 2,
      "name":"tag2"
    }],
    "files": [{
        "id": 79,
        "name": "test.jpg",
        "date": 1517542365,
        "comment": "",
        "uploader": {
            "id": 82,
            "given_name": "Simon",
            "family_name": "Chang",
            "company": {
                "id": 107,
                "name": "ABC Company"
            }
        },
        "link": "https://.../voucher/{voucher_number}/file/{file_id}"
    }]
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
| importer | object | The importer of voucher |
| payment | object | The payment information of the voucher |
| invoices | array | The invoice of voucher <br/>It’s order by created time from new to old |
| billing_address | object | The billing address of the voucher |
| shipping_address | object | The shipping address of the voucher |
| notes | array | Collection of note<br/>It's order by created time from new to old |
| tags | array | Collection of tag, order by Old to New (adding time) |
| files | array | Collection of file.<br/>Sort by date from new to old |

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

| voucher.invoices | Type | Description |
| -------: | :---- | :--- |
| type | string | The invoice type <ul><li>invoices</li><li>receipt</li></ul> |
| number | string | The invoice number |
| created_at | string | created time in the number of seconds  |
| download | string |The url of invoice or recipt for download, visit the url need to add header Authorization and value is api_key |
| sent | string |The invoice eamil sent status<ul><li>success</li><li>failed</li><li>pending</li></ul> |


| voucher.importer | Type | Description |
| -------: | :---- | :--- |
| name | string | The importer name |
| website | string | The importer website  |
| phone | string | The importer phone |
| email | string | The importer email |
| address | string | The importer address |

| voucher.payment | Type | Description |
| -------: | :---- | :--- |
| status | string | The current payment status of the voucher <ul><li>Collecting</li><li>Paid</li><li>Refund Requested</li><li>Refunded</li></ul> |
| currency | string | The currency name |
| request_refund_reason | string | The request refund reason(if voucher not request refund,should be null) |
| price | double | The original price of the voucher (copy from variant's price) |
| discount | double | The discount amount of the voucher |
| total | double | The total amount of the voucher (price - discount) |
| paid | double | The total paid amount of the voucher |
| unpaid | double | The unpaid amount of the voucher (total - paid) |
| refund | double | The refund amount of the voucher (if voucher not refunded,should be 0) |
| histories | array | The payment logs of the voucher<br/>It’s order by created time from new to old |

| voucher.payment.histories | Type | Description |
| -------: | :---- | :--- |
| id | integer | The history id |
| type | string | The history type <ul><li>Paid</li><li>Refunded</li><li>Refund Declined</li><li>Refund Requested</li></ul> |
| created_at | timestamp | created time in the number of seconds |
| payment_method | string | payment method <ul><li>cash</li><li>wxpay</li></ul></br>payment method returns "null" when type is <ul><li>Refunded</li><li>Refund Declined</li><li>Refund Requested</li></ul>|
| transaction_id | string | The transaction_id returns "null" when payment_method is <ul><li>cash</li></ul>Or when type is <ul><li>Refunded</li><li>Refund Declined</li><li>Refund Requested</li></ul>|
| amount | double | The paid amount of the payment.</br>amount returns "null" when type is <ul><li>Refund Declined</li><li>Refund Requested</li></ul>|
| comment | string | The history comment </br>comment returns "null" when type is <ul><li>Paid</li></ul>|
| operator | object | The operator who handled the payment |

| voucher.payment.histories.operator | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| given_name | string | The given name of the salesperson |
| family_name | string | The family name of the salesperson |
| company | object | The company of the salesperson |

| voucher.histories.operator.company | Type | Description |
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

| product.note | Type | Description |
| -------: | :---- | :--- |
| id | integer | The note id |
| content | string | The note content |
| operator | object | The operator |
| created_at | timestamp | The created time in seconds |

| product.note.operator | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| given_name | string | The given name of user |
| family_name | string | The family name of user |
| company | object | The company of operator |

| product.note.operator.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

| tags | Type | Description |
| -------: | :---- | :--- |
| id | integer | The tag id |
| name | string | The tag name |

| voucher.file | Type | Description |
| -------: | :---- | :--- |
| id | integer | The file id |
| name | string | The file name |
| date | timestamp | The uploaded date |
| comment | string | The uploaded comment |
| uploader | object | The user who uploading file |
| link | string | The download link of file, and it need add api_key to Authorization header in the request |

| voucher.file.uploader | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| given_name | string | The given name of user |
| family_name | string | The family name of user |
| company | object | The company of uploader |

| voucher.file.uploader.company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

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
| validation | object (option) | if the error_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| api_key | array (option) | <ul><li>required: api_key is required</li></ul> |
| number | array (option) | <ul><li>required: number is required</li></ul> |



## Voucher Payment

<details>
  <summary>Change Log</summary>
  <div class="summary-content">
  
  **2021.01.13 / CC**
  
  * Add Success Parameter
    * qrcode
    * transaction_id

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
  "payment_method":"wxpay",
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

```json
{
  "qrcode":"xxxxxx",
  "transaction_id": "zzzzzz"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| qrcode | string (option) | The product2 qrcode encoded by base64. The qrcode is reqired when payment_method is:<ul><li>wxpay</li></ul> |
| transaction_id | string (option) | The transaction id is reqired when payment_method is:<ul><li>wxpay</li></ul>|

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
| validation | object (option) | if the error_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| api_key | array (option) | <ul><li>required: The api_key is required</li></ul> |
| number | array (option) | <ul><li>required: The number is required</li></ul> |
| amount | array (option) | <ul><li>required: The amount is required</li><li>invalid: The amount is invalid</li></ul> |
| payment_method | array (option) | <ul><li>required: The payment_method is required</li><li>invalid: The payment_method is invalid</li></ul> |



## Voucher Transaction Result

<details>
  <summary>Change Log</summary>
  <div class="summary-content">
  
  **2021.01.20 / CC**
  
  * Remove case from fail.reason
  * Modify description of failure case "transaction_not_exist"
  * Modify json example of failure
  
  **2021.01.13 / CC**
  
  * Add New Api

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/voucher/transaction/result` |
| Method | `post` |
| Use | To get the transaction result, e.g. keep polling the wechat pay result |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "id": "xxxxx001"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| id | string | The transaction id |

> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json

{
  "status": "open"
}

{
  "status": "success"
}

{
  "status": "fail",
  "fail": {
    "reason": "xxx"
  }
}

```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| status | string | The transaction status.<ul><li>open: The transaction is still allowed to pay</li><li>success: The transaction result is successful and closed</li><li>fail: The transaction result is fail and closed</li></ul> |
| fail | object (option) | The "fail" object is reqired when status is fail.|

| fail | Type | Description |
| -------: | :---- | :--- |
| reason | string | The fail reason.<ul><li>Some errors from wxpay</li></ul> |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"transaction_not_exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>no_option: The current company of user does not have option with  company of the voucher</li><li>does_not_signin: the user does not signin</li><li>not_select_company_yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not_company_member: the user is not the company member</li><li>transaction_not_exist: The transaction id doesn't exist in system.<br>System will also remove transaction_id when the transaction is timeout</li></ul>|
| validation | object (option) | if the error_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| api_key | array (option) | <ul><li>required: The api_key is required</li></ul> |
| id | array (option) | <ul><li>required: The id is required</li></ul> |


## Refund Request

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2021.02.18 / Jonas**
  
  * Add New Api

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/voucher/refund/request` |
| Method | `post` |
| Use | to request refund voucher |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "number": "HORA001VC",
  "comment": "The watch is broken"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| number | string | The voucher number |
| comment | string (option) | The request refund reason |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>no_option: The current company of user does not have option with  company of the voucher</li><li>does_not_signin: the user does not signin</li><li>not_select_company_yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not_company_member: the user is not the company member</li><li>voucher_not_exist: <ol><li>voucher number is invalid</li><li>currenct company is not salesperson's company</li></ol></li><li>no_permission: only brand member can refund voucher</li><li>repeat: the request refund is repeated</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| api_key | array (option) | <ul><li>required: The api_key is required</li></ul> |
| number | array (option) | <ul><li>required: The number is required</li></ul> |

## Refund

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2021.02.18 / Jonas**
  
  * Add New Api

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/voucher/refund/confirm` |
| Method | `post` |
| Use | to refund voucher |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "number": "HORA001VC",
  "amount": 2000,
  "comment": "The watch is broken"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| number | string | The voucher number |
| amount | double | The refund total amount   |
| comment | string (option) | The comment of refund |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>no_option: The current company of user does not have option with  company of the voucher</li><li>does_not_signin: the user does not signin</li><li>not_select_company_yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not_company_member: the user is not the company member</li><li>voucher_not_exist: <ol><li>voucher number is invalid</li><li>currenct company is not salesperson's company</li></ol></li><li>no_permission: only brand member can refund voucher</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| api_key | array (option) | <ul><li>required: The api_key is required</li></ul> |
| number | array (option) | <ul><li>required: The number is required</li></ul> |
| amount | array (option) | <ul><li>required: The amount is required</li></ul> |


## Decline Refund


<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2021.02.18 / Jonas**
  
  * Add New Api

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/voucher/refund/decline` |
| Method | `post` |
| Use | to decline request refund voucher |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "number": "HORA001VC",
  "comment": "The watch is fine"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| number | string | The voucher number |
| comment | string(option) | The decline request refund reason |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>no_option: The current company of user does not have option with  company of the voucher</li><li>does_not_signin: the user does not signin</li><li>not_select_company_yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not_company_member: the user is not the company member</li><li>voucher_not_exist: <ol><li>voucher number is invalid</li><li>currenct company is not salesperson's company</li></ol></li><li>no_permission: only brand member can refund voucher</li><li>not_found_request: The request refund is not found request</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| validation | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| api_key | array (option) | <ul><li>required: The api_key is required</li></ul> |
| number | array (option) | <ul><li>required: The number is required</li></ul> |

## Send Voucher Email

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2021.3.22 / Lynn**

  * Add New API

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/voucher/email/send` |
| Method | `post` |
| Use | To send the email |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "number": "HORA001VC",
  "type": "invoice"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| number | string | The voucher number |
| type | string | The email type |

> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
  "error_name": "invalid_payment_status"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>no_option: The current company of user does not have option with  company of the voucher</li><li>does_not_signin: the user does not signin</li><li>not_select_company_yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not_company_member: the user is not the company member</li><li>voucher_not_exist: <ol><li>voucher number is invalid</li><li>currenct company is not salesperson's company</li></ol></li><li>no_permission: Only brand member can send voucher email</li><li>product_not_assign: When send invoice, assigned product should exist</li><li>invalid_payment_status: When send invoice, payment status should be "Paid"</li></ul> |
| validation | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| api_key | array (option) | <ul><li>required: The api_key is required</li></ul> |
| number | array (option) | <ul><li>required: The number is required</li></ul> |
| type | array (option) | <ul><li>required: The type is required</li></ul> |


## Download Voucher File

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2021.04.27 / CC**

  * Add New API

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | The link comes from the API Voucher Detail (file.link) |
| Method | `get` |
| Use | Download voucher file |
| Notice | |


### Headers Parameters

| Headers | Type | Description |
| -------: | :---- | :--- |
| Authorization | string | The identity token of user |

<aside class="success">
Success
</aside>

| Headers | Type | Description |
| -------: | :---- | :--- |
| Content-Type | string | The Mime type of file |
| Content-Disposition | string | <ul><li>inline: file is pdf</li><li>attachment: type not pdf</li></ul> |

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>no_authorization: The Authorization is invalid</li><li>no_permission: The user has no permission to download file</li><li>voucher_not_exist: The voucher is not exist</li><li>file_not_found: The file is not exist</li></ul> |
