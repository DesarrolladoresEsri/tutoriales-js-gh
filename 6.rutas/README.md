# Ejercicio 5: Mostrar Ubicación
El cálculo de rutas es el proceso de encontrar el camino desde un origen a un destino en una red de calles. Puede usar el servicio de cálculo de rutas para encontrar rutas, obtener indicaciones de conducción, calcular tiempos de conducción y resolver problemas complejos de cálculo de rutas de múltiples vehículos. El widget `Directions` facilita el cálculo de indicaciones entre dos o más ubicaciones. Las indicaciones resultantes se muestran en detalle con instrucciones en cada giro.
En este ejercicio usará el widget `Directions` para calcular una ruta entre dos o más ubicaciones.
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
        
        "esri/widgets/Locate",
        "esri/widgets/Compass",
        /* BLOQUE AGREGADO */
        "esri/widgets/Directions"
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
        
        Locate,
        Compass,
        /* BLOQUE AGREGADO */
        Directions
        /* FIN BLOQUE AGREGADO */
    ) {
        
    });
</script>
```
## Calcule rutas
El widget `Directions` facilita el cálculo de indicaciones entre dos o más ubicaciones. Las indicaciones resultantes se muestran en detalle con instrucciones en cada giro.

3. En la función principal, cree el widget `Directions` y establezca el parámetro `view` como `view`.
```javascript
view.ui.add(compassWidget, {
    position: "top-left",
    index: 4
});
/* BLOQUE AGREGADO */
let directionsWidget = new Directions({
    view: view
});
/* FIN BLOQUE AGREGADO */
```
4. Cree un `Expand` y establezca las propiedades `view`, `content` y `autoCollapse` como `view`, `directionsWidget` y `false` respectivamente.
```javascript
let directionsWidget = new Directions({
    view: view
});
/* BLOQUE AGREGADO */
const rtExpand = new Expand({
    view: view,
    content: directionsWidget,
    autoCollapse: false
});
view.ui.add(rtExpand, "top-right");
/* FIN BLOQUE AGREGADO */
```
## Ejecute su aplicación
Agregue su documento al servidor web de su preferencia y visualice el resultado en un navegador web.