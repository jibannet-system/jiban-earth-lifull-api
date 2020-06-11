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
* **URL:** [{API_ROOT}/tile/:map_type/:access_token/:z/:x/:y.png](#)
* **Method:** GET
* **Parameter**:
    * Map Type: **map_type**
    * Access Token: **access_token**
    * Z: **z**
    * X: **x**
    * Y: **y**
* **Content Type:** application/json
* **Reponse Type:** text/json

#### Request: 
		URL: [{API_ROOT}/tile/shaking/4AS2LdsNCIMhKVXjaABz/16/29101/12902.png
#### Response:
    
  ```
  12902.png
  ```
  
  
# USING WITH GOOGLE MAP
* **(1)** Add an element to the page, where the map should appear. 
```html
<div id="map"></div>
```

* **(2)** Add the Maps API script to your page:

```html
<script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY"></script>
```

* **(3)** Create a new map, attached to the element.

```javascript
var mapEl = document.querySelector('#map');
var map = new google.maps.Map(mapEl, {
  center: new google.maps.LatLng(39.8282, -98.5795),
  zoom: 5
});
```

* **(4)** Replace the sample `TILE_URL` with your own, which should look (roughly) like: `https://api.jiban.earth/tile/:map_type/:access_token/:z/:x/:y.png`.

Create a new tile layer using this URL:

```javascript
// Replace this with your URL.
var TILE_URL = 'https://api.jiban.earth/tile/shaking/4AS2LdsNCIMhKVXjaABz/:z/:x/:y.png';

// Name the layer anything you like.
var layerID = 'my_custom_layer';

// Create a new ImageMapType layer.
var layer = new google.maps.ImageMapType({
  name: layerID,
  getTileUrl: function(coord, zoom) {
    console.log(coord);
    var url = TILE_URL
      .replace(':x', coord.x)
      .replace(':y', coord.y)
      .replace(':z', zoom);
    return url;
  },
  tileSize: new google.maps.Size(256, 256),
  minZoom: 1,
  maxZoom: 20
});
```

* **(5)** Add the new tile layer to your map:

```javascript
// Register the new layer, then activate it.
map.mapTypes.set(layerID, layer);
map.setMapTypeId(layerID);
```

A complete example is shown in `index.html`.

Further documentation at [Google Maps JS API: Image Map Types](https://developers.google.com/maps/documentation/javascript/maptypes#ImageMapTypes).
