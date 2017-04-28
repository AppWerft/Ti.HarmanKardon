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

startDeviceScan() will refresh and update every 2 seconds the status of the devices in the
current WiFi network.```

## Get the number of available speakers
```javascript
Harman.getDeviceCount();
```
## Get info of a device

```javascript
Harman.getDeviceInfoByIndex(0); // or other int in range
```
Every device has a lot of paramters:
- [x] deviceId      the unique ID of the speaker
- [x] deviceName
- [x] ipAddress
- [x] volume
- [x] port
- [x] modelName
- [x] zoneName
- [x] active
- [x] version
- [x] wifiSignalStrength
- [x] groupId
- [x] balance
- [x] isPlaying
- [x] channelType
- [x] isMaster

## Change speaker name
```javascript
Harman.setDeviceName(deviceId,”MyOmni10”);
```
## Add or remove a speaker to/from a playback session
To play a music on a specific speaker, the speaker should be added to the playback session
