# Ensuring Web-accessibility

It is important to consistently work towards ensuring an inclusive web-experience by examining what barriers might prevent user access or interaction with the tools that we build and then taking steps to mitigate these points of contention. Here are a few steps towards ensuring that our work with Leaflet stays accessible. 

## Stay up to date

As with many digital tools, Leaflet is constantly developing new features and working on improving the innate accessibility of the product. Make sure that you are working with the [latest stable version](https://leafletjs.com/download.html) of the Leaflet library.

## Preserve useful defaults

As we explored some of the basic map options availabe in Leaflet, you may have noticed that keyboard navigation is enabled by default. If you are going to make changes to some of these defaults, be sure to consider the effects that this might have on your users.

## Alt lables

One of the options that you can pass to markers on your map is an alternate description or title. By passing an alternative title, we can ensure that our markers are also discernable to screen readers. Here is an example of how this is done:

```html
<script>
  var indePark = L.marker([39.950879, -75.150133], {alt: 'Independce National Historical Park'})
			.bindPopup('<h1>Independence National Historical Park</h1><p>This park is located in <b>Philadelphia</b> and encompases both <b>Independence Hall</b> and <b>the Liberty Bell</b>.</p>')
			.addTo(map);
</script>
```

Take a moment to add an alternative title to each of your markers.

## Hide decorative maps

If your map is purely decorative, like background images or videos, and not intended for user interaction, make sure that you hide these maps from assistive technologies.  This will avoid potential confusion for screen reader users and eliminate unnecessary tab stops for keyboard users. One way to achieve this is by using the HTML innert attribute polyfill in the ```<div>``` tag for your map.

```html
<body>
  <div id='decorative-map' inert></div>
  <script> ... </script>
</body>
```

## Accessibility testing

If possible, test your map using only your keyboard to navigate. Do the same with a screen reader. (You may find that you already have a screen reader pre-installed on your computer: Narrator on Windows, TalkBack on Android, VoiceOver on macOS and iOS).

There are also a variety of tools designed for testing the accessibility of different webpages and apps. Use these on your map. What works? What doesn't?

---

[<<< Previous](05-pop.md) | [Home >>>](https://github.com/sfritzell/Leaflet-Tutorial)
