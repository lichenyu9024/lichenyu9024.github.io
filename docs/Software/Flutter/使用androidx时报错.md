### 如果在使用androidx库时, 又不小心间接使用了其他的老库, 可能会遇到如下的报错:

```
Program type already present: android.support.v4.os.ResultReceiver
```

解决方法:
可以尝试在gradle.properties中添加:

```
android.useAndroidX=true
android.enableJetifier=true
```


已知以下Packages会导致该报错：
geolocator