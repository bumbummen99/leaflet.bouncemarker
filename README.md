# Leaflet Bouncemarker

This is a fork of the [maximeh's BounceMarker](https://github.com/maximeh/leaflet.bouncemarker/) plugin.

This little plugin for [Leaflet](http://www.leafletjs.com) will make a Marker
bounce when you add it on a map on whenever you want it to.

Watch the [demo](http://maximeh.github.com/leaflet.bouncemarker/).

## Install

Use the following command in order to install the latest compatible version of the package.

```console
npm i --save @skyraptor/leaflet.bouncemarker
```

# Usage

Let's consider we have a Leaflet map:

```javascript
var map = L.map('map');
L.tileLayer('http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: 'Map data &copy; <a href="http://www.osm.org">OpenStreetMap</a>'
}).addTo(map);
```

## Enable

In order to enable the plugin for a marker the bouncemarker option has to be set to true.

```javascript
L.marker([48.85, 2.35], {
    bouncemarker: true,
}).addTo(map);
```

## Bounce onAdd

Make your marker bounce when you add them to a map.

```javascript
L.marker([48.85, 2.35], {
    bouncemarker: true,
    bounceOnAddOptions: {},
    bounceOnAddCallback: callback,
}).addTo(map);
```

Or exclude it from OnAdd bouncing:

```javascript
L.marker([48.85, 2.35], {
    bouncemarker: true,
    bounceOnAdd: false,
}).addTo(map);
```

# Options

### bouncemarker (boolean)

If true, the plugin will be enabled for the marker and it will be able to bounce. Default to false.

### bounceOnAdd (boolean) (optional)

If true, your marker will bounce when added to the map. Default to true.

### bounceOnAddOptions (object) (optional)

* duration (integer) (Default: 1000)

    The duration of the animation in milliseconds.

* height (integer) (Default: top_y)

    The height (in pixel) at which the marker is "dropped".
    The default is the top point on the y axis of the Marker.

* loop (integer) (Default: 1)

    The number of times the animation should play.
    -1 is a special value for infinite loop.

### bounceOnAddCallback (function) (optional)

If you specify the callback parameter, it will be called at the end of the
animation.

**Example:**
```javascript
L.marker([48.85, 2.35], {
    bouncemarker: true,
    bounceOnAddOptions: {
        duration: 500, 
        height: 100, 
        loop: 2
    },
    bounceOnAddCallback: () => {
        console.log("done");
    }
}).addTo(map);
```

## bounce

Make a marker bounce at anytime you wish.

```javascript
bounce(options, callback);
```

**Example:**
```javascript
marker = new L.Marker([48.85, 2.35], {bounceOnAdd: true}).addTo(map);
marker.on('click', event => {
    marker.bounce({
        duration: 500, 
        height: 100
    });
});
```

### options (object) (optional)

* duration (integer) (Default: 1000)

    The duration of the animation in milliseconds.

* height (integer) (Default: top_y)

    The height (in pixel) at which the marker is "dropped".
    The default is the top point on the y axis of the Marker.

* loop (integer) (Default: 1)

    The number of times the animation should play.
    -1 is a special value for infinite loop.

### callback (function) (optional)

If you specify the callback parameter, it will be called at the end of the
animation.

**Example:**
```javascript
marker.bounce({
  duration: 500,
  height: 100
}, () => {
  console.log("done");
});
```

## stopBounce

Will stop the animation when called; the marker will be positionned at it's
destination.