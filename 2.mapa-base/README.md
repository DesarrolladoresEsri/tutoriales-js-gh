# Ejercicio 2: Mostrar Mapa
El servicio de capa de mapa base proporciona un número de estilos de capas de mapa base tales como topográfico, calles e imágenes que puede usar en sus mapas.
En este ejercicio usará los widgets BasemapGallery y BasemapToggle para seleccionar y mostrar diferentes capas de mapa base.
## Cree una página HTML
1. Haciendo uso del editor de código de su preferencia, abra o copie el contenido del ejercicio anterior.
## Agregue los módulos
2. En la instrucción `require`, agregue los módulos `BasemapToggle`, `BasemapGallery` y `Expand`.
```html
<link rel="stylesheet" href="https://js.arcgis.com/4.23/esri/themes/dark/main.css">
<script src="https://js.arcgis.com/4.23/"></script>

<script>
    require([
        "esri/config",
        "esri/Map",
        "esri/views/MapView",
        /* BLOQUE AGREGADO */
        "esri/widgets/BasemapToggle",
        "esri/widgets/BasemapGallery",
        "esri/widgets/Expand"
        /* FIN BLOQUE AGREGADO */
    ], function (
        esriConfig,
        Map,
        MapView,
        /* BLOQUE AGREGADO */
        BasemapToggle, 
        BasemapGallery,
        Expand
        /* FIN BLOQUE AGREGADO */
    ) {
        
    });
</script>
```
## Alterne entre mapas base
Una forma sencilla para habilitar la selección entre dos mapas base es usar el widget **Basemap Toggle**. Use el widget para alternar entre los mapas base `arcgis-topographic` y `arcgis-imagery`.

3. Cree un **Basemap Toggle** y establezca la vista. 
```javascript
const view = new MapView({
    map: map,
    center: [-74.090923, 4.694939], 
    zoom: 11, 
    container: "viewDiv" 
});

const basemapToggle = new BasemapToggle({
    view: view,
    nextBasemap: "arcgis-imagery"
});
```
4. Agregue el widget a la esquina inferior derecha (`bottom-right`) de la vista `view`.
```javascript
const basemapToggle = new BasemapToggle({
    view: view,
    nextBasemap: "arcgis-imagery"
});
/* BLOQUE AGREGADO */
view.ui.add(basemapToggle,"bottom-right");
/* FIN BLOQUE AGREGADO */
```
## Seleccione mapas base desde la galería
También puede usar el widget `BasemapGallery` para seleccionar diferentes mapas base. En este ejercicio se usará el widget `Expand` para incluir la galería en un botón y mantener una interfaz más limpia. 

5. Cree un `BasemapGallery`.
```javascript
view.ui.add(basemapToggle,"bottom-right");
/* BLOQUE AGREGADO */
const basemapGallery = new BasemapGallery({
    view: view
});
/* FIN BLOQUE AGREGADO */
```
6. Cree un `Expand` y establezca las propiedades `view`, `content` y `autoCollapse` como `view`, `basemapGallery` y `true` respectivamente.
```javascript
const basemapGallery = new BasemapGallery({
    view: view
});
/* BLOQUE AGREGADO */
const bgExpand = new Expand({
    view: view,
    content: basemapGallery,
    autoCollapse: true
});
/* FIN BLOQUE AGREGADO */
```
7. Agregue el widget `Expand` a la esquina superior derecha (`top-right`) de la vista `view`.
```javascript
const bgExpand = new Expand({
    view: view,
    content: basemapGallery,
    autoCollapse: true
});
/* BLOQUE AGREGADO */
view.ui.add(bgExpand, "top-right");
/* FIN BLOQUE AGREGADO */
```
## Ejecute su aplicación
Agregue su documento al servidor web de su preferencia y visualice el resultado en un navegador web.
