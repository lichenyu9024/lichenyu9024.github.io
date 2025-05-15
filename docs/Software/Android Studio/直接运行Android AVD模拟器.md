# 直接运行Android AVD模拟器

### 在SDK目录下找到emulator.exe程序，创建快捷方式

\AndroidSDK\tools\emulator.exe

### 在快捷方式属性中加入启动参数：

```
 -avd 你的模拟器名称
```


比如：

```
F:\AndroidSDK\tools\emulator.exe -avd Pixel
```