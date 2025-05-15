# 去除Flutter应用右上角的Debug标签：

方法一、在debug模式下去除Debug标签：

在MaterialApp的属性中加入下面代码：
debugShowCheckedModeBanner: false

```
  Widget build(BuildContext context) {
    return new MaterialApp(
      title: 'Welcome to Flutter',
      debugShowCheckedModeBanner: false,
      home: new Scaffold(
        appBar: new AppBar(
          title: new Text('Welcome to Flutter'),
        ),
        body: new Center(
          child: new Text('Hello World'),
        ),
      ),
    );
  }
```

方法二、发布Release版会自动去除该标签
Android：运行 flutter build apk
IOS：运行 flutter build ios