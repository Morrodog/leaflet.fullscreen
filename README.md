Fork Notes
===========
This has been forked to export a function that mutates the given `L` argument to add the fullscreen functionality.
Used like so:
```
import initializeLeafletFullscreen from 'leaflet.fullscreen'

// `L` defined elsewhere
initializeLeafletFullscreen(L);

// Now it should be possible to use it as described in the original documentation below.
```

Leaflet.Control.FullScreen
============

What ?
------

Simple plugin for Leaflet that adds fullscreen button to your maps.

Inspired by http://elidupuis.github.com/leaflet.zoomfs/

Use the native javascript fullscreen API with help of https://github.com/sindresorhus/screenfull.js

Released under the MIT License http://opensource.org/licenses/mit-license.php

How ?
------

Include Control.FullScreen.js and Control.FullScreen.css in your page:

``` html
 <link rel="stylesheet" href="Control.FullScreen.css" />
 <script src="Control.FullScreen.js"></script>
```

Add the fullscreen control to the map:

``` js
var map = new L.Map('map', {
  fullscreenControl: true,
  fullscreenControlOptions: {
    position: 'topleft'
  }
});
```

If your map has a zoomControl the fullscreen button will be added at the bottom of this one.

If your map doesn't have a zoomControl the fullscreen button will be added to topleft corner of the map (same as the zoomControl).

If you want to use the plugin on a map embedded in an iframe, don't forget to set `allowfullscreen` attribute on your iframe.

__Events and options__:

``` js
// create a fullscreen button and add it to the map
L.control.fullscreen({
  position: 'topleft', // change the position of the button can be topleft, topright, bottomright or bottomleft, default topleft
  title: 'Show me the fullscreen !', // change the title of the button, default Full Screen
  titleCancel: 'Exit fullscreen mode', // change the title of the button when fullscreen is on, default Exit Full Screen
  content: null, // change the content of the button, can be HTML, default null
  forceSeparateButton: true, // force separate button to detach from zoom buttons, default false
  forcePseudoFullscreen: true, // force use of pseudo full screen even if full screen API is available, default false
  fullscreenElement: false // Dom element to render in full screen, false by default, fallback to map._container
}).addTo(map);

// events are fired when entering or exiting fullscreen.
map.on('enterFullscreen', function(){
  console.log('entered fullscreen');
});

map.on('exitFullscreen', function(){
  console.log('exited fullscreen');
});

// you can also toggle fullscreen from map object
map.toggleFullScreen();
```

__Tips for typescript environments__:

Installation
```
npm i leaflet.fullscreen
npm i screenfull
npm i -D @types/leaflet.fullscreen
```

Usage
```
import * as leaflet from 'leaflet';
import 'leaflet.fullscreen';

@Component({
    :
})
export class AppComponent implements AfterViewInit {
  private map: leaflet.Map;
  private mapOptions: leaflet.MapOptions = {
    :
    fullscreenControl: true,
    fullscreenControlOptions: {
      position: 'topleft'
    }
  } ;

  ngAfterViewInit(): void {
    this.map = new leaflet.Map('map', this.mapOptions);
  }
    :
}
```

Usage In React using react-leaflet
```
import React from "react";
import L from "leaflet";
import {MapContainer} from "react-leaflet";
import "leaflet.fullscreen/Control.FullScreen";
import "leaflet.fullscreen/Control.FullScreen.css";

export default function MyMap(){
 return (
  <MapContainer 
    .....
    whenCreated={map=>{
        L.control.fullscreen({
                position: 'topleft', // change the position of the button can be topleft, topright, bottomright or bottomleft, default topleft
                title: 'Show me the fullscreen !', // change the title of the button, default Full Screen
                titleCancel: 'Exit fullscreen mode', // change the title of the button when fullscreen is on, default Exit Full Screen
                content: null, // change the content of the button, can be HTML, default null
                forceSeparateButton: true, // force separate button to detach from zoom buttons, default false
                forcePseudoFullscreen: true, // force use of pseudo full screen even if full screen API is available, default false
                fullscreenElement: false // Dom element to render in full screen, false by default, fallback to map._container
              }).addTo(map);
    }}
   >
   .....
   </MapContainer>
 );
}

```

Where ?
------

Source code : https://github.com/brunob/leaflet.fullscreen

Downloads : https://github.com/brunob/leaflet.fullscreen/releases

Demo : https://brunob.github.io/leaflet.fullscreen/
