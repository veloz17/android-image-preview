![](https://thedroid.io/assets/img/tb-image-preview.png)

![API](https://img.shields.io/badge/API-16%2B-34bf49.svg)
[ ![Download](https://api.bintray.com/packages/greentoad/android-image-preview/com.greentoad.turtlebody.imagepreview/images/download.svg?version=latest) ](https://bintray.com/greentoad/android-image-preview/com.greentoad.turtlebody.imagepreview/1.0.1/link)


### Demo:
![](https://media.giphy.com/media/SXxdWquu9zlLiHIuc2/giphy.gif)

[<img src="https://play.google.com/intl/en_us/badges/images/generic/en-play-badge.png"
     alt="Get it on Google Play"
     height="80">](https://play.google.com/store/apps/details?id=com.greentoad.turtlebody.imagepreview.sample)

## Image Preview Library for Android (AndroidX)

A Image Preview library for Android for selecting single/multiple files of any type.


## Setup
Step 1: Add the dependency

```gradle
dependencies {
    ...
    /*image preview*/
    implementation 'com.greentoad.turtlebody.imagepreview:image-preview:1.0.1'
}
```

## Usage
Step 1: Declare and Initialize ImagePreview.

#### Java
```java
ArrayList<Uri> arrayList = new ArrayList<>();
//add uri to arrayList

ImagePreviewConfig config = new ImagePreviewConfig().setAllowAddButton(true);

ImagePreview.with(this)
        .setUris(arrayList)
        .setConfig(config)
        .setListener(new ImagePreview.ImagePreviewImpl.OnImagePreviewListener() {
            @Override
            public void onDone(@NotNull ArrayList<Uri> data) {
                //after done all uri is sent back
            }

            @Override
            public void onAddBtnClicked() {
                //trigger when button clicked
            }
        })
        .start();
```

#### Kotlin
```kotlin
val arrayList = arrayListOf<Uri>()
//add uri to arrayList

val config = ImagePreviewConfig().setAllowAddButton(true)

ImagePreview.with(this)
    .setUris(arrayList)
    .setConfig(config)
    .setListener(object : ImagePreview.ImagePreviewImpl.OnImagePreviewListener{
        override fun onDone(data: ArrayList<Uri>) {
            info { "data: $data" }

            //info { "data size: ${DocumentFile.fromSingleUri(this@ActivityHome,data[0])!!.length()}" }
        }

        override fun onAddBtnClicked() {
            info { "addBtn clicked" }
        }
    })
    .start()
```

## Explanation:

#### 1. ImagePreviewConfig:
It is use to set the configuration.
1. **.setAllowAddButton(booleanValue)**: tells whether to show add button in preview activity.

eg.
```java
//Pick single file with confirmation dialog and set extentions arguments
ImagePreviewConfig config = new ImagePreviewConfig().setAllowAddButton(true);

```


### URI:
We will be returning the list of Uri after done button is clicked. That's why it is better to know about Uri first.

A Uniform Resource Identifier (URI) is a compact sequence of characters that identifies an abstract or physical resource.

In Android, Content providers manage access to a structured set of data. They encapsulate the data, and provide mechanisms for defining data security. Content providers are the standard interface that connects data in one process with code running in another process.
You can get almost all information from uri.
#### URI usages:
1. Get file from uri:
```java
File file = new File(uri.getPath());
```

2. Get mime from uri:
```java
String mimeType = getContentResolver().getType(uri);
```

3. Used in Glide:
```java
Glide.with(context)
     .load(uri)
     .into(imageView);
```


---
### Quick Links

*  [ChangeLog](/CHANGELOG.md)
*  [Documentation](https://github.com/Turtlebody/android-image-preview/wiki)

### Demos

*  [Example](/Example.md)
*  [Sample APK file](https://play.google.com/store/apps/details?id=com.greentoad.turtlebody.imagepreview.sample)

### Developers

*  [API Documentation](https://github.com/Turtlebody/android-image-preview/wiki/API-Documentation)
*  [Developer Setup & Usage](https://github.com/Turtlebody/android-image-preview/wiki/Developer-Setup)

---


## To pick media files(audio,image,video) you can use [Turtlebody Media Picker](https://github.com/Turtlebody/android-media-picker) library.





