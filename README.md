# Smart Display SDK HTML5 Creative Samples

In this repository you will find some creative samples that can run on our Display SDKs (Android and iOS):
* Transparent Cover
* Unfold

Both samples can be directly viewed in our Showcase apps, available for [iOS](https://itunes.apple.com/fr/app/smart-adserver-showcase/id1099838195?mt=8) and [Android](https://play.google.com/store/apps/details?id=com.smartadserver.android.showcase)

## Transparent Cover 

<img src="../master/TransparentCover.jpeg?raw=true)" width="200"/>
The purpose of this sample is to display 3d flowers animation above the app while the user can still interact with it (except for the bottom banner and close button that are still clickables).

Transparent Cover sample should be programmed on an interstitial placement using **transfer touch events** option activated.
This option is available in MRAID SDK Interstitial template.

Please note: when this option is activated, no interaction with the creative running in the webview can be done as all touch events will be transferred to the underlying native view except for the HTML ``<a>`` element.

If you need to activate a specific zone (such as div elements) you have two possibilities:
* surround it by HTML ``<a>`` element  
```
 <a href="myclickurl">
  <!-- Put inside, element(s) that should be clickable -->   
 </a>
```
* or set a custom attribute on it: **data-sas-touch-mode=1**
```
 <div id="banner" onclick="window.open('myclickurl');" data-sas-touch-mode="1">
  <!-- Put inside, element(s) that should be clickable -->   
 </div>
```

This option can be activated on MRAID SDK Interstitial format.

### Unfold

<img src="../master/Unfold.jpeg?raw=true)" width="200"/>
The purpose of this sample is to animate the current state of the app (unfold effect) to reveal the advertisement.

Unfold should be programmed on an interstitial placement using MRAID SDK Interstitial template.
This sample demonstrates how to use the extended MRAID screen capture Javascript API (not part of IAB) ``mraid.sasRequestScreenCapture()``, this Javascript API is asynchonous, so you will need to listen to ``sasReceiveScreenCapture`` events , ex:
```
mraid.addEventListener("sasReceiveScreenCapture", function(base64Image) {
        // use your sceen capture image element
        var img = new Image();
        img.src = base64Image;
        // ...
      });
```

Please note: 
* this API will only works inside Smart Display SDKs, to be sure that it's available where your creative is displayed, you can rely on  ``mraid.support("sasRequestScreenCapture")`` 
* your creative should be fully transparent when it's displaying on top of the app, as the purpose is to animate the the app, none elements should be displayed during the request of the screen capture, this is an important timing.

