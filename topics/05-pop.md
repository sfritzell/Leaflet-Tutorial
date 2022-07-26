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

Add this Popup to your map. Save your file and open it again in your browser. What do you notice? How do you interact with the Popup? Take a bit of time and define a few more Popups for points on your map. Remember that you can bind Popups to objects other than Markers!

## Adding a description 

Say that you wanted to add some content describing the whole of your map, rather than a single point. You can do this in Leaflet with a slightly more complex string of code to create a map legend or description panel. 

First we will create a new variable and define it with the function ```L.control()```, which will create a new Leaflet map control that we can then further specifiy using some HTML. We will also define the position of this new control on the screen.

```html
<script>
	var descrip = L.control({position: 'bottomleft'});
</script>
```

We want to fill our newly created control with a map description consisting of a few lines of text. (As with Popups, you can use basic HTML to style your text or to add links and images). To define the contents and behavior of our control, we will use the ```x.onAdd``` method, where x indicates the control defined by our variable. (This method essentially tells the control how to behave when it is added to the map using the ```x.addTo()``` operation). We will define our ```x.onAdd``` method as a function that creates a ```<div>``` and fills it with HTML.

```html
<script>
	var descrip = L.control({position: 'bottomleft'});
	descrip.onAdd = function() {
		let div = L.DomUtil.create('div', 'descrip');
		div.innerHTML =
			'<h1>About this Map</h1><hr>' + 
			'<p>This map displays parks near Philadelphia that</p>' +
			'<p> are sustained by the National Park Service.</p>' +
			'<h2>How to Use</h2>' +
			'<p>Click on a marker to learn more about a park.</p>';
		return div;
	};
	descrip.addTo(map);
</script>
```

In short, with the ```.onAdd``` method, we create a function that tells the computer "when the new control is added to the map, create a ```<div>``` and fill it with this stuff". Note how the name that we have set for our control gets used in this process to specificy precisely what the subject of this action should be. 

Finally, we need to add some CSS to provide our newly created description control with some basic styling. Here is one possibility:

```html
<style>
	.descrip {
      		width:  250 px;
      		font-size: 16px;
      		font-family: "Open Sans", Helvetica, sans-serif;
      		padding: 10px 14px;
      		background-color: #FFFFFF;
      		border-radius: 5px;
      		border: 5px solid #D3D3D3;
      	}
</style>
```

(Note that because the ```L.control``` method is used for creating *custom* controls without defaults, we must define some styling or the control won't appear on our map)

---

[<<< Previous](04-obj.md) | [Next >>>]()
