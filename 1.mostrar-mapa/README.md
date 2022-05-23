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