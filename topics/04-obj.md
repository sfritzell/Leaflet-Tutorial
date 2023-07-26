# Adding Objects

Let's say that we want to draw someone's attention to specific points or areas on the map. We *could* simply set the center and zoom level of our map to focus on one point of interest, but it might be better to physically highlight points of interest on the map instead. 

Leaflet provides us with three ways of marking a specific point:

1. **Marker**: Leaflet provides a default blue marker, but you can also create a custom marker using a PNG image
2. **Circle Marker**: a circle with a fixed radius defined in *pixles*
3. **Circle**: a circle with a fixed radius defined in *meters*

For our purposes, we will stick with the default Leaflet Marker.

## Creating a Marker

In order to add a marker to a Leaflet map, we use the ```L.marker()``` function. This function creates a marker obejct which we can then add to the map using the ```.addTo()``` method, with which we are already familiar. To create our first marker, let's add a new variable object as ```script``` in the  ```body``` of our html document. A marker can't exist without a defined point, so let's pass the coordinates of the Independence National Historical Park to our function using the ```[lat, lng]``` format which we used earlier when initializing our map. 

```html
<script>
  var indePark = L.marker([39.950879, -75.150133]).addTo(map);
</script>
```

Save your file and then open it in your browser. Notice anything new?

Note that while it is possible to simply create a marker object using the ```L.marker().addTo()``` method without defining a new variable, doing so limits the sort of advanced methods which you can apply to your map later on. And let's be honest, defining a marker as a new variable makes our code a bit more human-readable. 

Use this same method to add at least two more markers to your map. An easy trick for obtaining geographic coordinates: search for an address or place in GoogleMaps and right click on the icon. This will pull up a box with coordinates that you can copy and paste for your own use. 

## Other Leaflet objects

Leaflet also allows for the creation of slightly more complex objects, such as lines and polygons, which are composed of several points. We won't go into too much detail here, but let's create a simple line to get a better idea of how such objects migth be created. 

Lines in Leaflet are created using the ```L.polyline()``` function. Because a line is composed of *at least* two points, it is essential to specifiy the coordinates of the points which our line should pass through. We do this by passing the function an array of ```[lat, lng]``` coordinate arrays. The function will interpret the first set of coordinates as the starting point of the line, and the final set of coordinates as the ending point of the line.

Adapt the following example to create a line between two of the Markers that you have already defined on your map.

```html
<script>
  var line = L.polyline([[39.950879, -75.150133], [40.102052, -75.446917]]).addTo(map);
</script>
```

To create a polygon, use the ```L.polygon()``` function and pass it an array of *at least* three ```[lat, lng]``` coordinate arryas. The function will create a line between the specified coordinates, progressing from first to last, and then an additional line connecting the first and last points.

---

[< Previous](03-mods.md) | [Next >](05-pop.md)
