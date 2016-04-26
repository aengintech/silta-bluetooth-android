# Aengin SiltaBluetooth SDK for Android #

## 大綱

- [簡介](#簡介)
- [使用方式](#使用方式)
  - [安裝前條件](#安裝前條件)
  - [安裝](#安裝)
  - [使用](#使用)


## 簡介
SiltaBluetooth適用於Android之BLE App開發

功能: 提供控制 bluetooth 提供追蹤藍芽元件運行機制的各種方式
***

## 使用方式

### 安裝前條件
BLE 需 Android 4.3 (API Level 18) 或更高版本的 Android 設備

### 安裝

SiltaBluetooth Android SDK is available on Bintray Maven. 
Declare in your Gradle's `build.gradle` dependency to this library.

```gradle
dependencies {
    compile 'com.aengin.silta.sdk:SiltaBluetooth:1.0.0@aar'
    compile 'com.google.android.gms:play-services:8.4.0'
}
```

### 使用
提供控制Bluetooth功能
#### 開啟 SiltaBluetooth SDK
```gradle
  SiltaBluetooth.getManager().startScan();
```

#### 停止 SiltaBluetooth SDK
```gradle
  SiltaBluetooth.getManager().stopScan();
```

#### 取得Beacon列表
```gradle
  SiltaBluetooth.getManager().getlist(MainActivity.this);
```
   實現列表取得
   
```gradle
  public class MainActivity extends Activity implements SiltaBluetoothDelegate{
  Handler mHandler; // 初始化在onCreate裡
  ArrayList<Bluetooth> mBeacon = new ArrayList<Bluetooth>(); // Put Bluetooth into arraylist
      @Override
      public void onBluetoothDeviceListBeenRenewed(final ArrayList<Bluetooth> arrayList) {
          /** 因為來自非UI線程,所以不能直接更新UI */
          mHandler.post(new Runnable() {
              @Override
              public synchronized void run() {
                  /** 在這更新你的UI */
                  mBeacon = arrayList;
              }
          });
      }
      
  }
```


#### 對單一Beacon下指令
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
