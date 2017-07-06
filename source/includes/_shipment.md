# Shipment

## Shipment List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/shipment/list` |
| Method | `post` |
| Use | show shipment list |
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
    "shipments_of_brand": [{
		"number": "AAAA0000000001SH",
		"status": "Preparing",
		"shipped_at": 1498730137,
		"comment": "",
		"shipped_area": {
			"id": 1,
			"name": "Aruba"
		},
		"company": {
			"id": 1,
			"name": "Bike"
		},
		"importer": {
			"id": 1,
			"name": "Bike"
		},
		"recipient": {
			"given_name": "Abc",
			"family_name": "Hi"
		}
	}],
	"shipments_of_importer": []
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **shipments_of_brand** | **array** | the shipment is created by self |
| number | string | shipment latest status |
| status | string | shipment latest status |
| shipped_at | timestamp | shipped date |
| comment | string | shipment comment |
| **shipped_area** | **object** | country of shipped area |
| *id* | integer | country id |
| *name* | name | country name |
| **company** | **object** | shipment creator |
| *id* | integer | company id |
| *name* | name | company name |
| **importer** | **object** | company of importer |
| *id* | integer | company id of importer |
| *name* | name | company name of importer |
| **recipient** | **object** | recipient information |
| *given_name* | string | recipient given name |
| *family_name* | string | recipient family name |
| **shipments_of_importer** | **array** | the shipment is assigned to self |

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
|||**does not signin:** user does not signin|


