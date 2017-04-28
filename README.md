# Ti.Harman
<img src="https://www.developer.harman.com/images/harman/logo/Harman_Logo.png" width=200 />
Appcelerator Titanium module for controling Harman SDK (Soundsystem).

The Harman/Kardon WirelessHD SDK is provided for Android 3rd party developers to communicate
with Harman/Kardon Omni Series audio/video devices. The intent of this SDK is to provide the tools
and libraries necessary to build, test and deploy the latest audio applications on the Android platform.

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

Harman.addEventListener("scancomplete",function(devicelist){
    devicelist.forEach(function(device) {
        console.log(device);
    });
    Harman.stopDeviceScan();
});
Harman.startDeviceScan();  // will refresh and update every 2 seconds the status of the devices in the
                    // current WiFi network.```
```
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

```javascript
Harman.addDeviceToSession(0));
Harman.removeDeviceToSession(0));
```
### Play a  song 
```javascript
var Player = createAudioCodecHandler();
Player.playCAF({
    url : url,
    title : songTitle,
    resume : resumeFlag
});
```
Here, resumeFlag is false, if you start the song from the beginning. If you want to resume to play the
current song, then resumeFlag should be true. ‘songTitle’ is a string, representing the song name. (This
is only internally used as a file name to store converted PCM data in the memory temporarily.)
playCAF() can play both mp3, wav, flac, sac, m4a and ogg audio file. It is converted to PCM format
first, and then played.The sample rate of the song above 44100.
playWAV() can play wav audio file. It is played without conversion.

```javascript
Player.stop();
Player.pause();
Player.isPlaying();
```
## Volume control
```javascript
Harman.setVolumeAll(25);
Harman.setVolumeDevice(deviceId,volume)
```

## Callbacks
```javascriptt
Harman.addEventListener("statechanged",function(state){
});
Harman.addEventListener("complete",function(state){
});
Harman.addEventListener("progress",function(state){ //every second
});

```


```
