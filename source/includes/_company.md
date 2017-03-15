# Company

## Search Company

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/search` |
| Method | `post` |
| Use | to get all companies in the system |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"search_text": "CC"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| search_text | string | key word about company name |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"companies":[{
		"id": 1,
		"name": "CC Shop",
		"cover_img": {
			"240p": "http://abc/xxx_240p.jpg",
			"480p": "http://abc/xxx_480p.jpg",
			"720p": "http://abc/xxx_720p.jpg",
			"1080p": "http://abc/xxx_1080p.jpg"
		},
		"owner": {
			"id": 1,
			"given_name": "Wang",
			"family_name": "Jianhua",
			"email": "a@gmail.com"
		}
	}, {
		"id": 2,
		"name": "CC Bike",
		"cover_img": {},
		"owner": {
			"id": 1,
			"given_name": "Wang",
			"family_name": "Jianhua",
			"email": "a@gmail.com"
		}
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **companies** | **array** | all companies in the system. Order by company name from A-Z |
| id | number | company’s id |
| name | string | company name |
| cover_image | **object** | company’s cover image.If no set cover image, return empty. **Include:** |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 480 resolution (854x480) |
| *720p* | string | picture url of 720 resolution (1280x720) |
| *1080p* | string | picture url of 1080 resolution (1920x1080) |
| owner | **object** | company owner's information. **Include:** |
| *id* | integer | owner's user id |
| *given_name* | string | owner given_name |
| *family_name* | string | owner family_name |
| *email* | string | owner email |


<aside class="warning">
Failure
</aside>

```
{
	"error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|



## Company List Of User

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/list` |
| Method | `post` |
| Use | to get all companies of user |
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
	"companies":[{
		"id": 2,
		"name": "CC Bike",
		"cover_img": {},
		"owner": {
			"id": 1,
			"given_name": "Wang",
			"family_name": "Jianhua",
			"email": "a@gmail.com"
		},
		"selected": false,
		"currency": "EUR"
	}],
	"companies_with_option":[{
		"id": 3,
		"name": "CC Bike",
		"cover_img": {
			"240p": "http://abc/xxx_240p.jpg",
			"480p": "http://abc/xxx_480p.jpg",
			"720p": "http://abc/xxx_720p.jpg",
			"1080p": "http://abc/xxx_1080p.jpg"
		},
		"owner": {
			"id": 1,
			"given_name": "Wang",
			"family_name": "Jianhua",
			"email": "a@gmail.com"
		},
		"selected": true,
		"currency": "CHF"
	}],
	"current_company":{
		"id": 2,
		"name": "CC Bike",
		"cover_img": {
			"240p": "http://abc/xxx_240p.jpg",
			"480p": "http://abc/xxx_480p.jpg",
			"720p": "http://abc/xxx_720p.jpg",
			"1080p": "http://abc/xxx_1080p.jpg"
		},
		"owner": {
			"id": 1,
			"given_name": "Wang",
			"family_name": "Jianhua",
			"email": "a@gmail.com"
		},
		"selected": true,
		"currency": "CHF"
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **companies** | **array** | all companies in the system. Order by company name from A-Z |
| id | number | company’s id |
| name | string | company name |
| cover_image | **object** | company’s cover image.If no set cover image, return empty. **Include:** |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 480 resolution (854x480) |
| *720p* | string | picture url of 720 resolution (1280x720) |
| *1080p* | string | picture url of 1080 resolution (1920x1080) |
| owner | **object** | company owner's information. **Include:** |
| *id* | integer | owner's user id |
| *given_name* | string | owner given_name |
| *family_name* | string | owner family_name |
| *email* | string | owner email |
| selected | boolean | current company |
| currency | string | default currency of company |
| companies_with_option | array | companies which has signed with current companies. Content is same to above companies. |
| current_company | array | Current companies. Content is same to above companies. |



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



## Create Company

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/create` |
| Method | `post` |
| Use | to create company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"short_number": "AAAA",
	"name": "CC Bike",
	"website": "",
	"description": "",
	"street": "",
	"city": "",
	"state": "",
	"postal_code": "",
	"system_country_id": 228,
	"contact_given_name":  "Jianhua",
	"contact_family_name":  "Wang",
	"contact_job_title":  "coder",
	"contact_phone":  "0987654321",
	"contact_email":  "abc@gmail.com",
	"images":[{
			"name": "xxx.jpg",
			"cover": 1
		}, {
			"name": "xxx.jpg",
			"cover": 0
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| short_number | string | company short_number, four letter and uppercase |
| name | string | company name |
| website | string |company website link |
| description | string | company description |
| street | string | street of company |
| city | string | city of company |
| state | string | state of company |
| postal_code | string | postal code of company |
| system_country_id | integer | country id |
| contact_given_name | string | contact given name |
| contact_family_name | string | contact family name |
| contact_job_title | string | contact job title |
| contact_phone | string | contact phone number |
| contact_email | string | contact email |
| **images** | array | company images |
| name | string | file name which get from back end after specific image has been updated |
| cover | integer | cover image tag |
|||0: normal image|
|||1: cover image|


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
	"error_name": "illegal form input",
	"validation": {
		"name": ["dulicate"],
		"country": ["required"]
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**illegal form input:** form format does not pass validation|
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):** |
| short_number | array | **required:** it’s necessary parameter |
|||**dulicate:** the short number has already been taken|
|||**invalid value:** the short number not be allow to use|
| name | array | **required:** it’s necessary parameter |
|||**dulicate:** the name has already been taken|
| street | array | **required:** it’s necessary parameter |
| city | array | **required:** it’s necessary parameter |
| state | array | **required:** it’s necessary parameter |
| postal_code | array | **required:** it’s necessary parameter |
| country | array | **required:** it’s necessary parameter |
| contact_given_name | array | **required:** it’s necessary parameter |
| contact_family_name | array | **required:** it’s necessary parameter |
| contact_job_title | array | **required:** it’s necessary parameter |
| contact_phone | array | **required:** it’s necessary parameter |
| contact_email | array | **required:** it’s necessary parameter |



## Company Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/detail` |
| Method | `post` |
| Use | to get the company detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": "1"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | integer | company's id |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"short_number": "AAAA",
	"name": "CC Bike",
	"website": "",
	"description": "",
	"street": "",
	"city": "",
	"province": "",
	"postal_code": "",
	"country": {
        "id": 228,
        "name": "taiwan"
    },
	"contact_given_name": "XX",
	"contact_family_name": "X",
	"contact_job_title": "xxx",
	"contact_phone": "0987654321",
	"contact_email": "abc@gmail.com",
	"owner": {
		"id": 1,
		"given_name": "Wang",
		"family_name": "Jianhua",
		"email": "a@gmail.com"
	},
	"members": [{
		"id": 1,
		"given_name": "QQ",
		"family_name": "Wang",
		"email": "a@gmail.com",
		"administrator": 1,
		"manager": 1,
		"role": {
			"id": 1,
			"name": "Unsigned"
		}
	}],
	"role": [{
		"id": 1,
		"name": "Unsigned",
		"default": 1,
		"permissions": {
			"item": {
				"view": 0,
				"edit": 0,
				"delete": 0
			}
		},
			"product": {
				"view": 0,
				"edit": 0,
				"delete": 0
			},
			"option": {
				"view": 0,
				"edit": 0,
				"delete": 0
			},
			"order": {
				"view": 0,
				"edit": 0,
				"delete": 0
			},
			"sell": 0
	}],
	"images":[{
		"name": "xxx.jpg",
		"cover": true,
		"resource": {
			"240p": "http://abc/xxx_240p.jpg",
			"480p": "http://abc/xxx_480p.jpg",
			"720p": "http://abc/xxx_720p.jpg",
			"1080p": "http://abc/xxx_1080p.jpg"
		}
	}, {
		"name": "yyy.jpg",
		"cover": false,
		"resource": {
			"240p": "http://abc/yyy_240p.jpg",
			"480p": "http://abc/yyy_480p.jpg",
			"720p": "http://abc/yyy_720p.jpg",
			"1080p": "http://abc/yyy_1080p.jpg"
		}
	}],
	"currencies": [{
		"id": 1,
		"name": "EUR",
		"default": 1,
		"exchange_rate": 0,
		"display_precision_point": 2
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id|
| short_number | string | company short_number, four letter and uppercase |
| name | string | company name |
| website | string |company website link |
| description | string | company description |
| street | string | street of company |
| city | string | city of company |
| state | string | state of company |
| postal_code | string | postal code of company |
| *country* | *object* | country of company |
| *id* | integer | country id|
| *name* | string | country name|
| contact_given_name | string | contact given name |
| contact_family_name | string | contact family name |
| contact_job_title | string | contact job title |
| contact_phone | string | contact phone number |
| contact_email | string | contact email |
| **images** | **array** | company's images |
| name | string |  |
| cover | boolean |  |
| resource | **object** | each resolution of picture |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 480 resolution (854x480) |
| *720p* | string | picture url of 720 resolution (1280x720) |
| *1080p* | string | picture url of 1080 resolution (1920x1080) |
| owner | **object** | company owner's information. **Include:** |
| *id* | integer | owner's user id |
| *given_name* | string | owner given_name |
| *family_name* | string | owner family_name |
| *email* | string | owner email |
| **members** | **array** | members of company |
| id | integer | member's user id |
| given_name | string | member's given name |
| family_name | string | member's family name |
| email | string | member's email |
| role | **object** | member's role of company |
| *id* | integer | role id in the company |
| *name* | string | role name in the company |
| administrator | boolean | administrator identify in the company |
| manager | boolean | highest manager in the company |
| **roles** | **array** | roles of company |
| id | integer | role id |
| name | string | role name |
| default | boolean | default currency |
| permissions | **object** | permission of role |
| *item* | object | permission detail |
||| **view:**  [boolean] user can view |
||| **edit:**  [boolean] user can add and edit |
||| **delete:**  [boolean] user can delete |
| *product* | object | permission detail, as item. |
| *option* | object | permission detail, as item. |
| *order* | object | permission detail, as item. |
| *sell* | boolean | user can sell. |
| **currencies** | **array** | currencies which company own |
| id | number | currency id of system|
| name | string | currency name |
| default | boolean | default currency |
| exchange_rate | number | exchange rate of currency in the company|
| display_precision_point | integer | precision point of currency. Display_precision_point > 0 indicate the digits of presicion|
|||ex: display_precision_point = 2, price should round to 9.12 from 9.119|

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
|||**not company member:** user are not member in this company or no option with this company|
|||**company not exist:** company not exist|



## Edit Company Profile

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/profile` |
| Method | `post` |
| Use | to edit company profile |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"name": "CC Bike",
	"website": "",
	"description": "",
	"street": "",
	"city": "",
	"state": "",
	"postal_code": "",
	"system_country_id": 228,
	"contact_given_name":  "Jianhua",
	"contact_family_name":  "Wang",
	"contact_job_title":  "coder",
	"contact_phone":  "0987654321",
	"contact_email":  "abc@gmail.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| name | string | company name |
| website | string |company website link |
| description | string | company description |
| street | string | street of company |
| city | string | city of company |
| state | string | state of company |
| postal_code | string | postal code of company |
| system_country_id | integer | country id |
| contact_given_name | string | contact given name |
| contact_family_name | string | contact family name |
| contact_job_title | string | contact job title |
| contact_phone | string | contact phone number |
| contact_email | string | contact email |



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
	"error_name": "illegal form input",
	"validation": {
		"name": ["dulicate"],
		"country": ["required"]
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not company member:** user are not member in this company or no option with this company|
|||**company not exist:** company not exist|
|||**no permission:** authority too low|
|||**illegal form input:** form format does not pass validation|
| **validation** | **object** | if the err_name is illegal form input', web backend should assign the name of the wrong type for each error input. **Value(option):** |
| name | array | **required:** it’s necessary parameter |
|||**dulicate:** the name has already been taken|
| street | array | **required:** it’s necessary parameter |
| city | array | **required:** it’s necessary parameter |
| state | array | **required:** it’s necessary parameter |
| postal_code | array | **required:** it’s necessary parameter |
| country | array | **required:** it’s necessary parameter |
| contact_given_name | array | **required:** it’s necessary parameter |
| contact_family_name | array | **required:** it’s necessary parameter |
| contact_job_title | array | **required:** it’s necessary parameter |
| contact_phone | array | **required:** it’s necessary parameter |
| contact_email | array | **required:** it’s necessary parameter |



## Edit Company Image

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/image` |
| Method | `post` |
| Use | to edit company image |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"images":[{
			"name": "xxx.jpg",
			"cover": 1
		}, {
			"name": "xxx.jpg",
			"cover": 0
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | string | company id |
| **images** | array | company images |
| name | string | file name which get from back end after specific image has been updated |
| cover | integer | cover image tag |
|||0: normal image|
|||1: cover image|


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
	"error_name": "company not exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not company member:** user are not member in this company or no option with this company|
|||**company not exist:** company not exist|
|||**no permission:** authority too low|



## Add Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/add/member` |
| Method | `post` |
| Use | to add user into company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"email": "cc.lee@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | string | company id |
| email | string | email of new member |


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
	"error_name": "duplicate join"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not company member:** user are not member in this company or no option with this company|
|||**company not exist:** company not exist|
|||**no permission:**  not company administrator|
|||**duplicate join:** user of email already joined to this company|
|||**user not exist:** email is incorrent|



## Edit Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/member` |
| Method | `post` |
| Use | to edit authority of company member |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"email": "cc.lee@prophetdigits.com",
	"role_id": 1,
	"adminstrator": false
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | string | company id |
| email | string | user email |
| role_id | integer | role id of company |
| administrator | boolean | administrator tag |


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
	"error_name": "not join"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not company member:** user are not member in this company or no option with this company|
|||**company not exist:** company not exist|
|||**no permission:**  not company administrator|
|||**not join:** user of email not join to this company|
|||**user not exist:** email is incorrent|
|||**role not exist:** role id is incorrent|



## Delete Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/delete/member` |
| Method | `post` |
| Use | to delete relations with company member |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"email": "cc.lee@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | string | company id |
| email | string | user email |

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
	"error_name": "not join"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not company member:** user are not member in this company or no option with this company|
|||**company not exist:** company not exist|
|||**no permission:**  not company administrator|
|||**not join:** user of email not join to this company|
|||**user not exist:** email is incorrent|



## Create Company Role

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/create/role` |
| Method | `post` |
| Use | to create role into company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"name": "CEO"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | string | company id |
| name | string | role name |


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
	"error_name": "no permission"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not company member:** user are not member in this company or no option with this company|
|||**company not exist:** company not exist|
|||**no permission:**  not company administrator|



## Delete Company Role

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/delete/role` |
| Method | `post` |
| Use | to delete company role |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"role_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | string | company id |
| role_id | integer | role id of company |


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
	"error_name": "no permission"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not company member:** user are not member in this company or no option with this company|
|||**company not exist:** company not exist|
|||**no permission:**  not company administrator|
|||**role not exist:** role id incorrent|
|||**default role:** default role cannot be deleted|



## Edit Company Currency

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/currency` |
| Method | `post` |
| Use | to edit exchange rate of currency |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"currencies": [{
		"currency_id": 1,
		"exchange_rate": 0.3,
		"default": 1
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | integer | company_id |
| **currencies** | **array** | company currency setting |
| currency_id | integer | currency id |
| exchange_rate | number | default currency to specific currency exchange rate |
| default | boolean | default currency tag |


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
|||**not company member:** doesn’t join to this company|
|||**no permission:** not company manager|
|||**duplicate default currency**|
|||**no default currency**|



## Authority Of Company

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/auth` |
| Method | `post` |
| Use | to get authority of currency |
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
| company_id | integer | company_id |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"manager": {
		"profile":{
			"edit": false
		},
		"member": {
			"edit": false,
			"delete": false
		},
		"role": {
			"edit": false,
			"delete": false
		},
		"currency": {
			"edit": false
		}
	},
	"role": {
		"item":{
			"view": true,
			"edit": false,
			"delete": false
		},
		"product": {
			"view": true,
			"edit": false,
			"delete": false
		},
		"option": {
			"view": true,
			"edit": false,
			"delete": false
		},
		"order": {
			"view": true,
			"edit": false,
			"delete": false
		},
		"sell": true
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **manager** | **object** | user's authority in the company |
| *profile* | object | **edit:** [boolean] user can edit company profile|
|||**delete:** [boolean] user can delete member|
| *member* | object | **edit:** [boolean] user can add and edit member|
| *role* | object | **edit:** [boolean] user can add and edit role|
|||**delete:** [boolean] user can delete role|
| *currency* | object | **edit:** [boolean] user can add and edit currency|
| **role** | **object** | user permissions in the company |
| *item* | object | permission detail |
||| **view:**  [boolean] user can view |
||| **edit:**  [boolean] user can add and edit |
||| **delete:**  [boolean] user can delete |
| *product* | object | permission detail, as item. |
| *option* | object | permission detail, as item. |
| *order* | object | permission detail, as item. |
| *sell* | boolean | user can sell. |

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
|||**not company member:** doesn’t join to this company|
|||**no permission:** not company manager|


## Change Current Company

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/select/company` |
| Method | `post` |
| Use | change app’s global company to operate app functions |
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
| company_id | integer | company id|


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
|||**not company member:** doesn’t join to this company|
|||**company not exist:** the company is not exist|


## Generate Company Short Number

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/short_number/generate` |
| Method | `post` |
| Use | to get company short number which be generated by system |
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
	"short_number": "AAAA"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| short_number | string | short number of company |

<aside class="warning">
Failure
</aside>

```json
{
	"error_name": "illegal form input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  the name of the wrong type.|
|||Value:|
|||**lack of parameters:**  the request does not include the necessary parameters|
|||**does not signin:** user does not signin|



## Get Company Country List

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/country/list |
| Method | `post` |
| Use | to get countries of company |
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
    "countries": [{
        "company_country_id": 2,
        "name": "Taiwan",
        "importers": 2
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **countries** | **array** | countries of company |
| *company_country_id* | integer | country id |
| *name* | string | country name |
| *importers* | integer | importer number in country |

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
||| **lack of parameters:**  the request does not include the necessary parameters |
||| **does not signin:** user does not signin |


## Get Company Country Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/country/detail |
| Method | `post` |
| Use | to get detail of countries of company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "company_country_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_country_id | integer | company country id |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 2,
    "country_id": 228,
    "fixed_vat": 10,
    "adjusted_vats": [{
        "id": 1,
        "name": "fruit",
        "rate": 5,
        "comment": "",
        "items": []
      }, {
        "id": 2,
        "name": "3C",
        "rate": 15,
        "comment": "",
        "items": [
          2,
          3
        ]
    }],
    "importers": [{
        "id": 2,
        "name": "Company B",
        "comment": "test2"
      }, {
        "id": 3,
        "name": "Company D",
        "comment": ""
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | company country id |
| country_id | integer | country id |
| fixed_vat | integer | fixed vat |
| **adjusted_vats** | **array** | adjusted vats |
| *name* | *string* | name of adjusted vat |
| *rate* | *integer* | rate of adjusted vat |
| *comment* | *string* | comment of adjusted vat |
| **items** | **array** | a set of item id which has been assigned to this vat |
| **importers** | **array** | importers in country |
| *id* | *integer* | company id |
| *name* | *string* | company name |
| *comment* | *string* | comment for importer |

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
||| **lack of parameters:**  the request does not include the necessary parameters |
||| **does not signin:** user does not signin |


## Create Country

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/create/country |
| Method | `post` |
| Use | to create vat and importers to country of company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "country_id": 1,
    "fixed_vat": 0,
    "adjusted_vats": [{
        "name": "",
        "rate": 0,
        "comment": "",
        "items": []
    }],
    "importers": [{
        "id": 1,
        "comment": ""
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| country_id | integer | country id |
| fixed_vat | integer | fixed vat rate |
| **adjusted_vats** | **array** | adjusted vats |
| *name* | *string* | name of adjusted vat |
| *rate* | *integer* | rate of adjusted vat |
| *comment* | *string* | comment of adjusted vat |
| **items** | **array** | a set of item id which has been assigned to this vat |
| **importers** | **array** | importers in country |
| *id* | *integer* | company id |
| *comment* | *string* | comment for importer |

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
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
||| **lack of parameters:**  the request does not include the necessary parameters |
||| **does not signin:** user does not signin |
||| **country not exist:** select invalid country in system |
||| **country has been exist:** duplicate vat of country |


## Edit Country

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/edit/country |
| Method | `post` |
| Use | to edit vat and  importers to country of company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "id": 1,
    "country_id": 1,
    "fixed_vat": 0,
    "adjusted_vats": [{
        "name": "",
        "rate": 0,
        "comment": "",
        "items": []
    }],
    "importers": [{
        "id": 1,
        "comment": ""
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| id | integer | company country id |
| country_id | integer | country id |
| fixed_vat | integer | fixed vat rate |
| **adjusted_vats** | **array** | adjusted vats |
| *name* | *string* | name of adjusted vat |
| *rate* | *integer* | rate of adjusted vat |
| *comment* | *string* | comment of adjusted vat |
| **items** | **array** | a set of item id which has been assigned to this vat |
| **importers** | **array** | importers in country |
| *id* | *integer* | company id |
| *comment* | *string* | comment for importer |

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
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
||| **lack of parameters:**  the request does not include the necessary parameters |
||| **does not signin:** user does not signin |
||| **country not exist:** select invalid country in system |
||| **country has been exist:** duplicate vat of country |


## Delete Country

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/delete/country |
| Method | `post` |
| Use | to edit vat of company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "company_country_id": 1,
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_country_id | integer | country id of company |

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
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
||| **lack of parameters:**  the request does not include the necessary parameters |
||| **does not signin:** user does not signin |