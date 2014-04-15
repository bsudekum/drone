Everything Drone related
------------------------ 

# Flights
* [Polo Fields](https://github.com/rsudekum/drone/tree/gh-pages/polofields)
* [Corona Heights](https://github.com/rsudekum/drone/tree/gh-pages/corona-heights)
* [Bernal Heights](https://github.com/rsudekum/drone/tree/gh-pages/bernal)

# Processing 
Here is an end to end walkthrough showing how to process drone imagery into maps and then share it online, all using imagery we collected on a recent flight with the [3D Robotics](http://3drobotics.com/landing-product/) team and their [Aero](https://store.3drobotics.com/products/3DR-Aero) drone.

![](https://farm4.staticflickr.com/3823/13584148833_dd80838902_b.jpg)

### Piecing together the imagery
The first step in creating a sharable map is stitching the images into one single image. Software like [PhotoScan](http://www.agisoft.ru/products/photoscan/standard/) and [Pix4D](http://pix4d.com/) make this really easy for you. Here we are going to use Pix4d. Simply import images, select GeoTIFF as output option and let it run. 

![](https://i.cloudup.com/iHqv1dgZ8I.gif)
*Adding flight data to Pix4D*

### Rendering and uploading the map
After Pix4D has completed processing the imagery, import the resulting GeoTiff into [TileMill](https://www.mapbox.com/tilemill/), our open source map design studio. In TileMill follow these steps to make sure your imagery looks great:

* To remove the black border from around the imagery, set `nodata=0`. Usually this value is `0` but the value can vary and can be checked in [QGIS](http://www.qgis.org/en/site/)
* Increase the `raster  -mesh-size`. This will make sure re-projection artifacts do not appear
* Set `map-background:transparent`. This will make the map look better when overlaid on other imagery
* Set `raster-scaling:lanczos;`. This will ensure your imagery is nice and clear. It will also increase your processing time, but it's worth it.

Once all TileMill parameters are set, upload the imagery to Mapbox.com by clicking `Export` ---> `Upload`.

![](https://farm8.staticflickr.com/7366/13584023605_64302a6223_b.jpg)
![](https://farm6.staticflickr.com/5500/13584395174_080756d7a3_b.jpg)

*[Final Result](https://www.mapbox.com/bites/00029/map/#17/37.87210/-122.31840) on top of [Mapbox Satellite](https://www.mapbox.com/tour/#section-satellite) once uploaded to Mapbox.com and styled with mapbox.js.*

### Sharing the map
Once uploaded to Mapbox.com, you can optionally combine the imagery with [Mapbox Streets](http://mapbox.com/tour/#section-streets), [Mapbox Satellite](http://mapbox.com/tour/#section-satellite) or any other layer you have uploaded previously. From there it is easy to share the map either [by its URL](https://a.tiles.mapbox.com/v3/bobbysud.map-l4i2m7nd,bobbysud.57bymn29.html?secure#18/37.87190/-122.31861) or as a Youtube-like embed code. To extend the map further use [mapbox.js](https://www.mapbox.com/mapbox.js/). For instance, the example above is a simple [time line built with mapbox.js](https://www.mapbox.com/bites/00029/map/#17/37.87210/-122.31840).
