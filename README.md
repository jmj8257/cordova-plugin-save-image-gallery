# Cordova saveImageGallery Plugin
![Platform](https://img.shields.io/badge/platform-android%20%7C%20ios%20%7C%20windows-lightgrey.svg)

본 플러그인은 (based on [agomezmoron/cordova-save-image-gallery](https://github.com/agomezmoron/cordova-save-image-gallery#readme)) base64 데이터를 png/jpg 이미지로 기기(iOS 사진 라이브러리, Android 갤러리 또는 Windows Phone 8 사진 앨범)에 저장할 수 있습니다.

## 변경사항
android api level 상승에 따른 디렉토리 접근 및 권한 설정 변경 

## Alerts

### WP8 limitations
In this fork, the Android and iOS implementation were adapted but the WP8 cannot save images in PNG or reducing the quality of the images.

## Usage (saveBase64Image)
Call the `window.imageSaver.saveBase64Image()` method using success and error callbacks and the passing the image's base64 in the options JSON:

### Methods
#### `window.imageSaver.saveBase64Image(options [,success, fail])`

Param       | Type       | Default           | Description
----------- | ---------- | ----------------- | ------------------
**options** | *object*   | \*see below       | options
**success** | *function* | **console.log**   | success callback
**fail**    | *function* | **console.error** | fail callback

#### Available options

##### `data`
Base64 input String.

##### `prefix`
Saved file name prefix. Only works in Android and WP8.

**Default**: "img_"

##### `mediaScanner`
Android Media Scanner after file creation enabled or not. Only works in Android!

**Default**: true

##### `format`
Format to save the image. Allowed values 'JPG' and 'PNG'. Only supported for Android and iOS. Currently this option is ignored on Windows implementation.

**Default**: JPG

##### `quality`
Quality of the saved image. If you want to reduce the quality of the image, you are allow to do it. The value should be a number from 1 to 100. Only supported for Android and iOS. Currently this option is ignored on Windows implementation.

**Default**: 100

### Example

```javascript
function onDeviceReady() {
    var params = {data: base64String, prefix: 'myPrefix_', format: 'JPG', quality: 80, mediaScanner: true};
    window.imageSaver.saveBase64Image(params,
        function (filePath) {
          console.log('File saved on ' + filePath);
        },
        function (msg) {
          console.error(msg);
        }
      );
}
```

## Usage (removeImageFromLibrary)
Call the `window.imageSaver.removeImageFromLibrary()` method using success and error callbacks and the passing the image URL in the options JSON:

### Methods
#### `window.imageSaver.removeImageFromLibrary(options [,success, fail])`

Param       | Type       | Default           | Description
----------- | ---------- | ----------------- | ------------------
**options** | *object*   | \*see below       | options
**success** | *function* | **console.log**   | success callback
**fail**    | *function* | **console.error** | fail callback

#### Available options

##### `data`
File path input String.

### Example

```javascript
function onDeviceReady() {
    var params = {data: "/data/data/test.png"};
    window.imageSaver.removeImageFromLibrary(params,
        function (filePath) {
          console.log('File removed from ' + filePath);
        },
        function (msg) {
          console.error(msg);
        }
      );
}
```

## Author
- [J.Minjun](http://github.com/jmj8257)
