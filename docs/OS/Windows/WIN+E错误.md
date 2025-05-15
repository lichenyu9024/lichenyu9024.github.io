# WIN+E错误

以下代码存为.reg文件后运行：
```
Windows Registry Editor Version 5.00

[[HKEY_CLASSES_ROOT\Folder\shell\explore\command] 

"DelegateExecute"="{11dbb47c-a525-400b-9e80-a54615a090c0}"

[HKEY_CLASSES_ROOT\Folder\shell\opennewprocess\command] 

"DelegateExecute"="{11dbb47c-a525-400b-9e80-a54615a090c0}"

[HKEY_CLASSES_ROOT\Folder\shell\opennewwindow\command] 

"DelegateExecute"="{11dbb47c-a525-400b-9e80-a54615a090c0}"
```