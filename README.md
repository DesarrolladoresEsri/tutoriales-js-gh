# Iniciando en el desarrollo de aplicaciones web con la API de ArcGIS para Javascript
Use la **API de ArcGIS para JavaScript** para construir aplicaciones web atractivas que explotan el potencial de sus datos con una experiencia de usuario interactiva y visualizaciones 2D y 3D sorprendentes.
![Captura](/img/6.rutas.PNG)
Si quiere conocer todo el potencial, características y herramientas que ofrece la **API de ArcGIS para Javascript**, visite la [documentación](https://developers.arcgis.com/javascript/) en el portal de [ArcGIS para Desarrolladores](https://developers.arcgis.com/).
## Ejercicio 1: Mostrar Mapa
Un mapa contiene capas de datos geográficos. Un mapa contiene una capa de mapa base y, opcionalmente, una o más capas de datos. Puede mostrar el área específica de un mapa usando una vista de mapa y configurando la ubicación y el nivel de cercanía.
En este ejercicio creará y mostrará un mapa de Bogotá, Colombia usando la capa de mapa base topográfico.
- [Ir al ejercicio](1.mostrar-mapa/README.md)
## Ejercicio 2: Mostrar Mapa
El servicio de capa de mapa base proporciona un número de estilos de capas de mapa base tales como topográfico, calles e imágenes que puede usar en sus mapas.
En este ejercicio usará los widgets `BasemapGallery` y `BasemapToggle` para seleccionar y mostrar diferentes capas de mapa base.
- [Ir al ejercicio](2.mapa-base/README.md)
## Ejercicio 3: Buscar Direcciones
La geocodificación es el proceso de convertir una dirección o lugar en una ubicación. El servicio de Geocodificación puede buscar una dirección o lugar y realizar geocodificación inversa. Use el widget `Search` para acceder al servicio de Geocodificación y realizar búsquedas interactivas.
En este ejercicio usará el widget `Search` para buscar direcciones y sitios de interés.
- [Ir al ejercicio](3.buscar/README.md)
## Ejercicio 4: Geocidificación Inversa
La geocodificación inversa es el proceso de convertir una ubicación en una dirección o sitio. Para hacer una geocodificación inversa se usa el servicio de geocodificación y la operación `reverseGeocode`. Esta operación requiere una ubicación inicial y retorna una dirección con atributos tales como el nombre del lugar y la ubicación. Para simplificar el acceso al servicio de geocodificación, en este ejercicio se usa el módulo `locator`.
En este ejercicio usará el módulo `locator` para hacer una geocidificación inversa y encontrar una dirección donde haga clic en el mapa.
- [Ir al ejercicio](4.geocodificacion-inversa/README.md)
## Ejercicio 5: Mostrar Ubicación
Las aplicaciones pueden encontrar, rastrear y mostrar le geolocalización de un dispositivo con el widget `Locate`. Este widget usa **HTML 5 Geolocation API** para encontrar la ubicación del dispositivo y proporcionar actualizaciones. Una vez su geolocalización se encuentra, puede acercarse a la ubicación, mostrar un gráfico y seguir los cambios de su ubicación. El widget `Locate` encuentra y se acerca a su ubicación después de que se hace clic en el botón.
En este ejercicio usará el widget `Locate` para encontrar y mostrar su ubicación en un mapa.