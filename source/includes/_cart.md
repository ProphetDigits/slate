# Cart

## Cart List

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.12.31 / Jianhua**

  * Modify Input Parameters:
    * api_key: modify description
  * Modify Failure Parameters:
    * Apply new structure

  **2019.12.30 / CC**

  * Modify Success Parameter:
    * Apply new structure
    * currency: modify description
    * cart.id: modify example

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/cart/list` |
| Method | `post` |
| Use | Get user’s all shopping carts |
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

### Return Parameters

> Return Success Parameters

<aside class="success">
Success
</aside>

```json
{
  "carts": [{
    "id": 1,
    "currency": "EUR"
    }, {
    "id": 2,
    "currency": "TWD"
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| carts | array | Collection of cart |

| cart | Type | Description |
| -------: | :---- | :--- |
| id | integer |  cart’s  id |
| currency | string | User will pay for products in cart by this currency |

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



## Create a Cart

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.12.31 / Jianhua**

  * Modify Input Parameters:
    * api_key: modify description
  * Modify Failure Parameters:
    * Apply new structure

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/cart/create` |
| Method | `post` |
| Use | Create a new cart |
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


### Return Parameters

> Return Success Parameters

<aside class="success">
Success
</aside>

```json
{
  "cart_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| cart_id | integer | cart’s id |

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



## Add Product To Cart

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.1.2 / Jianhua**

  * Modify Input Parameter:
    * Modify "api_key" description
    * Modify "product_number" description
  * Modify Failure Parameter:
    * Apply new structure
    * Remove "cart_is_lock" in error_name

  **2019.12.30 / CC**

  * Modify Input Parameter:
    * Modify "currency" description
  * Modify Success Parameter:
    * Apply new structure

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/cart/product/add` |
| Method | `post` |
| Use | Add products to cart |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "cart_id": 1,
  "product_number": "UX76K3NB9",
  "currency": "EUR"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| cart_id | integer | cart’s id |
| product_number | string | product2 number |
| currency | string | Products will be paid by this currency. If the cart has never set currecy yet, you can assign currency to this cart. If the cart has set currency, you should always use this currency type to add products to this cart |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>cart not exist: cart id is invalid</li><li>currency error: currency not same to cart's currency</li><li>product in cart: product is added to cart</li><li>product not exist: <ol><li>product is not exist</li><li>item of product is deleted</li></ol></li><li>product sold: product is sold</li><li>sale region not found: VAT is not setted in company of product</li><li>importer region error: sales company is not importer in VAT country</li><li>no product permission: sales company has not option with product company</li><li>currency not exist: product company delete the currency</li></ul> |



## Give Discount

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.1.2 / Jianhua**

  * Modify Input Parameter:
    * Modify "api_key" description
  * Modify Failure Parameter:
    * Apply new structure
    * Add error_name:
      * "product currency not exist"
      * "invalid discount"
    * Remove error_name:
      * "currency error"
      * "product in cart"
      * "product sold"
      * "no product permission"
      * "currency not exist"
      * "cart_is_lock"

  **2019.12.30 / CC**

  * Modify Input Parameter:
    * product_number: modify description
    * product_number: modify example value
  * Modify Success Parameter:
    * Apply new structure

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/cart/product/discount/edit` |
| Method | `post` |
| Use | give product discount amount |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "product_number": "HORA001PD",
  "discount_amount": 1.01,
  "cart_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| cart_id | integer | cart’s id |
| product_number | string | The product number in cart |
| discount_amount | double | product discount amount |


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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>cart not exist: cart id is invalid</li><li>product not exist: <ol><li>product is not exist</li><li>item of product is deleted</li></ol></li><li>product currency not exist: product company delete the currency</li><li>invalid discount: discount amount should more than 0 and less than max discount which setting by product company</li></ul> |



## Delete Products From Cart

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.1.2 / Jianhua**

  * Modify Input Parameter:
    * Modify "api_key" description
  * Modify Failure Parameter:
    * Apply new structure
    * Remove error_name:
      * "cart_is_lock"

  **2019.12.30 / CC**

  * Modify Input Parameter:
    * products: modify description
    * products: modify example value
  * Modify Success Parameter:
    * Apply new structure

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/cart/product/delete` |
| Method | `post` |
| Use | remove products from cart |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "cart_id": 1,
  "products": ["HORA001PD", "HORA002PD"]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| cart_id | integer | cart’s id |
| products | array | a set of product’s number |


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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>cart not exist: cart id is invalid</li></ul> |



## Cart Detail

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.1.2 / Jianhua**

  * Modify Input Parameter:
    * Modify "api_key" description
  * Modify Success Parameter:
    * id: modify type
    * subtotal: modify type
    * total_discount: modify type
    * shipping: modify type
    * total: modify type
  * Modify Failure Parameter:
    * Apply new structure

  **2019.12.30 / CC**

  * Modify Use Decription
  * Modify Success Parameter:
    * Apply new structure
    * billing_address: modify example value
    * shipping_address: modify example value
    * products: modify example value
    * products: modify description
    * product.company_id: modify description
    * product.number: modify parameter name
    * price: add description
    * price.subtotal: modify description
    * price.shipping: modify description

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/cart/detail` |
| Method | `post` |
| Use | to show product list, billing/shipping address in cart |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "cart_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| cart_id | integer | cart’s id |


### Return Parameters

> Return Success Parameters

<aside class="success">
Success
</aside>

```json
{
  "id": 1,
  "company": {
    "id": 1,
    "name": "Company Test"
  },
  "billing_address": {
    "given_name": "",
    "family_name": "",
    "phone": "",
    "title": 0,
    "email": "",
    "street": "",
    "city": "",
    "state": "",
    "code": "",
    "country": ""
  },
  "shipping_address": {
    "given_name": "",
    "family_name": "",
    "phone": "",
    "title": 0,
    "email": "",
    "street": "",
    "city": "",
    "state": "",
    "code": "",
    "country": ""
  },
  "price": {
    "subtotal": 200,
    "total_discount": 60,
    "shipping": 0,
    "total": 140
  },
  "products":[{
    "number": "HORA001PD",
    "discount_amount": 10
    }, {
    "number": "HORA002PD",
    "discount_amount": 0
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | cart id |
| company | object | cart belongs to which company |
| products | array | Collection of product |
| price | object | Cart's price detail |
| billing_address | object | billing address information |
| shipping_address | object | shipping address information |

| company | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id |
| name | string | company name |

| product | Type | Description |
| -------: | :---- | :--- |
| number | string | product number |
| discount_amount | integer | product discount amount |
| company_id | integer | brand's compay id |

| price | Type | Description |
| -------: | :---- | :--- |
| subtotal | numeric | sum of all products' original price |
| total_discount | numeric | sum of all discount amount in the cart |
| shipping | numeric | cart shipping fee |
| total | numeric | cart total price (orignal total price - discount + shipping) |

| billing_address | Type | Description |
| -------: | :---- | :--- |
| given_name | string | recipient’s given_name |
| family_name | string | recipient’s family_name |
| phone | string | recipient’s phone number |
| title | integer | recipient’s title (0=Mr. 1=Ms.) |
| email | string | recipient’s email |
| street | string | recipient’s address |
| city | string | recipient’s address |
| state | string | recipient’s address |
| code | string | recipient’s address |
| country | string | recipient’s address |

| shipping_address | Type | Description |
| -------: | :---- | :--- |
| given_name | string | recipient’s given_name |
| family_name | string | recipient’s family_name |
| phone | string | recipient’s phone number |
| title | integer | recipient’s title (0=Mr. 1=Ms.) |
| email | string | recipient’s email |
| street | string | recipient’s address |
| city | string | recipient’s address |
| state | string | recipient’s address |
| code | string | recipient’s address |
| country | string | recipient’s address |


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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>cart not exist: cart id is invalid</li></ul> |



## Edit Cart Detail

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2019.1.2 / Jianhua**

  * Modify Input Parameter:
    * Modify "api_key" description
  * Modify Failure Parameter:
    * Apply new structure
    * Remove error_name:
      * "cart_is_lock"

  **2019.12.30 / CC**

  * Modify Input Parameter:
    * Apply new structure
    * cart_id: modify example
    * billing_address: modify example
    * shipping_address: modify example
  * Modify Success Parameter:
    * Apply new structure

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/cart/edit` |
| Method | `post` |
| Use | to edit invoice recipient |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "cart_id": 1,
  "billing_address": {
    "given_name": "Lee",
    "family_name": "CC",
    "phone": "+886 912345678",
    "title": 1,
    "email": "cc@abc.com",
    "street": "ABC st.",
    "city": "Taichung",
    "state": "",
    "code": "30123",
    "country": "Taiwan"
  },
  "shipping_address": {
    "given_name": "Lee",
    "family_name": "CC",
    "phone": "+886 912345678",
    "title": 1,
    "email": "cc@abc.com",
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
| cart_id | integer | cart’s id |
| billing_address | object | billing address information |
| shipping_address | object | shipping address information |

| billing_address | Type | Description |
| -------: | :---- | :--- |
| given_name | string | recipient’s given_name |
| family_name | string | recipient’s family_name |
| phone | string | recipient’s phone number |
| title | integer | recipient’s title (0=Mr. 1=Ms.) |
| email | string | recipient’s email |
| street | string | recipient’s address |
| city | string | recipient’s address |
| state | string | recipient’s address |
| code | string | recipient’s address |
| country | string | recipient’s address |

| shipping_address | Type | Description |
| -------: | :---- | :--- |
| given_name | string | recipient’s given_name |
| family_name | string | recipient’s family_name |
| phone | string | recipient’s phone number |
| title | integer | recipient’s title (0=Mr. 1=Ms.) |
| email | string | recipient’s email |
| street | string | recipient’s address |
| city | string | recipient’s address |
| state | string | recipient’s address |
| code | string | recipient’s address |
| country | string | recipient’s address |


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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: user need change current company</li><li>company not exist: currenct company not exist</li><li>not company member: the user is not the company member</li><li>cart not exist: cart id is invalid</li></ul> |
