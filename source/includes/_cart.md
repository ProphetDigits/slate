# Cart

## Cart List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/cart/list` |
| Method | `post` |
| Use | Get all user’s shopping carts |
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
  "carts": [{
    "id": "1",
    "currency": "EUR"
    }, {
    "id": "2",
    "currency": "TWD"
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **carts** | array |  |
| id | integer |  cart’s  id |
| currency | string | the cart use this currency to pay |

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


## Create a Cart

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
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |

> Return Parameters

### Return Parameters

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
|||**no permission:**|


## Add Product To Cart

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
  "products": ["UX76K3NB9"],
  "currency": "EUR"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| cart_id | integer | cart’s id |
| product_number | array | product number (from scan QR-Code or user keyin |
| currency | string| product be paid by this currency|

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
| (Nothing return) | |  |

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
|||**no permission:**
|||**cart not exist:** cart id error |
|||**currency error:** currency not same to cart |
|||**product in cart:** product in cart now |
|||**product not exist:** product number error |
|||**product sold:** product has been sold |
|||**no product permission:** not product owner company or no option with product company |
|||**currency not exist:** product cannot |
|||**sale region not found:** VAT region not set |
|||**importer region error:** importer not in VAT region |


## Give Discount

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
  "product_number": "BION000001",
  "discount_amount": 1.01,
  "cart_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| cart_id | integer | cart’s id |
| **product_number** | **array** | product number (from scan QR-Code or user keyin) |
| *discount_amount* | double | product discount amount |

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
| (Nothing return) | | |

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
|||**no permission:**|
|||**cart not exist:** cart id error |
|||**currency error:** currency not same to cart |
|||**product in cart:** product in cart now |
|||**product not exist:** product number error |
|||**product sold:** product has been sold |
|||**no product permission:** not product owner company or no option with product company |
|||**currency not exist:** product cannot |


## Delete Products From Cart

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
  "products": ["UX76K3NB9"]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| cart_id | integer | cart’s id |
| products | string | a set of product’s number (from scan QR-Code or user keyin) |

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
| (Nothing return) | | |

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
|||**no permission:**|
|||**cart not exist:** cart id error |


## Cart Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/cart/detail` |
| Method | `post` |
| Use | to show product list in cart |
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
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| cart_id | integer | cart’s id |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "id":"C000001",
  "company": {
    "id": 1,
    "name": "Company Test"
  },
  "billing_address": {
    "given_name": null,
    "family_name": null,
    "phone": null,
    "title": null,
    "email": null,
    "street": null,
    "city": null,
    "state": null,
    "code": null,
    "country": null
  },
  "shipping_address": {
    "given_name": null,
    "family_name": null,
    "phone": null,
    "title": null,
    "email": null,
    "street": null,
    "city": null,
    "state": null,
    "code": null,
    "country": null
  },
  "price": {
    "subtotal": 200,
    "total_discount": 60,
    "shipping": 0,
    "total": 140
  },
  "products":[{
    "number":"A00001",
    "discount_amount": 0
    }, {
    "number":"A00002",
    "discount_amount": 0
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | number | cart id |
| **company** | **object** | cart belongs to which company |
| *id* | integer | company id |
| *name* | string | company name |
| **products** | **array** | products in the cart |
| *product_number* | string | product number |
| *discount_amount* | integer | product discount amount |
| company_id | integer | compay id |
| **price** | **object** | |
| *subtotal* | number | total product original price |
| *total_discount* | number | sum of all product discount in the cart |
| *shipping* | number | cart shipping price |
| *total* | number | cart total price (orignal total price - discount + shipping) |
| **billing_address** | **object** | billing address information |
| *given_name* | string | recipient’s given_name |
| *family_name* | string | recipient’s family_name |
| *phone* | string | recipient’s phone number |
| *title* | integer | recipient’s title (0=Mr. 1=Ms.) |
| *email* | string | recipient’s email |
| *street* | string | recipient’s address |
| *city* | string | recipient’s address |
| *state* | string | recipient’s address |
| *code* | string | recipient’s address |
| *country* | string | recipient’s address |
| **shipping_address** | *object* | shipping address information |
| **same to billing_address** ||

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
|||**cart not exist:** cart id error |


## Edit Cart Detail

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
  "cart_id":"C00001",
  "billing_address": {
  "given_name":"Lee",
  "family_name":"CC",
  "phone":"0912345678",
  "title":"Ms.",
  "email":"cc@abc.com",
  "street":"ABC st.",
  "city":"Taichung",
  "state":"Taiwan",
  "code":"30123",
  "country":"R.O.C."
  },
  "shipping_address": {
  "given_name":"Lee",
  "family_name":"CC",
  "phone":"0912345678",
  "title":"Ms.",
  "email":"cc@abc.com",
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
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| cart_id | integer | cart’s id |
| **billing_address** | **object** | billing address information |
| *given_name* | string | recipient’s given_name |
| *family_name* | string | recipient’s family_name |
| *phone* | string | recipient’s phone number |
| *title* | integer | recipient’s title (0=Mr. 1=Ms.) |
| *email* | string | recipient’s email |
| *street* | string | recipient’s address |
| *city* | string | recipient’s address |
| *state* | string | recipient’s address |
| *code* | string | recipient’s address |
| *country* | string | recipient’s address |
| **shipping_address** | *object* | shipping address information |
| **same to billing_address** ||

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
| (Nothing return) | | |

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
|||**cart not exist:** cart id error |
