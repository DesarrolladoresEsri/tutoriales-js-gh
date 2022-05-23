# Ejercicio 1: Mostrar Mapa

Un mapa contiene capas de datos geográficos. Un mapa contiene una capa de mapa base y, opcionalmente, una o más capas de datos. Puede mostrar el área específica de un mapa usando una vista de mapa y configurando la ubicación y el nivel de cercanía.

En este ejercicio creará y mostrará un mapa de Bogotá, Colombia usando la capa de mapa base topográfico.

## Cree una página HTML
1. Haciendo uso del editor de código de su preferencia, cree un nuevo documento HTML.
2. Agregue el contenido principal HTML al documento. 
```html
<html>
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no" />
        <title>Mostrar un mapa: ArcGIS API para JavaScript</title>
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <script>
            esriConfig = {
                locale: "es"
            };
        </script>
        <style>
            html,
            body,
            #viewDiv {
                padding: 0;
                margin: 0;
                height: 100%;
                width: 100%;
            }
        </style>
    </head>
    <body>
        <div id="viewDiv"></div>
    </body>
</html>
```
## Agregue referencias a la API
3. En la etiqueta `head`, agregue las referencias al archivo CSS y la librería JS.
```html
<link rel="stylesheet" href="https://js.arcgis.com/4.23/esri/themes/dark/main.css">
<script src="https://js.arcgis.com/4.23/"></script>
```
## Agregue los módulos
La API de ArcGIS para JavaScript contiene módulos AMD. Haga referencia a los módulos `Map` y `MapView` en la instrucción `require`. 

4. En la etiqueta `head`, agregue una etiqueta `<script>` y una instrucción `require` de AMD para cargar los módulos `Map` y `MapView`.
```html
<script>
    require([
        "esri/config",
        "esri/Map",
        "esri/views/MapView"
    ], function (
        esriConfig,
        Map,
        MapView
    ) {
        
    });
</script>
```
## Consiga una API key
5. Ingrese al [cuadro de mando de desarrollador](https://developers.arcgis.com/dashboard/) para conseguir una API key. 
6. Copie la API key para poder usarla en el siguiente paso.
## Cree un mapa
Use un `Map` para establecer una capa de mapa base y aplicar su API key.

7. En su documento HTML, en la instrucción `require`, cree un nuevo `Map` y establezca la propiedad `basemap`como `arcgis-topographic`. Para habilitar el acceso al servicio de mapas base, establezca la propiedad `apiKey` de el `Map`.
```javascript
esriConfig.apiKey = "SU_API_KEY";

const map = new Map({
    basemap: "arcgis-topographic" 
});
```
## Cree una vista de mapa
Use una clase ```MapView```para establecer la ubicación del mapa que se mostrará. 

8. Cree una ```MapView``` y establezca la propiedad ```map```. Para centrar la vista de mapa, establezca la propiedad ```center``` como ```-74.090923, 4.694939``` y la propiedad ```zoom``` como ```11```. Establezca la propiedad ```container```como ```viewDiv```para mostrar los contenidos del mapa.
```javascript
const view = new MapView({
    map: map,
    center: [-74.090923, 4.694939], 
    zoom: 11, 
    container: "viewDiv" 
});
```
## Ejecute su aplicación
Agregue su documento al servidor web de su preferencia y visualice el resultado en un navegador web.
