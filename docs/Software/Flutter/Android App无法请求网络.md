# Android App无法请求网络

在AndroidManifest.xml中添加网络权限：

```
<uses-permission android:name="android.permission.INTERNET"/>
```

分两种情况没有网络：

Debug中在'app/src/debug/AndroidManifest.xml'中添加

Release中在'app/src/main/AndroidManifest.xml'中添加

