# Ejercicio 5: Mostrar Ubicación
Las aplicaciones pueden encontrar, rastrear y mostrar le geolocalización de un dispositivo con el widget `Locate`. Este widget usa **HTML 5 Geolocation API** para encontrar la ubicación del dispositivo y proporcionar actualizaciones. Una vez su geolocalización se encuentra, puede acercarse a la ubicación, mostrar un gráfico y seguir los cambios de su ubicación. El widget `Locate` encuentra y se acerca a su ubicación después de que se hace clic en el botón.
En este ejercicio usará el widget `Locate` para encontrar y mostrar su ubicación en un mapa.
## Cree una página HTML
1. Haciendo uso del editor de código de su preferencia, abra o copie el contenido del ejercicio anterior.
## Agregue los módulos
2. En la instrucción `require`, agregue los módulos `Locate` y `Compass`.
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
        
        "esri/rest/locator",
        /* BLOQUE AGREGADO */
        "esri/widgets/Locate",
        "esri/widgets/Compass"
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
        
        locator,
        /* BLOQUE AGREGADO */
        Locate,
        Compass
        /* FIN BLOQUE AGREGADO */
    ) {
        
    });
</script>
```
## Encuentre su geolocalización
El widget `Locate` usa HTML5 para encontrar la ubicación de su dispositivo y acercar el mapa. Agregue este widget al mapa para encontrar y mostrar su ubicación actual.

3. En la función principal, cree el widget `Locate` y establezca el parámetro `view` como `view`.
```javascript
function showAddress(address, pt) {
    view.popup.open({
        title:  + Math.round(pt.longitude * 100000)/100000 + ", " + Math.round(pt.latitude * 100000)/100000,
        content: address,
        location: pt
    });
}
/* BLOQUE AGREGADO */
const locateBtn = new Locate({
    view: view
});
/* FIN BLOQUE AGREGADO */
```
4. Agregue  el widget en la esquina superior izquierda, en la posición `3`.
```javascript
const locateBtn = new Locate({
    view: view
});
/* BLOQUE AGREGADO */
view.ui.add(locateBtn, {
    position: "top-left",
    index: 3
});
/* FIN BLOQUE AGREGADO */
```
## Agregue el widget Compass
El widget `Compass` indica dónde es el norte en relación a la rotación de la vista actual. Haciendo clic en este widget se rota la vista para mirar hacia el norte.

5. Cree un widget `Compass`. Establezca la propiedad `view` como `view`.
```javascript
view.ui.add(locateBtn, {
    position: "top-left",
    index: 3
});
/* BLOQUE AGREGADO */
const compassWidget = new Compass({
    view: view
});
/* FIN BLOQUE AGREGADO */
```
6. Agregue  el widget en la esquina superior izquierda, en la posición `4`.
```javascript
const compassWidget = new Compass({
    view: view
});
/* BLOQUE AGREGADO */
view.ui.add(compassWidget, {
    position: "top-left",
    index: 4
});
/* FIN BLOQUE AGREGADO */
```
## Ejecute su aplicación
Agregue su documento al servidor web de su preferencia y visualice el resultado en un navegador web.
