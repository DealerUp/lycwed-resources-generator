# lycwed-resources-generator

Automatic icon and splash screen resizing for any **Cordova** based applications including **PhoneGap**. It uses an ```icon.png``` and a ```splash.png``` to automatically resize and copy it for all the platforms your project supports (currently works with **iOS**, **Android** and **Windows Phone 8**).

### Installation

     $ npm install lycwed-resources-generator -g

---

### Usage

Add ```icon.png``` and ```splash.png``` 'resources' folder under the root folder of your cordova project and run:

     $ resources-generator

You can change the default folder for the base images using the argument `imagespath`. Consider the following example:

     $ resources-generator --imagespath="path/to/assets"

This will look for an ```icon.png``` and a ```splash.png``` in the **path/to/assets** folder under the root folder of your cordova project.

By default it will generate ios and android icons. You can add manually platforms with `platforms`. Consider the following example:

     $ resources-generator --platforms="ios, android, wp8, windows"

### Model 

Use the Photoshop templates provided in the model folder to generate the PNG files.

### Icon

Should be a 1024x1024px with a 5% margin.

#### Splash

Your splash must be 2732x2732px as it now is the largest resolution (used by iPad Pro 12.9"), and the artwork should fit a center square (1200x1200px).
This Photoshop splash screen template provides the recommended size and guidelines of the artwork’s safe zone.

#### Platform specific assets

You can provide a platform-specific icon by creating a subfolder with the name of the platform.

- model
    - icon.png      // Default icon used for all platforms if not overriden.
    - splash.png    // Default splash used for all platforms if not overriden.
    - android
        - icon.png  // Override the default icon for the 'android' platform. So you can use an icon with alpha, as apple doens't allow.

---

### Requirements

#### ImageMagick

Install on a Mac:

     $ brew install imagemagick

On linux:

    $ sudo apt-get install imagemagick

On windows, see http://www.imagemagick.org/script/binary-releases.php#windows. Also, on the version 7.0.0+ you will have to check the 'Install legacy utilities' option (which is not enabled by default).
     

---

### Configuring icons & splascreen for Cordova project

Include in your ```config.xml``` file:

```xml
<platform name="android">
    <icon density="ldpi" src="resources/android/icon/drawable-ldpi-icon.png" />
    <icon density="mdpi" src="resources/android/icon/drawable-mdpi-icon.png" />
    <icon density="hdpi" src="resources/android/icon/drawable-hdpi-icon.png" />
    <icon density="xhdpi" src="resources/android/icon/drawable-xhdpi-icon.png" />
    <icon density="xxhdpi" src="resources/android/icon/drawable-xxhdpi-icon.png" />
    <icon density="xxxhdpi" src="resources/android/icon/drawable-xxxhdpi-icon.png" />
    <splash density="land-ldpi" src="resources/android/splash/drawable-land-ldpi-screen.png" />
    <splash density="land-mdpi" src="resources/android/splash/drawable-land-mdpi-screen.png" />
    <splash density="land-hdpi" src="resources/android/splash/drawable-land-hdpi-screen.png" />
    <splash density="land-xhdpi" src="resources/android/splash/drawable-land-xhdpi-screen.png" />
    <splash density="land-xxhdpi" src="resources/android/splash/drawable-land-xxhdpi-screen.png" />
    <splash density="land-xxxhdpi" src="resources/android/splash/drawable-land-xxxhdpi-screen.png" />
    <splash density="port-ldpi" src="resources/android/splash/drawable-port-ldpi-screen.png" />
    <splash density="port-mdpi" src="resources/android/splash/drawable-port-mdpi-screen.png" />
    <splash density="port-hdpi" src="resources/android/splash/drawable-port-hdpi-screen.png" />
    <splash density="port-xhdpi" src="resources/android/splash/drawable-port-xhdpi-screen.png" />
    <splash density="port-xxhdpi" src="resources/android/splash/drawable-port-xxhdpi-screen.png" />
    <splash density="port-xxxhdpi" src="resources/android/splash/drawable-port-xxxhdpi-screen.png" />
</platform>
<platform name="ios">
    <icon height="57" src="resources/ios/icon/icon.png" width="57" />
    <icon height="114" src="resources/ios/icon/icon@2x.png" width="114" />
    <icon height="40" src="resources/ios/icon/icon-40.png" width="40" />
    <icon height="80" src="resources/ios/icon/icon-40@2x.png" width="80" />
    <icon height="120" src="resources/ios/icon/icon-40@3x.png" width="120" />
    <icon height="50" src="resources/ios/icon/icon-50.png" width="50" />
    <icon height="100" src="resources/ios/icon/icon-50@2x.png" width="100" />
    <icon height="60" src="resources/ios/icon/icon-60.png" width="60" />
    <icon height="120" src="resources/ios/icon/icon-60@2x.png" width="120" />
    <icon height="180" src="resources/ios/icon/icon-60@3x.png" width="180" />
    <icon height="72" src="resources/ios/icon/icon-72.png" width="72" />
    <icon height="144" src="resources/ios/icon/icon-72@2x.png" width="144" />
    <icon height="76" src="resources/ios/icon/icon-76.png" width="76" />
    <icon height="152" src="resources/ios/icon/icon-76@2x.png" width="152" />
    <icon height="167" src="resources/ios/icon/icon-83.5@2x.png" width="167" />
    <icon height="29" src="resources/ios/icon/icon-small.png" width="29" />
    <icon height="58" src="resources/ios/icon/icon-small@2x.png" width="58" />
    <icon height="87" src="resources/ios/icon/icon-small@3x.png" width="87" />
    <splash height="1136" src="resources/ios/splash/Default-568h@2x~iphone.png" width="640" />
    <splash height="1334" src="resources/ios/splash/Default-667h.png" width="750" />
    <splash height="2208" src="resources/ios/splash/Default-736h.png" width="1242" />
    <splash height="1242" src="resources/ios/splash/Default-Landscape-736h.png" width="2208" />
    <splash height="1536" src="resources/ios/splash/Default-Landscape@2x~ipad.png" width="2048" />
    <splash height="768" src="resources/ios/splash/Default-Landscape~ipad.png" width="1024" />
    <splash height="2048" src="resources/ios/splash/Default-Portrait@2x~ipad.png" width="1536" />
    <splash height="1024" src="resources/ios/splash/Default-Portrait~ipad.png" width="768" />
    <splash height="960" src="resources/ios/splash/Default@2x~iphone.png" width="640" />
    <splash height="480" src="resources/ios/splash/Default~iphone.png" width="320" />
</platform>
```


**Notes**:

With new versions of the Cordova you may want to use the config `<preference name="SplashMaintainAspectRatio" value="true" />` to avoid distorted images on android.
More info on [cordova-plugin-splashscreen](https://github.com/apache/cordova-plugin-splashscreen).

---

### Configuring splash and icon for PhoneGap project

You can use the same configuration of an cordova project just adjusting the xml elements as their documentation says:

[http://docs.phonegap.com/phonegap-build/configuring/icons-and-splash/](http://docs.phonegap.com/phonegap-build/configuring/icons-and-splash/) 

---

### Generate custom assets

You can use this package under node to specify custom assets. I personally use this for adding a custom Icon for Push on android. That needs to be an icon with transparency.
I use it with gulp like this:

```js
var splashiconGenerator = require("lycwed-resources-generator");

gulp.task('generate-splashicon', function(done) {
    // Generate all the default assets
    splashiconGenerator.generate()
    .then(function() {

        // Configure the custom assets with their sizes 
        var options = {
            ICON_FILE: path.join('model', 'pushicon.png'),
            SPLASH_FILE: '', // ignore plash generation
            ICON_PLATFORMS: [{
                name: 'android-push-icon',
                iconsPath: 'res/icons/android/',
                isAdded: true,
                icons: [
                    { name: 'push-icon-36-ldpi.png', size: 36, density: 'ldpi' },
                    { name: 'push-icon-48-mdpi.png', size: 48, density: 'mdpi' },
                    { name: 'push-icon-72-hdpi.png', size: 72, density: 'hdpi' },
                    { name: 'push-icon-96-xhdpi.png', size: 96, density: 'xhdpi' },
                    { name: 'push-icon-144-xxhdpi.png', size: 144, density: 'xxhdpi' },
                    { name: 'push-icon-192-xxxhdpi.png', size: 192, density: 'xxxhdpi' }
                ]
            }]
        };
        // Generate only the custom assets specified in the `options` parameter
        splashiconGenerator.generate(options).then(function() {
            done();
        });
    });
});
```

Then just add it to the `config.xml`:

```xml
<!-- pushicon -->
<platform name="android">
    <icon density="ldpi" src="res/icons/android/push-icon-36-ldpi.png" />
    <icon density="mdpi" src="res/icons/android/push-icon-48-mdpi.png" />
    <icon density="hdpi" src="res/icons/android/push-icon-72-hdpi.png" />
    <icon density="xhdpi" src="res/icons/android/push-icon-96-xhdpi.png" />
    <icon density="xxhdpi" src="res/icons/android/push-icon-144-xxhdpi.png" />
    <icon density="xxxhdpi" src="res/icons/android/push-icon-192-xxxhdpi.png" />
</platform>
```

---

### References

- [iOS Human Interface Guidelines - Graphics](https://developer.apple.com/ios/human-interface-guidelines/graphics/app-icon/)

---

### License

MIT