## Shipment Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/shipment/detail` |
| Method | `post` |
| Use | show shipment detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "shipment_number": "AAAA0000000001SH"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| shipment_number | string | shipment number. |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"number": "AAAA0000000001SH",
	"status": "Preparing",
	"proforma_invoice_number": "",
	"comment": "",
	"shipped_at": 1498730137,
	"tracking_number": "",
	"pieces": 1,
	"shipped_area": {
		"id": 1,
		"name": "Aruba"
	},
	"company": {
		"id": 1,
		"name": "Bike"
	},
	"importer": {
		"id": 1,
		"name": "Bike"
	},
	"recipient": {
		"company_name": "Bike",
		"given_name": "Abc",
		"family_name": "Hi",
		"title": 1,
		"phone": "0123456789",
		"email": "abc@abc.com",
		"street": "qq",
		"city": "ww",
		"state": "ee",
		"postal_code": "123",
		"country": "Taiwan"
	},
	"histories": [{
		"id": 1,
		"status": "Preparing",
		"comment": "",
		"date": 1498730137
	}],
	"packages": [{
		"item": {
			"id": 1,
			"name": "watch"
		},
		"variant": {
			"id": 1,
			"name": "k1-gold"
		},
		"id": 1,
		"description": "",
		"invoice_show": true,
		"products": ["AAAA0000000001PD", "AAAA0000000011PD"],
		"unit_value": 999.99,
		"currency_name": "EUR"
	}],
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
	}],
	"status_message": {
		"country": "country not found",
		"importer": "importer not in country"
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| number | string | shipment number |
| proforma_invoice_number | string | proforma invoice number of shipment |
| status | string | shipment latest status |
| comment | string | shipment comment |
| shipped_at | timestamp | shipped date |
| tracking_number | string | tracking number of logistics company |
| pieces | integer | total unit of shipment |
| **shipped_area** | **object** | country of shipped area |
| *id* | integer | country id |
| *name* | name | country name |
| **company** | **object** | shipment creator |
| *id* | integer | company id |
| *name* | name | company name |
| **importer** | **object** | company of importer |
| *id* | integer | company id of importer |
| *name* | name | company name of importer |
| **recipient** | **object** | recipient information |
| *company_name* | string | the company which recipient belongs to |
| *given_name* | string | recipient given_name |
| *family_name* | string | recipient family_name |
| *title* | string | recipient title |
| *phone* | string | recipient phone |
| *email* | string | recipient email |
| *street* | string | recipient street |
| *city* | string | recipient city |
| *state* | string | recipient state |
| *postal_code* | string | recipient postal_code |
| *country* | string | recipient country |
| **histories** | **array** | shipment status |
| *id* | string | history city |
| *status* | string | history status |
| *comment* | string | history comment |
| *date* | string | history created date |
| **packages** | **array** | shipment packages |
| *id* | integer | package id |
| *item* | **object** | item information of package |
| *id* | integer | item id |
| *name* | name | item name |
| *variant* | **object** | variant information of package |
| *id* | integer | variant id |
| *name* | name | variant name |
| *proforma_description* | string | proforma description |
| *invoice_show* | boolean | show product number in the proforma invoice |
| *products* | array | a set of product number in the package |
| *unit_value* | double | unit value of item |
| *currency_name* | string | currency unit |
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
| *download* | string | download link |

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"does not signin"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | the name of the wrong type. |
|||**does not signin:** user does not signin|
||| **shipment not found:** shipment not exist |


## Create Shipment

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/shipment/create` |
| Method | `post` |
| Use | create shipment |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "proforma_invoice_number": "",
	"comment": "",
	"shipped_at": 1498730137,
	"tracking_number": "",
	"pieces": 1,
	"vat": {
		"country_id": 1,
		"importer_id": 1
	},
	"recipient": {
		"company_name": "Bike",
		"given_name": "Abc",
		"family_name": "Hi",
		"title": 1,
		"phone": "0123456789",
		"email": "abc@abc.com",
		"street": "qq",
		"city": "ww",
		"state": "ee",
		"postal_code": "123",
		"country": "Taiwan"
	},
	"added_histories": [{
		"status": "Preparing",
		"comment": "",
		"date": 1498730137
	}],
	"added_packages": [{
		"variant_id": 1,
		"proforma_description": "",
		"invoice_show": true,
		"products": ["AAAA0000000001PD", "AAAA0000000011PD"],
		"unit_value": 999.99
	}],
	"added_files": [{
		"name": "proforma.jpg",
		"date": 1498730137,
		"comment": "proforma invoice",
		"resource": ""
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| proforma_invoice_number | string (option) | proforma_invoice_number of shipment |
| comment | string (option) | shipment comment |
| shipped_at | timestamp (option) | shipped date |
| tracking_number | string (option) |  |
| pieces | integer (option) | total unit of shipment |
| **vat** | **object (option)** | vat information |
| *country_id* | integer  | country id of shipped area |
| *importer_id* | integer  | company id of importer in shipped country |
| **recipient** | **object (option)** | recipient information |
| *company_name* | string | the company which recipient belongs to |
| *given_name* | string | recipient given_name |
| *family_name* | string | recipient family_name |
| *title* | string | recipient title |
| *phone* | string | recipient phone |
| *email* | string | recipient email |
| *street* | string | recipient street |
| *city* | string | recipient city |
| *state* | string | recipient state |
| *postal_code* | string | recipient postal_code |
| *country* | string | recipient country |
| **added_histories** | **array (option)** | added histories |
| *status* | string | history status |
| *comment* | string | history comment |
| *date* | string | history created date |
| **added_packages** | **array (option)** | added packages |
| *variant_id* | integer | variant id of package |
| *proforma_description* | string | proforma description |
| *invoice_show* | boolean | show product number in the proforma invoice |
| *products* | array | a set of product number in the package |
| *unit_value* | double | unit value of item |
| **added_files** | **array (option)** | uploaded files |
| *name* | string | file name |
| *date* | timestamp | uploaded date |
| *comment* | string | file comment |
| *resource* | string | uploaded data |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"shipment_number": "AAAA0000000001SH"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| shipment_number | string | shipment number |


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
|||**does not signin:** user does not signin|
|||**illegal form input:** form format does not pass validation|
| **validation** | **object (option)** | if the err_name is illegal form input', systyem should show the name of the wrong for each error input. |
| *country* | **array (option)** | **country not found: ** |
| *importer* | **array (option)** | **importer not in country: ** |
| *histories* | **array (option)** | **invalid format: ** |
| *packages* | **array (option)** | **invalid format: ** |
||| **product conflict: ** product has already been assigned |
| **products** | **array (option)** | conflict products |
| product number | string | product number |
| *variant* | **object** | variant of product |
| id | integer | variant id |
| name | string | variant name |
| *files* | **array (option)** | **invalid format: ** |


## Edit Shipment

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/shipment/edit` |
| Method | `post` |
| Use | edit shipment |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "shipment_number": "AAAA0000000001SH",
    "proforma_invoice_number": "",
	"comment": "",
	"shipped_at": 1498730137,
	"tracking_number": "",
	"pieces": 1,
	"vat": {
		"country_id": 1,
		"importer_id": 1
	},
	"recipient": {
		"company_name": "Bike",
		"given_name": "Abc",
		"family_name": "Hi",
		"title": 1,
		"phone": "0123456789",
		"email": "abc@abc.com",
		"street": "qq",
		"city": "ww",
		"state": "ee",
		"postal_code": "123",
		"country": "Taiwan"
	},
	"added_histories": [],
	"added_packages": [],
	"added_files": [],
	"edited_histories": [{
		"id": 1,
		"comment": ""
	}],
	"edited_packages": [{
		"id": 1,
		"proforma_description": "",
		"invoice_show": true,
		"products": ["AAAA0000000001PD", "AAAA0000000011PD"],
		"unit_value": 999.99
	}],
	"deleted_histories": [1, 2, 3],
	"deleted_packages": [1, 2, 3],
	"deleted_files": [1, 2, 3]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| shipment_number | string | shipment number. |
| proforma_invoice_number | string (option) | proforma_invoice_number of shipment |
| comment | string (option) | shipment comment |
| shipped_at | timestamp (option) | shipped date |
| tracking_number | string (option) |  |
| pieces | integer (option) | total unit of shipment |
| **vat** | **object (option)** | vat information |
| *country_id* | integer  | country id of shipped area |
| *importer_id* | integer  | company id of importer in shipped country |
| **recipient** | **object (option)** | recipient information |
| *company_name* | string | the company which recipient belongs to |
| *given_name* | string | recipient given_name |
| *family_name* | string | recipient family_name |
| *title* | string | recipient title |
| *phone* | string | recipient phone |
| *email* | string | recipient email |
| *street* | string | recipient street |
| *city* | string | recipient city |
| *state* | string | recipient state |
| *postal_code* | string | recipient postal_code |
| *country* | string | recipient country |
| **added_histories** | **array (option)** | added histories |
| *status* | string | history status |
| *comment* | string | history comment |
| *date* | string | history created date |
| **added_packages** | **array (option)** | added packages |
| *id* | integer | variant id of package |
| *proforma_description* | string | proforma description |
| *invoice_show* | boolean | show product number in the proforma invoice |
| *products* | array | the products of package |
| *unit_value* | double | unit value of item |
| **added_files** | **array (option)** | uploaded files |
| *name* | string | file name |
| *date* | timestamp | uploaded date |
| *comment* | string | file comment |
| *resource* | string | uploaded data |
| **edited_histories** | **array (option)** | edited histories |
| *id* | integer | history id |
| *comment* | string | history comment |
| **edited_packages** | **array (option)** | edited packages |
| *id* | integer | package id |
| *proforma_description* | string | proforma description |
| *invoice_show* | boolean | show product number in the proforma invoice |
| *products* | array | a set of product number in the package |
| *unit_value* | double | unit value of item |
| **deleted_histories** | array (option) | a set of historie id |
| **deleted_packages** | array (option) | a set of package id |
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
|||**does not signin:** user does not signin|
|||**illegal form input:** form format does not pass validation|
| **validation** | **object (option)** | if the err_name is illegal form input', systyem should show the name of the wrong for each error input. |
| *country* | **array (option)** | **country not found: ** |
| *importer* | **array (option)** | **importer not in country: ** |
| *histories* | **array (option)** | **invalid format: ** |
| *packages* | **array (option)** | **invalid format: ** |
||| **product conflict: ** product has already been assigned |
| **products** | **array (option)** | conflict products |
| product number | string | product number |
| *variant* | **object** | variant of product |
| id | integer | variant id |
| name | string | variant name |
| *files* | **array (option)** | **invalid format: ** |


## Delete Shipment

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/shipment/delete` |
| Method | `post` |
| Use | delete shipment |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "shipment_number": "AAAA0000000001SH"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| shipment_number | string | shipment number. |


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
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
|||**does not signin:** user does not signin|
|||**shipment not found:** shipment not exist|
|||**permission denied:** not shipment owner|


## Get Profoma Invoice PDF

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/shipment/{shipment_number}/invoice/` |
| Method | `get` |
| Use | get Profoma Invoice pdf |
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

| Parameter | Type | Description |
| -------: | :---- | :--- |
| shipment_number | string | shipment number. |


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
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |