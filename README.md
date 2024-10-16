# capacitor-nfc

Capacitor plugin for reading NFC tags

### Android

## Requires
`@capacitor/core`

## Install
Add the following to your package.json -> dependencies
```json
"t4i-capacitor-nfc": "github:time4innovation/t4i-capacitor-nfc"
```

## Usage in JavaScript
Import the following
```javascript
import { Plugins } from "CapacitorCore";
const { Time4InnovationNfc } = Plugins;
```
You might include CapacitorCore as the following in ember-cli-build.js
```javascript
'use strict';

const EmberApp = require('ember-cli/lib/broccoli/ember-app');
const ENV = require('./config/environment.js');

module.exports = function (defaults) {
	 // CAPACITOR -> CORE
    app.import('node_modules/@capacitor/core/dist/index.cjs.js', {
        using: [{ transformation: 'cjs', as: 'CapacitorCore' }],
    });
}
```

Implement the following method and call it where you need to read an RFID-Tag.
```javasacript
nfcInit() {
    // Initialize the NFC detection
    Time4InnovationNfc.initializeNFC()
        .then((result) => {
            // Now tagInfo is part of JSObject
            console.log("NFC Tag Information:", result.tagInfo);
        })
        .catch((error) => {
            console.error("Error initializing NFC:", error);
        });
}
```

## Manifest.xml

<uses-permission android:name="android.permission.NFC" />
<uses-feature android:name="android.hardware.nfc" android:required="true"/>
