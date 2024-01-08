# MLKit VIN Scanner

[![Latest Stable Version](https://img.shields.io/npm/v/cordova-plugin-ia-mlkit-scanner.svg) ](https://npm-stat.com/charts.html?package=cordova-plugin-ia-mlkit-scanner)
[![Total Downloads](https://img.shields.io/npm/dt/cordova-plugin-ia-mlkit-scanner.svg)](https://npm-stat.com/charts.html?package=cordova-plugin-ia-mlkit-scanner)

Scan VINs using [Google MLKit](https://developers.google.com/ml-kit/vision/barcode-scanning). 

This plugin supports the `android` and `ios` platforms.

Modified slightly from original: it only accepts a decoded barcode if it has the 17 characters of a Vehicle Identification Number.

Also some android strings were added to get it to compile correctly.

## Installation

```
cordova plugin add cordova-plugin-ia-mlkit-scanner
```

If using Ionic:

```
ionic cordova plugin add cordova-plugin-ia-mlkit-scanner
```

## Usage

### Barcode Scanner

To call up the barcode scanner, refer to this example code:

```typescript
enum CameraFacing {
  BACK = 0,
  FRONT = 1
}

function onSuccess(barcode) {
  console.log("Success:" + barcode);
}

function onError(message) {
  console.log("Error:" + message);
}

window["MLKitBarcodeScanner"].scanBarcode(CameraFacing.FRONT, onSuccess, onError);
```

---

### Check Play Service Availability (ANDROID)

As this plugin is based on Google's MLKit, Play services is required for it to function correctly on Android devices. You can check if the host device has support, by calling **checkSupport**:

```javascript
function onSuccess(isSupported) {
  console.log("Has Support: " + isSupported);
}

function onError(message) {
  console.log("Error: " + message);
}

window["MLKitBarcodeScanner"].checkSupport(onSuccess, onError);
```
