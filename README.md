ImagePicker (Forked version from https://github.com/nguyenhoanglam/ImagePicker)
========

A simple library that allows you to select images from the device library or directly from the camera.

[![](https://jitpack.io/v/alokvnair/ImagePicker.svg)](https://jitpack.io/#alokvnair/ImagePicker)

Download
--------

Add it in your root build.gradle at the end of repositories
```java
allprojects {
    repositories {
        ...
        maven { url "https://maven.google.com" }
        maven { url "https://jitpack.io" }
    }
}
```

Add the dependency
```java
dependencies {
    implementation 'com.github.alokvnair:ImagePicker:1.3.4'
}
```

You NEED to migrate your project to support AndroidX by add following lines on gradle.properties file:
```java
android.useAndroidX=true
android.enableJetifier=true
```

Usage
--------

### Start ImagePicker
```java
ImagePicker.with(this)                         //  Initialize ImagePicker with activity or fragment context
           .setToolbarColor("#212121")         //  Toolbar color
           .setStatusBarColor("#000000")       //  StatusBar color (works with SDK >= 21  )
           .setToolbarTextColor("#FFFFFF")     //  Toolbar text color (Title and Done button)
           .setToolbarIconColor("#FFFFFF")     //  Toolbar icon color (Back and Camera button)
           .setProgressBarColor("#4CAF50")     //  ProgressBar color
           .setBackgroundColor("#212121")      //  Background color
           .setCameraOnly(false)               //  Camera mode
           .setMultipleMode(true)              //  Select multiple images or single image
           .setFolderMode(true)                //  Folder mode
           .setShowCamera(true)                //  Show camera button
           .setFolderTitle("Albums")           //  Folder title (works with FolderMode = true)
           .setImageTitle("Galleries")         //  Image title (works with FolderMode = false)
           .setDoneTitle("Done")               //  Done button title
           .setLimitMessage("You have reached selection limit")    // Selection limit message
           .setMaxSize(10)                     //  Max images can be selected
           .setSavePath("ImagePicker")         //  Image capture folder name
           .setSelectedImages(images)          //  Selected images
           .setAlwaysShowDoneButton(true)      //  Set always show done button in multiple mode
           .setRequestCode(100)                //  Set request code, default Config.RC_PICK_IMAGES
           .setKeepScreenOn(true)              //  Keep screen on when selecting images
           .start();                           //  Start ImagePicker    
```

### Receive images

```java
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    if (requestCode == Config.RC_PICK_IMAGES && resultCode == RESULT_OK && data != null) {
        ArrayList<Image> images = data.getParcelableArrayListExtra(Config.EXTRA_IMAGES);
        // do your logic here...
    }
    super.onActivityResult(requestCode, resultCode, data);  // You MUST have this line to be here
                                                            // so ImagePicker can work with fragment mode
}
```

What's New
--------

- Fix selected images can not be unselected after restart ImagePicker.


License
========

Copyright 2016 Nguyen Hoang Lam, Alok Nair

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
