# Ti.Harman

Appcelerator Titanium module for controling Harman SDK (Soundsystem).

## Permissions

First we need a lot of permissions:

```xml
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.MOUNT_UNMOUNT_FILESYSTEMS"/>
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.WAKE_LOCK" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
<uses-permission android:name="android.permission.CHANGE_WIFI_STATE"/>
<uses-permission android:name="android.permission.CHANGE_WIFI_MULTICAST_STATE"/>
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
<uses-permission android:name="android.permission.CHANGE_NETWORK_STATE"/>
<uses-permission android:name="android.permission.WRITE_SETTINGS"/>
```
A part of it needs runtime permissions for API upto M.

# Usage

## Browsing for Harman devices
```javascript
var Harman = require("de.appwerft.harman");
Harman.startDeviceScan();
Harman.addEventListener("load",function(devicelist){
    devicelist.forEach(showDevicesFn);
});
Harman.stopDeviceScan();

```
Every device has a lot of paramters:

- [x] deviceName

## 
