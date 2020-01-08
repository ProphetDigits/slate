# Inventory

## Search Near Products

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.08 / Joey Huang**

  * Modify Failure Parameter:
    * Apply new structure
    * Modify the description of the failure response

</details>

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/item/product/search/distance` |
| Method | `post` |
| Use | to get company list which own unsold products and distance in 10 km |
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
| api_key | string | System gives it after user sign in |
| target_company_id | integer | The company id of variant |
| variant_id | integer | The variant id |
| latitude | number | The latitude of location |
| longitude | number | The longitude of location |

> Return Success Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "companies": [{
    "id": 1,
    "name": "CC Bike",
    "description": "...",
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
| companies | array | The set of company which own stock and distance in 10 km |

| company | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id |
| name | string | company name |
| description | string |  company description |
| stock | integer | product number of variant |
| distance | number | the distance between current location and target company(km) |
| street | string | street of company |
| city | string | city of company |
| state | string | state of company |
| postal_code | string | postal_code of company |
| country | string | country of company |
| latitude | number | latitude of location |
| longitude | number | longitude of location |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"variant_not_exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>target_company_not_exist: the target_company_id of a company does not exist</li><li>no_option: The permission deny by target company </li><li>variant_not_exist: The variant is not exist or not belongs to target company</li></ul> |

## Search Inventory

<details>
  <summary>Change Log</summary>
  <div class="summary-content">

  **2020.01.08 / Joey Huang**

  * Modify Failure Parameter:
    * Apply new structure

</details>

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
| api_key | string | System gives it after user sign in |
| item_name | string | The item name |
| company_id | integer | The company id |

> Return Success Parameters

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
| inventories | array | The stock of variant and its location |

| inventory | Type | Description |
| -------: | :---- | :--- |
| id | integer | The variant id |
| name | string | The variant name |
| stock | integer | The stock in the location |
| location | object | The location of inventory |
| item | object | The item of variant |

| location | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company  id |
| name | string | The company name |
| street | string | The street of company |
| city | string | The city of company |
| state | string | The state of company |
| postal_code | string | The postal_code of company |
| country | string | The country of company |
| latitude | number | The latitude of location |
| longitude | number | The longitude of location |

| item | Type | Description |
| -------: | :---- | :--- |
| id | integer | The item id |
| number | string | The item number |
| name | string | The item name |

> Return Failure Parameters

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"not_select_company"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li></ul> |
