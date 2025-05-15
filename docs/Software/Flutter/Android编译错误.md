# 一些Android 编译错误：

#### 报错：
```
Error running Gradle
Could not find lint-gradle-api.jar
```



原因是jcenter google库无法访问到导致的问题。

1.使用Android Studio打开Flutter工程目录下的android文件夹
2.打开Project->build.gradle
3.注释掉jcenter()，google()。使用阿里的镜像。

```
buildscript {
    repositories {
//        google()
//        jcenter()
        maven { url 'https://maven.aliyun.com/repository/google' }
        maven { url 'https://maven.aliyun.com/repository/jcenter' }
        maven { url 'http://maven.aliyun.com/nexus/content/groups/public' }
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:3.1.2'
    }
}

allprojects {
    repositories {
//        google()
//        jcenter()
        maven { url 'https://maven.aliyun.com/repository/google' }
        maven { url 'https://maven.aliyun.com/repository/jcenter' }
        maven { url 'http://maven.aliyun.com/nexus/content/groups/public' }
    }
}
```

4.⁨打开Flutter SDK目录下/packages/flutter_tools/gradle⁩/flutter.gradle
5.注释jcenter，参考以下内容修改

```
buildscript {
    repositories {
        //jcenter()
        //maven {
        //    url 'https://dl.google.com/dl/android/maven2'
        //}
        maven{
            url 'https://maven.aliyun.com/repository/jcenter'
        }
        maven{
            url 'http://maven.aliyun.com/nexus/content/groups/public'
        }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.1.2'
    }
}
```





#### 报错：Execution failed for task ':app:processDebugResources'

```
FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:processDebugResources'.
> Android resource linking failed
  Output:  F:\App\FlutterProject\loctest\build\app\intermediates\incremental\mergeDebugResources\merged.dir\values\values.xml:197: error: resource android:attr/fontVariationSettings not found.
  F:\App\FlutterProject\loctest\build\app\intermediates\incremental\mergeDebugResources\merged.dir\values\values.xml:198: error: resource android:attr/ttcIndex not found.
  error: failed linking references.

  Command: C:\Users\Ant\.gradle\caches\transforms-1\files-1.1\aapt2-3.2.1-4818971-windows.jar\4025b668f7ca8fb376b6e3fdd09b559f\aapt2-3.2.1-4818971-windows\aapt2.exe link -I\
          F:\App\AndroidSDK\platforms\android-27\android.jar\
          --manifest\
          F:\App\FlutterProject\loctest\build\app\intermediates\merged_manifests\debug\processDebugManifest\merged\AndroidManifest.xml\
          -o\
          F:\App\FlutterProject\loctest\build\app\intermediates\processed_res\debug\processDebugResources\out\resources-debug.ap_\
          -R\
          @F:\App\FlutterProject\loctest\build\app\intermediates\incremental\processDebugResources\resources-list-for-resources-debug.ap_.txt\
          --auto-add-overlay\
          --java\
          F:\App\FlutterProject\loctest\build\app\generated\not_namespaced_r_class_sources\debug\processDebugResources\r\
          --custom-package\
          com.example.loctest\
          -0\
          apk\
          --output-text-symbols\
          F:\App\FlutterProject\loctest\build\app\intermediates\symbols\debug\R.txt\
          --no-version-vectors
  Daemon:  AAPT2 aapt2-3.2.1-4818971-windows Daemon #0
  Output:  C:\Users\Ant\.gradle\caches\transforms-1\files-1.1\core-1.0.0-rc01.aar\195170eaf644fd758b0616863f692a31\res\values\values.xml:89:5-125:25: AAPT: error: resource android:attr/fontVariationSettings not found.

  C:\Users\Ant\.gradle\caches\transforms-1\files-1.1\core-1.0.0-rc01.aar\195170eaf644fd758b0616863f692a31\res\values\values.xml:89:5-125:25: AAPT: error: resource android:attr/ttcIndex not found.

  error: failed linking references.
  Command: C:\Users\Ant\.gradle\caches\transforms-1\files-1.1\aapt2-3.2.1-4818971-windows.jar\4025b668f7ca8fb376b6e3fdd09b559f\aapt2-3.2.1-4818971-windows\aapt2.exe link -I\
          F:\App\AndroidSDK\platforms\android-27\android.jar\
          --manifest\
          F:\App\FlutterProject\loctest\build\app\intermediates\merged_manifests\debug\processDebugManifest\merged\AndroidManifest.xml\
          -o\
          F:\App\FlutterProject\loctest\build\app\intermediates\processed_res\debug\processDebugResources\out\resources-debug.ap_\
          -R\
          @F:\App\FlutterProject\loctest\build\app\intermediates\incremental\processDebugResources\resources-list-for-resources-debug.ap_.txt\
          --auto-add-overlay\
          --java\
          F:\App\FlutterProject\loctest\build\app\generated\not_namespaced_r_class_sources\debug\processDebugResources\r\
          --custom-package\
          com.example.loctest\
          -0\
          apk\
          --output-text-symbols\
          F:\App\FlutterProject\loctest\build\app\intermediates\symbols\debug\R.txt\
          --no-version-vectors
  Daemon:  AAPT2 aapt2-3.2.1-4818971-windows Daemon #0

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 1s
WARNING: This version of google_maps_flutter will break your Android build if it or its dependencies aren't compatible with AndroidX.
         See https://goo.gl/CP92wY for more information on the problem and how to fix it.
         This warning prints for all Android build failures. The real root cause of the error may be unrelated.
         *********************************************************
Finished with error: Gradle task assembleDebug failed with exit code 1
```

#### 可能可以解决的方法：

打开android\app\build.gradle

修改 compileSdkVersion 和 targetSdkVersion为：28

```
android {
    compileSdkVersion 28

    lintOptions {
        disable 'InvalidPackage'
    }

    defaultConfig {
        // TODO: Specify your own unique Application ID (https://developer.android.com/studio/build/application-id.html).
        applicationId "com.lyokone.locationexample"
        minSdkVersion 16
        targetSdkVersion 28
        versionCode flutterVersionCode.toInteger()
        versionName flutterVersionName
        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            // TODO: Add your own signing config for the release build.
            // Signing with the debug keys for now, so `flutter run --release` works.
            signingConfig signingConfigs.debug
        }
    }
}
```

---

#### 报错：FormatException: Bad UTF-8 encoding

#### 解决方法：

Android Studio修改设置

Flie - Settings - Editor - Flie Encodeing

project encoding 改为utf-8