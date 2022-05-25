# Ejercicio 4: Geocidificación Inversa
La geocodificación inversa es el proceso de convertir una ubicación en una dirección o sitio. Para hacer una geocodificación inversa se usa el servicio de geocodificación y la operación `reverseGeocode`. Esta operación requiere una ubicación inicial y retorna una dirección con atributos tales como el nombre del lugar y la ubicación. Para simplificar el acceso al servicio de geocodificación, en este ejercicio se usa el módulo `locator`.
En este ejercicio usará el módulo `locator` para hacer una geocidificación inversa y encontrar una dirección donde haga clic en el mapa.
## Cree una página HTML
1. Haciendo uso del editor de código de su preferencia, abra o copie el contenido del ejercicio anterior.
## Agregue los módulos
2. En la instrucción `require`, agregue el módulo `locator`.
```html
<link rel="stylesheet" href="https://js.arcgis.com/4.23/esri/themes/dark/main.css">
<script src="https://js.arcgis.com/4.23/"></script>

<script>
    require([
        "esri/config",
        "esri/Map",
        "esri/views/MapView",
        
        "esri/widgets/BasemapToggle",
        "esri/widgets/BasemapGallery",
        "esri/widgets/Expand",
        
        "esri/widgets/Search",
        "esri/widgets/Home",
        /* BLOQUE AGREGADO */
        "esri/rest/locator"
        /* FIN BLOQUE AGREGADO */
    ], function (
        esriConfig,
        Map,
        MapView,
        
        BasemapToggle, 
        BasemapGallery,
        Expand,
        
        Search,
        Home,
        /* BLOQUE AGREGADO */
        locator
        /* FIN BLOQUE AGREGADO */
    ) {
        
    });
</script>
```
## Defina la url del servicio
Use el módulo `locator` para acceder al servicio de Geocodificación y la operación `reverseGeocode`.

3. Defina una variable, `serviceUrl`, para referenciar el servicio de Geocodificación.
```javascript
const homeBtn = new Home({
    view: view
});
view.ui.add(homeBtn, {
    position: "top-left",
    index: 2
});
/* BLOQUE AGREGADO */
const serviceUrl = "http://geocode-api.arcgis.com/arcgis/rest/services/World/GeocodeServer";
/* FIN BLOQUE AGREGADO */
```
## Realice geocodificación inversa
Use un controlador para capturar la ubicación del clic en el mapa y llamar al servicio de Geocodificación. El servicio retorna una dirección si la encuentra, o un error si no puede encontrar un resultado. Muestre los resultados en una ventana emergente con la latitud, longitud y dirección.

4. En la función principal, agregue un controlador `click`  a la vista. Cree `params` y establezca el parámetro `location` como `evt.mapPoint`.
```javascript
const serviceUrl = "http://geocode-api.arcgis.com/arcgis/rest/services/World/GeocodeServer";
/* BLOQUE AGREGADO */
view.on("hold", function(evt){
    const params = {
        location: evt.mapPoint
    };

});
/* FIN BLOQUE AGREGADO */
```
5. Cree una función `showAddress` para mostrar las coordenadas y la correspondiente dirección.
```javascript
view.on("hold", function(evt){
    const params = {
        location: evt.mapPoint
    };

});
/* BLOQUE AGREGADO */
function showAddress(address, pt) {
    view.popup.open({
        title:  + Math.round(pt.longitude * 100000)/100000 + ", " + Math.round(pt.latitude * 100000)/100000,
        content: address,
        location: pt
    });
}
/* FIN BLOQUE AGREGADO */
```
6. Actualice el controlador `clic` para llamar a `locationToAddress` para aplicar geocodificación inversa a `mapPoint`. Use la función `showAddress` para mostrar una ventana emergente con los resultados. 
```javascript
view.on("hold", function(evt){
    const params = {
        location: evt.mapPoint
    };
    /* BLOQUE AGREGADO */
    locator.locationToAddress(serviceUrl, params)
        .then(function(response) {
            const address = response.address;
            console.log(response);
            showAddress(address, evt.mapPoint);
        }, function(err) {
        showAddress("No se encontró dirección.", evt.mapPoint);
    });
    /* FIN BLOQUE AGREGADO */
});
```
## Ejecute su aplicación
Agregue su documento al servidor web de su preferencia y visualice el resultado en un navegador web.
