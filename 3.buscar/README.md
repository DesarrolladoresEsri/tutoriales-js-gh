# Ejercicio 3: Buscar Direcciones
El servicio de capa de mapa base proporciona un número de estilos de capas de mapa base tales como topográfico, calles e imágenes que puede usar en sus mapas.
En este ejercicio usará los widgets BasemapGallery y BasemapToggle para seleccionar y mostrar diferentes capas de mapa base.
## Cree una página HTML
1. Haciendo uso del editor de código de su preferencia, abra o copie el contenido del ejercicio anterior.
## Agregue los módulos
2. En la instrucción `require`, agregue los módulos `Search` y `Home`.
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
        /* BLOQUE AGREGADO */
        "esri/widgets/Search",
        "esri/widgets/Home"
        /* FIN BLOQUE AGREGADO */
    ], function (
        esriConfig,
        Map,
        MapView,
        
        BasemapToggle, 
        BasemapGallery,
        Expand,
        /* BLOQUE AGREGADO */
        Search,
        Home
        /* FIN BLOQUE AGREGADO */
    ) {
        
    });
</script>
```
## Actualice el mapa
Una capa de mapa base de calles es usado típicamente en aplicaciones de geocodificación. Actualice la propiedad `basemap` para usar el mapa base `arcgis-navigation`.

3. Actualice la propiedad `basemap` de `arcgis-topographic` a `arcgis-navigation`.
```javascript
esriConfig.apiKey = "SU_API_KEY";

const map = new Map({
    /* BLOQUE EDITADO */
    basemap: "arcgis-navigation"
    /* FIN BLOQUE EDITADO */ 
});
```
## Agregue el widget Search
El widget `Search` es un control visible que le permite buscar de forma interactiva direcciones y lugares. Este proporciona sugerencias a medida que se escribe y le permite seleccionar un resultado. Cuando selecciona un resultado, se acerca a una ubicación y muestra una ventana emergente con información de la dirección. Por defecto, el widget usa un `locator` y `source` que acceden al servicio de Geocodificación. 

4. Cree un widget `Search`. Establezca la propiedad `view` como `view`.
```javascript
const bgExpand = new Expand({
    view: view,
    content: basemapGallery,
    autoCollapse: true
});
view.ui.add(bgExpand, "top-right");
/* BLOQUE AGREGADO */
const search = new Search({
    view: view
});
/* FIN BLOQUE AGREGADO */
```
5. Agregue  el widget en la esquina superior izquierda, en la posición `0`.
```javascript
const search = new Search({
    view: view
});
view.ui.add(search, {
    position: "top-left",
    index: 0
});
```
## Agregue el widget Home
El widget `Home` permite cambiar la vista a su punto de vista inicial rápidamente.

6. Cree un widget `Home`. Establezca la propiedad `view` como `view`.
```javascript
const search = new Search({
    view: view
});
view.ui.add(search, {
    position: "top-left",
    index: 0
});
/* BLOQUE AGREGADO */
const homeBtn = new Home({
    view: view
});
/* FIN BLOQUE AGREGADO */
```
7. Agregue  el widget en la esquina superior izquierda, en la posición `2`.
```javascript
const homeBtn = new Home({
    view: view
});
/* BLOQUE AGREGADO */
view.ui.add(homeBtn, {
    position: "top-left",
    index: 2
});
/* FIN BLOQUE AGREGADO */
```
## Ejecute su aplicación
Agregue su documento al servidor web de su preferencia y visualice el resultado en un navegador web.
