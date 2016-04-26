# Aengin SiltaBluetooth SDK for Android #

## Table of Contents

- [Introduction](#introduction)
- [How to Use](#How-to-Use)
  - [Before Installation](#before-installation)
  - [Installation](#installation)
  - [Application](#application)


## Introduction
SiltaBluetooth applies to Bluetooth Low Energy (BLE) App development on Android environment.

Its main feature is to control, monitor, and track any BLE device or module.

***

## How to Use

### Before Installation
BLE is supported begin Android 4.3 (API Level 18).

### Installation

SiltaBluetooth Android SDK is available on Bintray Maven. 
Declare in your Gradle's `build.gradle` dependency to this library.

```gradle
dependencies {
    compile 'com.aengin.silta.sdk:SiltaBluetooth:1.0.0@aar'
    compile 'com.google.android.gms:play-services:8.4.0'
}
```

### Application

Provides the functions to control Bluetooth devices.

#### Launch SiltaBluetooth SDK
```gradle
  SiltaBluetooth.getManager().startScan();
```

#### Quit SiltaBluetooth SDK

```gradle
  SiltaBluetooth.getManager().stopScan();
```

#### Get Beacon List

```gradle
  SiltaBluetooth.getManager().getBleList(YourActivity.this);
```
   An example showing the beacon list is successfully retrieved.
   
```gradle
  public class MainActivity extends Activity implements SiltaBluetoothDelegate{
  Handler mHandler; // Initialized in onCreate..
  ArrayList<Bluetooth> mBeacon = new ArrayList<Bluetooth>(); // Put Bluetooth into arraylist
  
      @Override
      public void onBluetoothDeviceListBeenRenewed(final ArrayList<Bluetooth> bles) {
          /** It is from the system default UI, and the UI cannot be updated here. */
          mHandler.post(new Runnable() {
              @Override
              public synchronized void run() {
                  /** Your UI is updated here. */
                  mBeacon = bles;
              }
          });
      }
      
  }
```


#### Give a command to one single Beacon device.
```gradle
  SiltaBluetooth.getManager().fireCommand(ICommand.Buzzer,Bluetooth);
```

#### Start SiltaBluetooth transmitter

```gradle
  SiltaBluetooth.getManager().startTransmitter(String Magjor, String Minor, String MeasurePower);
```

#### Stop SiltaBluetooth transmitter

```gradle
  SiltaBluetooth.getManager().stopTransmitter();
```
