# openlayer_wms_map
A wms map created using  Openlayers and Geoserver
# Motive
The main motive of this program was to make the program as readable, easy and short as possible.
# requirements
# Geoserver
* download geoserver (you may download it any way you like), from the official link or from this [link](https://drive.google.com/file/d/1PkcyuIdH2vNFGb9rx1GofMHTDDhvzOx_/view?usp=sharing)(this is the custom setup made by me.
* Than, when you will install leave the default settings as it is. 
![s](https://github.com/pranayteaches/openlayer_wms_map/blob/master/process/Installation.PNG)
* after the installation go to the search bar of your operating system and search for "start geoserver"., if it is there click on it and your server will be started. Else, try reinstalling itand repeat the process mentioned.
* open your browser and type http://localhost:8080/geoserver/web/ a webportal of geo server will apear.
* Just login using    username:- admin     password:- geoserver
* a welcome screen of geoserver will open.
![asd](https://github.com/pranayteaches/openlayer_wms_map/blob/master/process/login.PNG)
* click on the "workspace" in the left corner and "add a new workspace" by giving it a name and any url(not needs to be real). fr ex: pranay
* after creating click on the "stores" above the "workspace" in the data panel(left side). and add a new shape file(first option).
![a](https://github.com/pranayteaches/openlayer_wms_map/blob/master/process/3.jpg)
* download any shape file like a file. For ex. indian states.
* in "stores" in the workspace choose the workspace you created.
* below give any name to it, you may leave the description empty.
* at last browse the directry of shapefiles, for ex ``` D:\india```, and than click on save.
* after click on the "layers" above "stores". than add new layer. than choose the name of shapefile you uploaded in add layers from.
![ds](https://github.com/pranayteaches/openlayer_wms_map/blob/master/process/stores.PNG)
* than click on publish.
* first of all give a name to your layer and than title, leave the other things as it is and than scroll down to "Bounding Boxes".
* After that you just need to click on "compute from data", for the "native bounding box" and than below for "lat/long bounding box", click on "compute from native bounds".
![asd](https://github.com/pranayteaches/openlayer_wms_map/blob/master/process/layers.PNG)
* than click on save, congratulations your WMS layer has been created.
# Open Layers
* download node.js and install openlayers by:-
``` npm intall ol ```
* download any ide (vs code) (personal prefrence).
* install VsCode plugins
* create a new html file.
* and just copy and paste the code I mentioned.
* congratulations you are all set.
# how to use the code
* First you have to start your geoserver.
* Then you may just open the html file in the chrome or start it using VsCode.
* If you wnat to use it directly just copy and paste the link below.
 http://localhost:8080/geoserver/wms/reflect?format=application/openlayers&layers=pranay:IND_pj&CQL_FILTER=NAME_1+IN+(%27Uttaranchal%27)
# why use my code
As, it is very simple and updated, and also very small, which saves time.
# how is it so Small while other codes of same are verybig.
First of all every things not worked for me right, it took me 2 days to research about open layers and geoserver but nothing works for me. Then suddenly when I was just reading Geoserver's 2.17.x documentation I came to know about a new feature." WMS Reflector".
# WMS Reflector
What WMS reflector do is it creates an open layer's layer or just make its image file.
WMS reflector has a great advantage in some occasions., as Standard WMS requests can be quite long and verbose. Typing into a browser, or HTML editor, can be quite cumbersome and error prone. The WMS Reflector solves this problem nicely by using good default values for the options that you do not specify.
For instance the following, which returns an OpenLayers application with an 800x600 image set to display the feature for ```
Russia:Asia_Russia ```
```
<!DOCTYPE html>
<html lang="en">
    <a href="http://localhost:8080/geoserver/wms/reflect?format=application/openlayers&layers=pranay:IND_pj">
      <img src="http://localhost:8080/geoserver/wms/reflect?layers=pranay:IND_pj&width=400"/>
      </a>
 </html>
 ```
# Code Difference(WMS(Reflector) VS WMS(Standard)) 
Here I will just provide you the code with the same function but one with (WMS(Reflector)) and one with (WMS(Standard)) 
They Display the image set to display the feature for ``` pranay:IND_pj ```
(NOTE: Both code are made in a contribution to OSGeo)
### (REFRENCE: WMS(std) = WMS Standard, WMS(ref) = WMS Reflector)
### WMS Reflector 
WMS(ref) = (pros) small and simple code .With ease understand

WMS(ref) = (cons) as it is only used to preview, so only one layer can be shown i.e you may not show multiple layers and even base layer also can't be added
### WMS Standard
WMS(std) = (pros) you may add many layers and functionality

WMS(std) = (cons it is time consume and the code needs to be long and elongated
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

  

