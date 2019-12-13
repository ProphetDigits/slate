# Company

## Search Companies

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/search` |
| Method | `post` |
| Use | To get companies by name |
| Notice | It's prefix search and return 10 companies most similar |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"search_text": "Test"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| search_text | string | The company name |


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
[{
	"id": 1,
	"name": "Test Shop",
	"cover_image": {
		"name": "xxx",
		"cover": true,
		"resource": {
			"240p": "http://abc/xxx_240p.jpg",
			"480p": "http://abc/xxx_480p.jpg",
			"720p": "http://abc/xxx_720p.jpg",
			"1080p": "http://abc/xxx_1080p.jpg"
		}
	},
	"owner": {
		"id": 1,
		"given_name": "Tester",
		"family_name": "Prophet",
		"email": "tester@prophetdigits.com"
	}
}, {
	"id": 2,
	"name": "Test Bike",
	"cover_image": {},
	"owner": {
		"id": 1,
		"given_name": "Tester",
		"family_name": "Prophet",
		"email": "tester@prophetdigits.com"
	}
}]
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | number | The company id |
| name | string | The company name |
| cover_image | object | The company’s cover image. If no set cover image, return empty |
| owner | object | The founder information of company |

| cover_image | Type | Description |
| -------: | :---- | :--- |
| name | string | The filename without extension |
| cover | boolean | The flag of cover image |
| resource | ojbect | The urls of each resolution |

| cover_image.resource | Type | Description |
| -------: | :---- | :--- |
| 240p | string | The picture url of 240 resolution (426x240) |
| 480p | string | The picture url of 480 resolution (854x480) |
| 720p | string | The picture url of 720 resolution (1280x720) |
| 1080p | string | The picture url of 1080 resolution (1920x1080) |

| owner | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| given_name | string | The given name |
| family_name | string | The family name |
| email | string | The email |

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>empty text: the search text cannot be empty</li></ul> |



## Company List

### Description

| Title | Description |
| -------: | :---- |
| URL | `company/list` |
| Method | `get` |
| Use | to get all companies list |
| Notice |  |


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
    "companies":[
        {
          "id": 1,
          "name": "CC Bike",
        },
        {
          "id": 2,
          "name": "BB Bike"
        }
    ]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **companies** | **array** | all companies in the system. Order by company name from A-Z |
| id | number | company’s id |
| name | string | company name |




<aside class="warning">
Failure
</aside>

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|




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
| Use | To create company |
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
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| short_number | string | The company short number, four letter and uppercase |
| name | string | The company name |
| website | string (option) | The company website link |
| description | string (option) | The company description |
| street | string | The street of company |
| city | string | The city of company |
| state | string (option) | The state of company |
| postal_code | string | The postal code of company |
| system_country_id | integer | The system country id |
| contact_given_name | string | The given name of contactor |
| contact_family_name | string | The family name of contactor |
| contact_job_title | string | The job title of contactor |
| contact_phone | string | The phone number of contactor |
| contact_email | string | The email of contactor |
| **images** | **array (option)** | The company images |
| *name* | string | The file name which get from API after uploded image |
| *cover* | boolean | The tag decide image is covered or not <br /> false: normal image <br /> true: cover image|


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |


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
| error_name | string | The failed reason which HTTP code is 403 |
|||**lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **illegal form input:** The data validation failed |
| **validation** | **object** | The validation parameter will appear if the error_name is illegal form input |
| *short_number* | array | **required:** The data cannot be empty or null |
|||**dulicate:** The short number has already been taken|
|||**invalid value:** The short number not be allow to use|
| *name* | array | **required:** The data cannot be empty or null |
|||**dulicate:** The name has already been taken |
| *street* | array | **required:** The data cannot be empty or null |
| *city* | array | **required:** The data cannot be empty or null |
| *state* | array | **required:** The data cannot be empty or null |
| *postal_code* | array | **required:** The data cannot be empty or null |
| *country* | array | **invalid country:** The country not exist |
| *contact_given_name* | array | **required:** The data cannot be empty or null |
| *contact_family_name* | array | **required:** The data cannot be empty or null |
| *contact_job_title* | array | **required:** The data cannot be empty or null |
| *contact_phone* | array | **required:** The data cannot be empty or null |
| *contact_email* | array | **required:** The data cannot be empty or null |


## Get Company Detail Without Login

### Description

| Title | Description |
| -------: | :---- |
| URL | `company/{company_id}/detail` |
| Method | `get` |
| Use | To get the company detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"company_id": "1"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| company_id | integer | The company id |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "name": "CC Bike",
    "default_currency": "USD",
    "currencies": [
        {
            "id": 1,
            "name": "EUR",
            "default": false,
            "exchange_rate": 1,
            "display_precision_point": 2
        },
        {
            "id": 3,
            "name": "USD",
            "default": true,
            "exchange_rate": 1.137,
            "display_precision_point": 2
        },
        {
            "id": 4,
            "name": "TWD",
            "default": false,
            "exchange_rate": 36,
            "display_precision_point": 0
        }
    ],
    "images":[{
        "name": "xxx.jpg",
        "cover": 1,
        "resource": {
            "px240": "http://abc/xxx_240p.jpg",
            "px480": "http://abc/xxx_480p.jpg",
            "px720": "http://abc/xxx_720p.jpg",
            "px1080": "http://abc/xxx_1080p.jpg"
        }
    }, {
        "name": "yyy.jpg",
        "cover": 0,
        "resource": {
            "px240": "http://abc/yyy_240p.jpg",
            "px480": "http://abc/yyy_480p.jpg",
            "px720": "http://abc/yyy_720p.jpg",
            "px1080": "http://abc/yyy_1080p.jpg"
        }
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id|
| name | string | The company name |
| default_currency | string | default currency of company |
| **currencies** | **array** | currencies which company own |
| *id* | number | The currency id of system|
| *name* | string | The currency name |
| *default* | boolean | The default currency of company |
| *exchange_rate* | number | The exchange rate of currency in the company|
| *display_precision_point* | integer | The precision point of currency. Display_precision_point > 0 indicate the digits of presicion <br /> ex: If the display_precision_point is 2, than the price should round to 9.12 from 9.119 |
| **images** | **array** | The company images |
| *name* | string | The image name |
| *cover* | boolean | Is cover image <br /> false: normal image <br /> true: cover image |
| **resource** | **object** | The resolution of picture |
| *px240* | string | picture url of 240 resolution (426x240) |
| *px480* | string | picture url of 480 resolution (854x480) |
| *px720* | string | picture url of 720 resolution (1280x720) |
| *px1080* | string | picture url of 1080 resolution (1920x1080) |

<aside class="warning">
Failure
</aside>

```json
{
	"error_name":"company not exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |
||| **company not exist:** The company not exist |


## Get Company Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/detail` |
| Method | `post` |
| Use | To get the company detail |
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
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |


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
		"manager": 1
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
| short_number | string | The company short number |
| name | string | The company name |
| website | string | The company website link |
| description | string | The company description |
| street | string | The street address of company |
| city | string | The city of company |
| state | string | The state of company |
| postal_code | string | The postal code of company |
| **country** | **object** | The country of company |
| *id* | integer | country id |
| *name* | string | country name |
| contact_given_name | string | The given name of contactor |
| contact_family_name | string | The family name of contactor |
| contact_job_title | string | The job title of contactor |
| contact_phone | string | The phone number of contactor |
| contact_email | string | The email of contactor |
| **images** | **array** | The company images |
| *name* | string | The image name |
| *cover* | boolean | Is cover image <br /> false: normal image <br /> true: cover image |
| **resource** | **object** | The resolution of picture |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 480 resolution (854x480) |
| *720p* | string | picture url of 720 resolution (1280x720) |
| *1080p* | string | picture url of 1080 resolution (1920x1080) |
| **owner** | **object** | The information of company owner |
| *id* | integer | The user id |
| *given_name* | string | The user given name |
| *family_name* | string | The owner family name |
| *email* | string | The user email |
| **members** | **array** | The members of company |
| *id* | integer | The user id |
| *given_name* | string | The user given name |
| *family_name* | string | The user family name |
| *email* | string | The user email |
| *administrator* | boolean | The administrator identify in the company |
| *manager* | boolean | The highest manager in the company |
| **currencies** | **array** | currencies which company own |
| *id* | number | The currency id of system|
| *name* | string | The currency name |
| *default* | boolean | The default currency of company |
| *exchange_rate* | number | The exchange rate of currency in the company|
| *display_precision_point* | integer | The precision point of currency. Display_precision_point > 0 indicate the digits of presicion <br /> ex: If the display_precision_point is 2, than the price should round to 9.12 from 9.119 |

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
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |


## Edit Company Profile

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/profile` |
| Method | `post` |
| Use | To edit company profile |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
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
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| name | string | The company name |
| website | string (option) | The company website link |
| description | string (option) | The company description |
| street | string | The street of company |
| city | string | The city of company |
| state | string (option) | The state of company |
| postal_code | string | The postal code of company |
| system_country_id | integer | The system country id |
| contact_given_name | string | The given name of contactor |
| contact_family_name | string | The family name of contactor |
| contact_job_title | string | The job title of contactor |
| contact_phone | string | The phone number of contactor |
| contact_email | string | The email of contactor |



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
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **not company member:** The user are not member in this company or no option with this company |
||| **company not exist:** The company not exist |
||| **no permission:** The permission deny |
|| |**illegal form input:** The data validation failed |
| **validation** | **object** | The validation parameter will appear if the error_name is illegal form input |
| *name* | array | **required:** The data cannot be empty or null |
|||**dulicate:** The name has already been taken |
| *street* | array | **required:** The data cannot be empty or null |
| *city* | array | **required:** The data cannot be empty or null |
| *state* | array | **required:** The data cannot be empty or null |
| *postal_code* | array | **required:** The data cannot be empty or null |
| *country* | array | **invalid country:** The country not exist |
| *contact_given_name* | array | **required:** The data cannot be empty or null |
| *contact_family_name* | array | **required:** The data cannot be empty or null |
| *contact_job_title* | array | **required:** The data cannot be empty or null |
| *contact_phone* | array | **required:** The data cannot be empty or null |
| *contact_email* | array | **required:** The data cannot be empty or null |



## Edit Company Images

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
			"cover": true
		}, {
			"name": "xxx.jpg",
			"cover": false
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| **images** | **array** | The company images |
| *name* | string | The file name which get from API after uploded image |
| *cover* | boolean | The tag decide image is covered or not <br /> false: normal image <br /> true: cover image|


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
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |
||| **not company member:** The user are not member in this company or no option with this company |
||| **no permission:** The permission deny |



## Add Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/add/member` |
| Method | `post` |
| Use | To add user into company as member |
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
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| email | string | The user email |


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
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |
||| **not company member:** The user are not member in this company or no option with this company |
||| **no permission:**  Not company administrator |
||| **duplicate join:** The user email is already joined to this company |
||| **user not exist:** The email is incorrent |



## Edit Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/member` |
| Method | `post` |
| Use | To edit authority of company member |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"email": "cc.lee@prophetdigits.com",
	"adminstrator": false
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| email | string | The user email |
| administrator | boolean | Is company administrator |


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
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |
||| **not company member:** The user are not member in this company or no option with this company |
||| **no permission:**  Not company administrator |
||| **not join:** The user email not join to this company |
||| **user not exist:** email is incorrent |



## Delete Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/delete/member` |
| Method | `post` |
| Use | To remove user from company member |
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
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| email | string | The user email |

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
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |
||| **not company member:** The user are not member in this company or no option with this company |
||| **no permission:**  Not company administrator |
||| **not join:** The user email not join to this company |
||| **user not exist:** email is incorrent |



## Edit Company Currencies

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/currency` |
| Method | `post` |
| Use | To edit company currencies |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"currencies": [{
		"currency_id": 1,
		"exchange_rate": 0.3,
		"default": true
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| **currencies** | **array** | The company currencies |
| *currency_id* | integer | The currency id |
| *exchange_rate* | number | The default currency to specific currency exchange rate |
| *default* | boolean | Is default currency |


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
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |
||| **not company member:** The user are not member in this company or no option with this company |
||| **duplicate default currency:** Two currencies is setted as the default currency |
||| **no default currency:** No currencies is setted as the default currency |



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
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |


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
        "id": 228,
        "name": "Taiwan",
        "importers": 2
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **countries** | **array** | countries of company |
| *company_country_id* | integer | company country id |
| *id* | integer | country id |
| *name* | string | country name |
| *importers* | integer | importer number in the country |

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