# Working with Popups

While Markers and other objects in Leaflet are great for singling out specific points of interest, they don't provide much information on their own about why these points are important. This is where Popups come into play. 

By default, Popups are small windows which can be opened and closed by the user to get more information about different features on the map. This information could be your standard set of metadata, a title, description, or even an image. While we will be defining the popup content for one point at a time, when working with large datasets it is typically best to batch-define your popups for a standarized look accross all of your points. 

## Adding Popups

Popups are added to a Leaflet map using the method ```x.bindPopup()```, where x stands for a Leaflet object like a Marker, Line, or Polygon. This method accepts a text string which expresses the Popup content. You can use HTML tags within the string to add some basic styling, make lists, create links, add images, etc. For more advanced styling, you should create a new CSS class for your Popups in the ```<head>``` of your HTML document. 

Here's how we might define a basic Popup for our Marker object at Philadelphia's Independence National Historical Park:

```html
<script>
  var indePark = L.marker([39.950879, -75.150133])
		.bindPopup('<h1>Independence National Historical Park</h1><p>This park is located in <b>Philadelphia</b> and encompases both <b>Independence Hall</b> and <b>the Liberty Bell</b>.</p>')
		.addTo(map);
</script>
```

Note that this entire expression could be written as a single line of code. Because humans are not machines, however, it is best to split this code into multiple lines, especially if you ever plan to modify your Popup content!

---

[<<< Previous](04-obj.md) | [Next >>>]()
