# react-native-adbmobile

Integrates
[Adobe Mobile Services SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services)
as [React Native](https://facebook.github.io/react-native/) module,
enabling applications to use Analytics, Target, Campaign, and Audience
Manager.

## Getting started

`$ npm install react-native-adbmobile --save`

### Mostly automatic installation

`$ react-native link react-native-adbmobile`

### Manual installation

#### iOS

1. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2. Go to `node_modules` ➜ `react-native-adbmobile` and add `RNADBMobile.xcodeproj`
3. In XCode, in the project navigator, select your project. Add `libRNADBMobile.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4. Run your project (`Cmd+R`)


#### Android

1. Open up `android/app/src/main/java/[...]/MainActivity.java`
  - Add `import co.work.RNADBMobilePackage;` to the imports at the top of the file
  - Add `new RNADBMobilePackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':react-native-adbmobile'
  	project(':react-native-adbmobile').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-adbmobile/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
      compile project(':react-native-adbmobile')
  	```

## Configuration

### Android

Follow
[Download the SDK](https://marketing.adobe.com/resources/help/en_US/mobile/android/requirements.html)
instructions, we're particularly interested in the `ADBMobileConfig.json`,
since is automatically handled by Gradle.

Then add the `ADBMobileConfig.json` file to the
`android/app/src/main/assets` folder in your Application.

The following permissions are required in your
`android/app/src/main/AndroidManifest.xml`:
```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Life cycle metrics are implemented using React Native's context.
If other activities exist, then follow the instructions at
[Adobe Cloud Center Help: Implement Lifecycle Metrics](https://marketing.adobe.com/resources/help/en_US/mobile/android/dev_qs.html)
to ensure accurate crash reporting.

## Usage
```javascript
import { Config, Analytics } from 'react-native-adbmobile';

// Setters do not return a value, neither throw errors
Config.setPrivacyStatus(Config.MobilePrivacyStatus.optIn);

// Getters are promises
Config.getUserIdentifier().then(userIdentifier => console.log(userIdentifier));

// Tracking takes an optional 'contextData' as last parameter.
// It's an object to basic types (string, number, boolean)
// or array/object of those.
Analytics.trackAction('anAction')
Analytics.trackState('aState', { key: 'value' })
```

## Development

### Android

Open `android/` using Android Studio.

### iOS


# References
 - [Adobe Mobile Services Help](https://marketing.adobe.com/resources/help/en_US/mobile/)
 - [Adobe Mobile Services GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services)
 - [React Native Modules - Android](https://facebook.github.io/react-native/docs/native-modules-android.html)
 - [React Native Modules - iOS](https://facebook.github.io/react-native/docs/native-modules-ios.html)
