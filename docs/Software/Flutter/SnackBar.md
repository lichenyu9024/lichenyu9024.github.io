# SnackBar

SnackBar是显示提示信息的一个控件，会自动隐藏。它还可以添加操作按钮。

SnackBar是通过Scaffold的showSnackBar方法来显示的。

所以要显示一个SnackBar，要先有Scaffold。



### 定义一个SnackBar

```
final snackBar = SnackBar(
	content: Text('这是一个SnackBar!')
);
```

### 定义一个带按钮的SnackBar

```
final snackBar = SnackBar(
	content: Text('这是一个SnackBar!'),
	action: new SnackBarAction(
        label: '好的',
        onPressed: () {}
    ),
);
```

### 显示SnackBar

```
Scaffold.of(context).showSnackBar(snackBar);
```



### 注意事项

当BuildContext在Scaffold之前时，调用Scaffold.of(context)会报错。这时可以通过Builder Widget来解决，代码如下：

```
Scaffold(
    body: Builder(builder: (BuildContext context) {
        return RaisedButton(
            child: Text('显示'),
            onPressed: () {
            var snackBar = SnackBar(content: Text('nmb'));
            Scaffold.of(context).showSnackBar(snackBar);
            },
        );
    }),
),
```

