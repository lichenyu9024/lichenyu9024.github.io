# Android & IOS声明定位权限

### Android

在"工程/app/src/main/AndroidManifest.xml"中添加：

```
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```



### IOS

在"工程/Runner/Info.plist"中添加(前台定位 / 后台定位)：

```
<key>NSLocationWhenInUseUsageDescription</key>
<string>若不开启定位客户将无法获取您的位置信息</string>

<key>NSLocationAlwaysUsageDescription</key>
<string>若不开启定位客户将无法获取您的位置信息</string>
```

