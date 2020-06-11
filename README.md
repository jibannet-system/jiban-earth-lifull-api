### API Document

**API_ROOT:** https://api.jiban.earth

## List API
###### 1. [Authentications](#1-authentications)
###### 2. [Get Tile Data](#2-get-tile-data)


***********************

## 1. Authentications
* **URL:** [{API_ROOT}/auth/:key](#)
* **Method:** GET
* **Parameter**: **:key**
* **Content Type:** application/json
* **Reponse Type:** text/json

#### Request: 
		URL: [{API_ROOT}/auth/abc123
#### Response:
    
  ```
	{
        "status": "success",
        "access_token": 4AS2LdsNCIMhKVXjaABz
    }
  ```
  
 ## 2. Get Tile Data
* **URL:** [{API_ROOT}/tile/:map_type/:access_token/:x/:y/:z](#)
* **Method:** GET
* **Parameter**:
    * Map Type: **map_type**
    * Access Token: **access_token**
    * X: **x**
    * Y: **y**
    * Z: **z**
* **Content Type:** application/json
* **Reponse Type:** text/json

#### Request: 
		URL: [{API_ROOT}/tile/shaking/4AS2LdsNCIMhKVXjaABz/29101/12902/16
#### Response:
    
  ```
	{
        "status": "success",
        "tile": LdsNCIMh_12902.png
    }
  ```
