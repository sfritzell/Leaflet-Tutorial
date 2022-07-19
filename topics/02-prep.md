# Setting up the Map

Before we begin building a Leaflet map, we first need to build a space to house our JavaScript, which is best done with a basic HTML document.

## A basic HTML framework

Using a text-editor of your choice (VSCode, Sublime, Atom, etc.), create an empty text file and name it ```index.html```. Next add the standard components of a simple HTML document. For now you can think of these as placeholders.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Leaflet Web Map</title>
    <!-- More content will go here -->
</head>
<body>
    <!-- More content will go here -->
</body>
</html>
```

Save the file and open it in your browser. Right now the page is empty, so let's return to our editor and add a few more items to provide it with more shape.

## Referencing Leaflet files

Frist we need to include a reference to the Leaflet CSS and JavaScript files so that our document can access those expansive collections of code. To do this we need to place a ```<script>``` element that refers to the relevant files in our HTML document. Best practice dictates that scripts for loading libraries (like Leaflet) should be placed in the ```<head>``` of a document, which means that the script will be loaded before any visible elements of the page are loaded.

When loading an external script file using the ```<script>``` element we use the ```src``` attribute to specify the file location. This could be a path to a local file saved on your computer, or the URL of a web hosted file. Navigate to the [Leaflet Download page](https://leafletjs.com/download.html) to get a sense of the different options for hosting and referencing the Leaflet library. For this tutorial we will use a remote script. 

```html
<head>
  <title>Leaflet Web Map</title>
  <script src="https://unpkg.com/leaflet@1.8.0/dist/leaflet.js" 
          integrity="sha512-BB3hKbKWOc9Ez/TAwyWxNXeoV9c1v6FIeYiBieIWkpLjauysF18NzgR1MBNBXf8/KABdlkX68nAhlwcDFLGPCQ==" 
          crossorigin="">
  </script>
</head>
```

Note that placing a script in the ```<head>``` does carry the risk of causing the page to load slowely if the referenced script is particuarly large. Leaflet, like most JavaScript libraries, is fairly small, so there is no noticable delay.

Many JavaScript libraries consist of a single ```.js``` file, but Leaflet is slightly more complex and is built on a CSS file in addition to its JavaScript file. CSS files should always be referenced with a ```<link>``` element before the reference to the JavaScript file. Note that the CSS file can be hosted locally, just like the JavaScript file, but we will be using a remote script for this tutorial.


```html
<head>
  <title>Leaflet Web Map</title>
  <link rel="stylesheet" 
        href="https://unpkg.com/leaflet@1.8.0/dist/leaflet.css" 
        integrity="sha512-hoalWLoI8r4UszCkZ5kL8vayOGVae1oxXe/2A4AO6J9+580uKHDO3JdHb7NzwwzK5xr/Fs0W40kiNHxM9vyTtQ==" crossorigin="" 
        />
  <script src="https://unpkg.com/leaflet@1.8.0/dist/leaflet.js" 
          integrity="sha512-BB3hKbKWOc9Ez/TAwyWxNXeoV9c1v6FIeYiBieIWkpLjauysF18NzgR1MBNBXf8/KABdlkX68nAhlwcDFLGPCQ==" 
          crossorigin="">
  </script>
</head>
```

In addition to its CSS and JavaScript files, the Leaflet library also consists of a handful of image files which are used to display elements on a map. Because we are already referencing remote CSS and JavaScript files in this tutorial, we don't need to do anything else to gain access to these image files - these images live in the same place as the files that we are already referencing. If you are working with a locally hosted version of Leaflet, however, you will need to create an ```images``` directory within the directory where the CSS file is also located.

## Creating and styling the map

Now that we have created references to the Leaflet library, we can go ahead and create some space for the web map to exist within our basic HTML framework. We can do this by adding a ```<div>``` element within the ```<body>``` of the HTML, which creates space used to hold the interactive map. 

```html
<body>
    <div id="map"></div>
</body>
```

You can think of a ```<div>``` element as something which collects differing pieces of content into a single group. By adding an ```id``` attribute to our ```<div>``` tag, we can better refer to this unified group in CSS or JavaScript code. 

We also need to define the basic visual structure of the map, which we will do by adding a bit of CSS within a ```<style>``` element in the ```<head>``` of our HTML (below the ```<title>```, ```<link>```, and ```<script>``` tags). The example below is for a full-screen map.

```html
<head>
  <style>
      body {
        padding: 0;
        margin: 0;
      }
      
      html, body, #map {
        height: 100%;
        width: 100%;
      }
  </style>
</head>
```

It is possible, and, in fact, preferred to create a seperate CSS file and then add a reference to that file with a ```<link>```, much like we did with the Leaflet CSS file, but since we aren't adding too much additional styling to our page, the use of *embedded* CSS isn't too much of a problem.

## Initializing the map

...

---

[<<< Previous](01-leaflet.md) | [Next >>>]()
