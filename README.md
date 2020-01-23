c

# Code Difference(WMS(Reflector) VS WMS(Standard)) 
Here I will just provide you the code with the same function but one with (WMS(Reflector)) and one with (WMS(Standard)) 
They Display the image set to display the feature for ``` pranay:IND_pj ```
(NOTE: Both code are made in a contribution to OSGeo)
### WMS(Standard)
```
<!doctype html>
<html lang="en">
  <head>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.1.1/css/ol.css" type="text/css">
    <style>
      .map {
        height: 400px;
        width: 100%;
      }
    </style>
    <script src="https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.1.1/build/ol.js"></script>
    <title>OpenLayers By Pranay</title>
  </head>
  <body>
    <h2>Pranay Map</h2>
    <div id="map" class="map"></div>
    <script type="text/javascript">
      var map = new ol.Map({
        target: 'map',
        layers: [
          new ol.layer.Tile({
            source: new ol.source.OSM()
          }),
          new ol.layer.Tile({
    				source: new ol.source.TileWMS({
        		url: 'http://localhost:8080/geoserver/pranay/wms?',
       			params: {
              'LAYERS': 'pranay:IND_pj',
              'VERSION': '1.1',
              'FORMAT': 'image/png',
              'TILED': true
        		},
    			})
				})
        ],
        view: new ol.View({
          center: ol.proj.fromLonLat([-88, 35]),
          zoom: 4
        })
      });
    </script>
  </body>
</html> 
```
### Code with WMS(Reflector)
```
<!DOCTYPE html>
<html lang="en">
    <a href="http://localhost:8080/geoserver/wms/reflect?format=application/openlayers&layers=pranay:IND_pj">
      <img src="http://localhost:8080/geoserver/wms/reflect?layers=pranay:IND_pj&width=400"/>
      </a>
 </html>
 ```
### Results
You may clearly see the difference in the code and in this case one would surely choose the WMS(Reflector) as the best option.
# how to use the code
* First you have to start your geoserver.
* Then you may just open the html file in the chrome or start it using VsCode.
* If you wnat to use it directly just copy and paste the link below.
http://localhost:8080/geoserver/wms/reflect?format=application/openlayers&layers=pranay:IND_pj&width=800
# why use my code
As, it is very simple and updated, and also very small, which saves time.
# how is it so Small while other codes of same are verybig.
First of all every things not worked for me right, it took me 2 days to research about open layers and geoserver but nothing works for me. Then suddenly when I was just reading Geoserver's 2.17.x documentation I came to know about a new feature." WMS Reflector".
# WMS Reflector
What WMS reflector do is it creates an open layer's layer or just make its image file.

# Code Explaination
* First of all i described that it is a HTML file.
* in this line ``` <a href="http://localhost:8080/geoserver/wms/reflect?format=application/openlayers&layers=pranay:IND_pj"> ```
``` <a href=""> ``` tells that it is a web link.
``` "http://localhost:8080/geoserver/wms/" ``` is the localserver address
``` reflect ``` returns it 
``` ?format=application/openlayers&layer ``` is to describe that it is openlayer based application format.
``` pranay:IND_pj ``` workspace and layer for diasplaying. Should be entered in following manner
                              ``` {workspace name}:{layer name"} ```
* in the last line ``` <img src="http://localhost:8080/geoserver/wms/reflect?layers=pranay:IND_pj&width=400"/> ```
it just tells that we just have to take an image of the src(source code) which is the web link or the local server link.
* Congrats you Geoserver layer can be opened in the open layer
* just same the HTML file and open it(make sure your geoserver is not stopped)
* A image will appear of the shapefile you created and uploaded on Geoserver.
* click on it to view the "open layers view".
* You may also give a it a pre existing Height and width. by using {&, width, height)
for ex:- ```  <img src="http://localhost:8080/geoserver/wms/reflect?layers=pranay:IND_pj&width=400"height="169" width="400"/> ```
Image Of the Code written in VsCode
![fesk](https://github.com/pranayteaches/openlayer_wms_map/blob/master/process/Vscode_html.PNG)
# the images for the process is in the process folder don't forget to check it out
# A ScreenShot Of The layer.
![sad](https://github.com/pranayteaches/openlayer_wms_map/blob/master/process/map_image.PNG)
Thank you, 
That's all for the tutorial

  

