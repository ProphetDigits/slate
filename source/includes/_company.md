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
| id | integer | The company id |
| name | string | The company name |
| cover_image | object | The company’s cover image. If no set cover image, return empty |
| owner | object | The founder information of company |

| cover_image | Type | Description |
| -------: | :---- | :--- |
| name | string | The filename without extension |
| cover | boolean | The tag that decide image is cover or not <ul><li>true: cover image</li><li>false: normal image </li></ul> |
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
| Use | To get all companies |
| Notice |  |


### Input Parameters

There is no parameters


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "companies":[{
        "id": 1,
        "name": "Test Shop"
    }, {
        "id": 2,
        "name": "Test Bike"
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| companies | array | Collection of company. Order by company name from A-Z |

| company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |

<aside class="warning">
Failure
</aside>

There is no failure



## Company List Of User

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/list` |
| Method | `post` |
| Use | To get companies of user |
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
    "companies": [{
        "id": 2,
        "name": "Test Bike",
        "cover_image": {},
        "owner": {
            "id": 1,
            "given_name": "Tester",
            "family_name": "Prophet",
            "email": "tester@prophetdigits.com"
        },
        "selected": true,
        "currency": "EUR"
    }],
    "companies_with_option": [{
        "id": 3,
        "name": "Test Bike",
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
            "id": 2,
            "given_name": "Tester",
            "family_name": "Digits",
            "email": "tester@prophetdigits.com"
        },
        "selected": false,
        "currency": "CHF"
    }],
    "current_company": {
        "id": 2,
        "name": "Test Bike",
        "cover_image": {},
        "owner": {
            "id": 1,
            "given_name": "Tester",
            "family_name": "Prophet",
            "email": "tester@prophetdigits.com"
        },
        "selected": true,
        "currency": "EUR"
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| companies | array | Collection of company that user created or joined. Order by company name from A-Z |
| companies_with_option | array | Collection of company that signed option with current company |
| current_company | object | Current company of user |

| company | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |
| cover_image | object | The company’s cover image. If no set cover image, return empty |
| owner | object | The founder information of company |
| selected | boolean | The tag of current company <ul><li>true: current company</li><li>false: not current company</li></ul> |
| currency | string | The default currency name |

| company.cover_image | Type | Description |
| -------: | :---- | :--- |
| name | string | The filename without extension |
| cover | boolean | The tag that decide image is cover or not <ul><li>true: cover image</li><li>false: normal image </li></ul> |
| resource | ojbect | The urls of each resolution |

| company.cover_image.resource | Type | Description |
| -------: | :---- | :--- |
| 240p | string | The picture url of 240 resolution (426x240) |
| 480p | string | The picture url of 480 resolution (854x480) |
| 720p | string | The picture url of 720 resolution (1280x720) |
| 1080p | string | The picture url of 1080 resolution (1920x1080) |

| company.owner | Type | Description |
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
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li></ul> |



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
    "name": "Test Bike",
    "website": "",
    "description": "description",
    "street": " street",
    "city": "city",
    "state": "",
    "postal_code": "777",
    "system_country_id": 228,
    "contact_given_name":  "Tester",
    "contact_family_name":  "Prophet",
    "contact_job_title":  "coder",
    "contact_phone":  "0987654321",
    "contact_email":  "tester@prophetdigits.com",
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
| api_key | string | The identity token of user |
| short_number | string | The short number of company, four letters and uppercase |
| name | string | The company name |
| website | string | The company website link |
| description | string | The company description |
| street | string | The street of company |
| city | string | The city of company |
| state | string | The state of company |
| postal_code | string | The postal code of company |
| system_country_id | integer | The country id of system |
| contact_given_name | string | The given name of contacts |
| contact_family_name | string | The family name of contacts |
| contact_job_title | string | The job title of contacts |
| contact_phone | string | The phone number of contacts |
| contact_email | string | The email of contacts |
| images | array (option) | Collection of company image |

| image | Type | Description |
| -------: | :---- | :--- |
| name | string | The temporary filename which takes from uploded image api |
| cover | boolean | The tag that decide image is cover or not <ul><li>true: cover image</li><li>false: normal image </li></ul> |


> Return Success Parameters

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

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "illegal form input",
    "validation": {
        "name": ["duplicate"],
        "country": ["invalid country"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>illegal_form_input: the input does not pass validation</li></ul> |
| validation | object (option) | If the error_name is 'illegal form input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| short_number | array (option) | required: <ol><li>The short_number cannot be empty or null</li></ol> duplicate: <ol><li>The short_number has already been taken</li></ol> invalid value: <ol><li>The short_number not be allow to use</li></ol> |
| name | array (option) | required: <ol><li>The name cannot be empty or null</li></ol> duplicate: <ol><li>The name has already been taken</li></ol> |
| description | array (optoin) | required: <ol><li>The name cannot be empty or null</li></ol> |
| street | array (optoin) | required: <ol><li>The street cannot be empty or null</li></ol> |
| city | array (optoin) | required: <ol><li>The city cannot be empty or null</li></ol> |
| postal_code | array (optoin) | required: <ol><li>The postal_code cannot be empty or null</li></ol> |
| country | array (optoin) | invalid country: <ol><li>The country has not been exist</li></ol> |
| contact_given_name | array (optoin) | required: <ol><li>The contact_given_name cannot be empty or null</li></ol> |
| contact_family_name | array (optoin) | required: <ol><li>The contact_family_name cannot be empty or null</li></ol> |
| contact_job_title | array (optoin) | required: <ol><li>The contact_job_title cannot be empty or null</li></ol> |
| contact_phone | array (optoin) | required: <ol><li>The contact_phone cannot be empty or null</li></ol> |
| contact_email | array (optoin) | required: <ol><li>The contact_email cannot be empty or null</li></ol> |



## Company Detail Without Signin

### Description

| Title | Description |
| -------: | :---- |
| URL | `company/{company_id}/detail` |
| Method | `get` |
| Use | To get the company detail |
| Notice |  |


### Url Parameters

| Parameter | Type | Description |
| -------: | :---- | :--- |
| company_id | integer | The company id |


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "name": "Test Bike",
    "default_currency": "USD",
    "currencies": [{
        "id": 3,
        "name": "USD",
        "default": true,
        "exchange_rate": 1.137,
        "display_precision_point": 2
    }, {
        "id": 4,
        "name": "TWD",
        "default": false,
        "exchange_rate": 36,
        "display_precision_point": 0
    }],
    "images":[{
        "name": "xxx.jpg",
        "cover": true,
        "resource": {
            "px240": "http://abc/xxx_240p.jpg",
            "px480": "http://abc/xxx_480p.jpg",
            "px720": "http://abc/xxx_720p.jpg",
            "px1080": "http://abc/xxx_1080p.jpg"
        }
    }, {
        "name": "yyy.jpg",
        "cover": false,
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
| id | integer | The company id|
| name | string | The company name |
| default_currency | string | The default currency name |
| currencies | array | Collection of company currency |
| images | array | Collection of company image |

| currency | Type | Description |
| -------: | :---- | :--- |
| id | number | The currency id of system|
| name | string | The currency name |
| default | boolean | The tag that is it default currency for company |
| exchange_rate | number | The exchange rate of currency in the company |
| display_precision_point | integer | The minimize denominations of currency. <br /> ex.: If the value is 2, than the price should not show third decimal place |

| image | Type | Description |
| -------: | :---- | :--- |
| name | string | The filename |
| cover | boolean | The tag that decide image is cover or not <ul><li>true: cover image</li><li>false: normal image </li></ul> |
| resource | ojbect | The urls of each resolution |

| company.cover_image.resource | Type | Description |
| -------: | :---- | :--- |
| px240 | string | The picture url of 240 resolution (426x240) |
| px480 | string | The picture url of 480 resolution (854x480) |
| px720 | string | The picture url of 720 resolution (1280x720) |
| px1080 | string | The picture url of 1080 resolution (1920x1080) |

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>company not exist: the company not exist</li></ul> |



## Company Detail

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
    "company_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| company_id | integer | The company id |


> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "short_number": "AAAA",
    "name": "Test Bike",
    "website": "",
    "description": "",
    "street": "",
    "city": "",
    "state": "",
    "postal_code": "",
    "country": {
        "id": 228,
        "name": "taiwan"
    },
    "contact_given_name": "Tester",
    "contact_family_name": "Prophet",
    "contact_job_title": "coder",
    "contact_phone": "0987654321",
    "contact_email": "tester@prophetdigits.com",
    "owner": {
        "id": 1,
        "given_name": "Tester",
        "family_name": "Prophet",
        "email": "tester@prophetdigits.com"
    },
    "members": [{
        "id": 1,
        "given_name": "Tester",
        "family_name": "Prophet",
        "email": "tester@prophetdigits.com",
        "administrator": true,
        "manager": true
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
        "default": true,
        "exchange_rate": 1,
        "display_precision_point": 2
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id|
| short_number | string | The short number of company, four letters and uppercase |
| name | string | The company name |
| website | string | The company website link |
| description | string | The company description |
| street | string | The street of company |
| city | string | The city of company |
| state | string | The state of company |
| postal_code | string | The postal code of company |
| country | object | The country of company |
| contact_given_name | string | The given name of contacts |
| contact_family_name | string | The family name of contacts |
| contact_job_title | string | The job title of contacts |
| contact_phone | string | The phone number of contacts |
| contact_email | string | The email of contacts |
| images | array | Collection of company image |
| owner | object | The information of company owner |
| members | array | Collection of company member |
| currencies | array | Collection of company currency |

| country | Type | Description |
| -------: | :---- | :--- |
| id | integer | The country id |
| name | string | The country name |

| image | Type | Description |
| -------: | :---- | :--- |
| name | string | The filename |
| cover | boolean | The tag that decide image is cover or not <ul><li>true: cover image</li><li>false: normal image </li></ul> |
| resource | ojbect | The urls of each resolution |

| image.resource | Type | Description |
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

| member | Type | Description |
| -------: | :---- | :--- |
| id | integer | The user id |
| given_name | string | The given name |
| family_name | string | The family name |
| email | string | The email |
| administrator | boolean | The tag that is it company administrator |
| manager | boolean | The tag that is it company owner |

| currency | Type | Description |
| -------: | :---- | :--- |
| id | number | The currency id of system|
| name | string | The currency name |
| default | boolean | The tag that is it default currency for company |
| exchange_rate | number | The exchange rate of currency in the company |
| display_precision_point | integer | The minimize denominations of currency. <br /> ex.: If the value is 2, than the price should not show third decimal place |

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li></ul> |



## Edit Company Profile

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/profile` |
| Method | `post` |
| Use | To edit company profile |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "company_id": 1,
    "name": "Test Bike",
    "website": "",
    "description": "",
    "street": "",
    "city": "",
    "state": "",
    "postal_code": "",
    "system_country_id": 228,
    "contact_given_name":  "Tester",
    "contact_family_name":  "Prophet",
    "contact_job_title":  "coder",
    "contact_phone":  "0987654321",
    "contact_email":  "tester@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| company_id | integer | The company id |
| name | string | The company name |
| website | string | The company website link |
| description | string | The company description |
| street | string | The street of company |
| city | string | The city of company |
| state | string | The state of company |
| postal_code | string | The postal code of company |
| system_country_id | integer | The system country id |
| contact_given_name | string | The given name of contacts |
| contact_family_name | string | The family name of contacts |
| contact_job_title | string | The job title of contacts |
| contact_phone | string | The phone number of contacts |
| contact_email | string | The email of contacts |


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
    "error_name": "illegal form input",
    "validation": {
        "name": ["duplicate"],
        "country": ["required"]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li><li>no permission: the permission deny</li><li>illegal form input: the input does not pass validation</li></ul> |
| validation | object (option) | If the error_name is 'illegal form input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| name | array (option) | required: <ol><li>The name cannot be empty or null</li></ol> duplicate: <ol><li>The name has already been taken</li></ol> |
| description | array (optoin) | required: <ol><li>The name cannot be empty or null</li></ol> |
| street | array (optoin) | required: <ol><li>The street cannot be empty or null</li></ol> |
| city | array (optoin) | required: <ol><li>The city cannot be empty or null</li></ol> |
| postal_code | array (optoin) | required: <ol><li>The postal_code cannot be empty or null</li></ol> |
| country | array (optoin) | invalid country: <ol><li>The country has not been exist</li></ol> |
| contact_given_name | array (optoin) | required: <ol><li>The contact_given_name cannot be empty or null</li></ol> |
| contact_family_name | array (optoin) | required: <ol><li>The contact_family_name cannot be empty or null</li></ol> |
| contact_job_title | array (optoin) | required: <ol><li>The contact_job_title cannot be empty or null</li></ol> |
| contact_phone | array (optoin) | required: <ol><li>The contact_phone cannot be empty or null</li></ol> |
| contact_email | array (optoin) | required: <ol><li>The contact_email cannot be empty or null</li></ol> |



## Edit Company Images

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/image` |
| Method | `post` |
| Use | To edit company image |
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
| api_key | string | The identity token of user |
| company_id | integer | The company id |
| images | array | Collection of company image |

| image | Type | Description |
| -------: | :---- | :--- |
| name | string | The temporary filename which takes from uploded image api |
| cover | boolean | The tag that decide image is cover or not <ul><li>true: cover image</li><li>false: normal image </li></ul> |


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
    "error_name": "company not exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li><li>no permission: the permission deny</li></ul> |



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
    "email": "tester@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| company_id | integer | The company id |
| email | string | The email |


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
    "error_name": "duplicate join"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li><li>no permission: the permission deny</li><li>user not exist: the email has not been registered</li><li>duplicate join: the user has been joined to company</li></ul> |



## Edit Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/member` |
| Method | `post` |
| Use | To edit authority of company member |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "company_id": 1,
    "email": "tester@prophetdigits.com",
    "adminstrator": false
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| company_id | integer | The company id |
| email | string | The email |
| administrator | boolean | The authority of administrator |


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
    "error_name": "not join"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li><li>no permission: the permission deny</li><li>user not exist: the email has not been registered</li><li>not join: The user not join to this company</li></ul> |



## Delete Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/delete/member` |
| Method | `post` |
| Use | To remove company member |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "company_id": 1,
    "email": "tester@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| company_id | integer | The company id |
| email | string | The email |


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
    "error_name": "not join"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li><li>no permission: the permission deny</li><li>user not exist: the email has not been registered</li><li>not join: The user not join to this company</li></ul> |



## Edit Company Currencies

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/currency` |
| Method | `post` |
| Use | To edit company currencies |
| Notice | |


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
| currencies | array | Collection of company currencies |

| currency | Type | Description |
| -------: | :---- | :--- |
| currency_id | integer | The currency id |
| exchange_rate | number | The exchange rate compared to default currency |
| default | boolean | The tag that is it default currency for company |


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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li><li>duplicate default currency: two currencies is setted as the default currency</li><li>no default currency: no currency is setted as the default currency</li></ul> |



## Change Current Company

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/select/company` |
| Method | `post` |
| Use | To change current comapny of user |
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
| api_key | string | The identity token of user |
| company_id | integer | The company id |


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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li></ul> |



## Generate Company Short Number

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/short_number/generate` |
| Method | `post` |
| Use | To get a random short number of company |
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
    "short_number": "AAAA"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| short_number | string | The short number of company |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "short number is full"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>short number is full: there are not available short number</li></ul> |



## Get Vat Country List

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/country/list |
| Method | `post` |
| Use | To get vat countries of company |
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
| countries | array | Collection of company country |

| country | Type | Description |
| -------: | :---- | :--- |
| company_country_id | integer | The country id of company |
| id | integer | The country id of system |
| name | string | The country name |
| importers | integer | The importer quantity |

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: current company not select</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li></ul> |



## Get Vat Country Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/country/detail |
| Method | `post` |
| Use | To get vat country detail of company |
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
| api_key | string | The identity token of user |
| company_country_id | integer | The country id of company |


> Return Success Parameters

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
        "name": "fruit",
        "rate": 5,
        "comment": "",
        "items": []
    }, {
        "name": "3C",
        "rate": 15,
        "comment": "",
        "items": [2, 3]
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
| id | integer | The country id of company |
| country_id | integer | The country id of system |
| fixed_vat | integer | The fixed vat |
| adjusted_vats | array | Collection of adjusted vat |
| importers | array | Collection of importer |

| adjusted_vat | Type | Description |
| -------: | :---- | :--- |
| name | string | The name of adjusted vat |
| rate | integer | The rate of adjusted vat |
| comment | string | The comment of adjusted vat |
| items | array | Collection of item id |

| importer | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| name | string | The company name |
| comment | string | The comment for importer |

> Return Failure Parameters

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
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: current company not select</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li><li>country not found: the country not exist</li></ul> |



## Create Vat Country

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/create/country |
| Method | `post` |
| Use | To create vat country of company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "country_id": 1,
    "fixed_vat": 10,
    "adjusted_vats": [{
        "name": "VIP goods",
        "rate": 5,
        "comment": "",
        "items": [1, 2]
    }],
    "importers": [{
        "id": 1,
        "comment": ""
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| country_id | integer | The country id of system |
| fixed_vat | integer | The fixed vat |
| adjusted_vats | array | Collection of adjusted vat |
| importers | array | Collection of importer |

| adjusted_vat | Type | Description |
| -------: | :---- | :--- |
| name | string | The name of adjusted vat |
| rate | integer | The rate of adjusted vat |
| comment | string | The comment of adjusted vat |
| items | array | Collection of item id |

| importer | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| comment | string | The comment for importer |


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
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: current company not select</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li><li>country not exist: the country not exist in system</li><li>country has been exist: duplicate vat country</li><li>illegal form input: the input does not pass validation</li></ul> |
| validation | object (option) | If the error_name is 'illegal form input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| fixed_vat | array (option) | invalid vat: <ol><li>The fixed_vat should more than 0 and less than 100</li></ol> |
| adjusted_vat | array (option) | invalid vat: <ol><li>The fixed_vat should more than 0 and less than 100</li></ol> |



## Edit Vat Country

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/edit/country |
| Method | `post` |
| Use | To edit vat country of company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "id": 2,
    "country_id": 1,
    "fixed_vat": 10,
    "adjusted_vats": [{
        "name": "VIP goods",
        "rate": 5,
        "comment": "",
        "items": [1, 2]
    }],
    "importers": [{
        "id": 1,
        "comment": ""
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | The identity token of user |
| id | integer | The country id of company |
| country_id | integer | The country id of system |
| fixed_vat | integer | The fixed vat |
| adjusted_vats | array | Collection of adjusted vat |
| importers | array | Collection of importer |

| adjusted_vat | Type | Description |
| -------: | :---- | :--- |
| name | string | The name of adjusted vat |
| rate | integer | The rate of adjusted vat |
| comment | string | The comment of adjusted vat |
| items | array | Collection of item id |

| importer | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |
| comment | string | The comment for importer |


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
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: current company not select</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li><li>country doesnot exist: the vat country not exist</li><li>country has been exist: duplicate vat country</li><li>country not exist: the country not exist in system</li><li>illegal form input: the input does not pass validation</li></ul> |
| validation | object (option) | If the error_name is 'illegal form input', system will show reasons for each error input |

| validation | Type | Description |
| -------: | :---- | :--- |
| fixed_vat | array (option) | invalid vat: <ol><li>The fixed_vat should more than 0 and less than 100</li></ol> |
| adjusted_vat | array (option) | invalid vat: <ol><li>The fixed_vat should more than 0 and less than 100</li></ol> |



## Delete Vat Country

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/delete/country |
| Method | `post` |
| Use | To delete vat country of company |
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
| api_key | string | The identity token of user |
| company_country_id | integer | The country id of company |


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
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>lack of parameters: required parameters miss in the request</li><li>does not signin: the user does not signin</li><li>not select company yet: current company not select</li><li>company not exist: the company not exist</li><li>not company member: user is not member in this company</li></ul> |