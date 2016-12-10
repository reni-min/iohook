# iohook
Node.js global native keyboard and mouse listener.  
This module can handle keyboard and mouse events via native hooks.  

## OS Support
Already tested in:
- Ubuntu 16.04
- macOS Sierra 10.12
- Windows (NOT TESTED YET)

## Installation
This module use native library libuiohook and require some installed packages

`npm install iohook --save`

### Ubuntu 16
- `sudo apt install libx11-dev libxtst-dev libxt-dev libx11-xcb-dev`
- `sudo apt install libxkbcommon-dev libxkbcommon-x11-dev`
- `npm install iohook --save`

### macOS
- `brew install cmake autoreconf libtool pkg-config`
- `npm install iohook --save`

## Usage
Module is pretty simple for use. There is example:  

```javascript
'use strict';
const ioHook = require('./index.js');

ioHook.on("mousemove", event => {
  console.log(event);
  /* You get object like this
    {
      type: 'mousemove',
      x: 700,
      y: 400
    }
   */
});

//Register and stark hook
ioHook.start();
```

### Available events

### keypress
Calls when user press and release a key. Event contain next object:  
`{keychar: 'f', keycode: 19, rawcode: 15, type: 'keypress'}`

### keydown
Calls when user press a key. Event contain next object:  
`{ keychar: 'd', keycode: 46, rawcode: 8, type: 'keydown' }`

### keyup
Calls when user release a key. Event contain next object:  
`{keychar: 'f', keycode: 19, rawcode: 15, type: 'keup'}`

### mouseclick
Calls when user click mouse button. Event contain next object:  
`{ button: 1, clicks: 1, x: 545, y: 696, type: 'mouseclick' }`

### mousedown
Calls when user press and release a key. Event contain next object:  
`{ button: 1, clicks: 1, x: 545, y: 696, type: 'mousedown' }`

### mouseup
Calls when user press and release a key. Event contain next object:  
`{ button: 1, clicks: 1, x: 545, y: 696, type: 'mouseup' }`

### mousemove
Calls when user press and release a key. Event contain next object:  
`{ button: 0, clicks: 0, x: 521, y: 737, type: 'mousemove' }`

### mousedrag
Calls when user press and release a key. Event contain next object:  
`{ button: 0, clicks: 0, x: 373, y: 683, type: 'mousedrag' }`

### mousewheel
Calls when user press and release a key. Event contain next object:  
`{ amount: 3, clicks: 1, direction: 3, rotation: 1, type: 'mousewheel', x: 466, y: 683 }`

## Known issues
In some cases, most often when you make mouse moves or keyboard events very fast,
module crash with "Segmentation fault: 11". Looks like it is problem in my native implementation,
but I still can't find a problem. Will be happy if somebody helps with it.

## Credits
Thanks for libuiohook project!