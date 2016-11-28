# Inventory

## Search Near Products

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product/search/distance` |
| Method | `post` |
| Use | to get user nearby company list which own products of variant |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "target_company_id": 1,
  "variant_id": 1,
  "latitude": 24.6543,
  "longitude": 120.64621
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| target_company_id | integer | company id of variant |
| variant_id | integer | variant id |
| latitude | number | latitude of gps exclude direction |
| longitude | number | longitude of gps exclude direction |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "companies": [{
    "id": 1,
    "name": "CC Bike",
    "stock": 5,
    "street": "",
    "city": "",
    "state": "",
    "postal_code": "",
    "country": "",
    "latitude": 24.65321,
    "longitude": 120.63216,
    "distance": 1
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **companies** | **array** |  |
| id | integer |  company  id |
| name | string |  company  name |
| description | string |  company description |
| stock | integer | product number of variant |
| company_id | integer | variant belongs to which company |
| distance | number | the distance between current company and target company(km) |
| street | string | street of company |
| city | string | city of company |
| state | string | state of company |
| postal_code | string | postal_code of company |
| country | string | country of company |
| latitude | number | latitude of location |
| longitude | number | longitude of location |

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


## Search Inventory

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/inventory/search` |
| Method | `post` |
| Use | to get inventory list. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "item_name": "Evo v1",
  "company_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| item_name | string | number of purchase order |
| company_id | integer | company id  |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "inventories": [{
    "id": 1,
    "name": "S-Red",
    "stock": 5,
    "location": {
      "id": 1,
      "name": "Company A",
      "street": "",
      "city": "",
      "state": "",
      "postal_code": "",
      "country": "",
      "latitude": 24.65321,
      "longitude": 120.63216
    },
    "item": {
      "id": 1,
      "number": "1",
      "name": "Company A"
    }
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | variant’s id |
| name | string | variant’s name |
| stock | integer | stock quantity in the retailer |
| **location** | **object** | location of stock of variant |
| id | integer |  company  id |
| name | string |  company  name |
| street | string | street of company |
| city | string | city of company |
| state | string | state of company |
| postal_code | string | postal_code of company |
| country | string | country of company |
| latitude | number | latitude of location |
| longitude | number | longitude of location |
| **item** | **object** | variant belongs to which item |
| id | integer | item’s id |
| number | string | item’s number |
| name | string | item’s name |


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
|||**lack of parameters:** the request does not include the necessary parameters |
|||**does not signin:** user does not signin |
|||**not select company yet:** user need change current company |
|||**company not exist:** currenct company not exist |
|||**not company member:** the user is not the company member |
|||**no permission:**cannot purchase in the current company |
