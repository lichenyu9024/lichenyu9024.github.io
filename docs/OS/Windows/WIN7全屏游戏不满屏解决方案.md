# WIN7全屏游戏不满屏解决方案 

进注册表编辑器，找到：

HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\GraphicsDrivers\Configuration\

将scaling的键值改为3（原值是4）。