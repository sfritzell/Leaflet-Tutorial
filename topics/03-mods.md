# Modifying the Base Map

## More map options

When initializing our map, we used the options ```center``` and ```zoom``` to define the center point of our map using latitudinal and longitudinal coordinates at a particular level of magnifiation. These are called "state options" because they define the particular state of the map when it loads. There are many map options available in Leaflet that define not just the state of the map, but also ways of interacting with and navigating it. 

Here are a few additional map options that you might find useful. Spend a bit of time trying them out and think about how they affect the default settings of the map:

| Option Name | Type | Default Setting | Description |
| ----------- | ---- | --------------- | ----------- |
| zoomControl | Boolean | true | A control option; defines whether a zoom control is added to the map by default |
| dragging | Boolean | true | An interaction option; defines whether the map is draggable with the mouse or by touch |
| center | LatLng | undefined | A map state option; defines the initial geographic center of the map |
| zoom | Number | undefined | A map state option; defines the initial map zoom level |
| minZoom | Number | undefined | A map state option; defines the minimum zoom level of the map; if not specified, the lowest of the minZoom options for the gridLayer or tileLayer of the map will be used instead |
| maxZoom | Number | undefined | A map state option; defines the maximum zoom level of the map; if not specified, the highest of the maxZoom options for the gridLayer or tileLayer of the map will be used instead |
| keyboard | Boolean | true | A keyboard navigation option; defines whether a user can navigate the map using keyboard arrows and + - keys |
| scrollWheelZoom | Boolean | true | A mouse wheel option; defines whether a user can use the mousewheel to zoom on the map |

## Adding a WMS layer

Say that you want your map to display topographical information beyond what is shown in your basic geographical background. One way to do this is to use a WMS, or Web Map Service, which is a popular way of publishing maps by professional GIS software. In format, WMS is similar to map tiles, but it is defined a little differently under-the-hood, so we need to add WMS layers using a slightly different syntax in Leaflet. 

```html
<!-- Head content is here -->
<body>
  <!-- Other body content is here -->
  <script>
    var wmsLayer = L.tileLayer.wms().addTo(map);
  </script>
</body>
```

As when we created our map variable, the operation ```L.tileLayer.wms()``` requires two arguments (and, if you look at the content that we copy-pasted for our basemap, you should notice that the L.tileLayer() operation uses similar syntax!). The first is a URL string that directs to the base WMS. The second consists of your ```wmsOptions```, of which one is required: ```layers```.  Let's add a WMS representing meteorological radar data for the United States with the following:

```html
<!-- Head content is here -->
<body>
  <!-- Other body content is here -->
  <script>
    var wmsLayer = L.tileLayer.wms('https://mesonet.agron.iastate.edu/cgi-bin/wms/nexrad/n0q.cgi?', {
      layers: 'nexrad-n0q-900913',
      format: 'image/png',
      transparent: true
    }).addTo(map);
  </script>
</body>
```

Save your file and open the map in your browser.  What do you notice?

---

[< Previous](02-prep.md) | [Next >](04-obj.md)
