# VS Code Vim插件禁用某些组合键

##### 例子：禁用`Ctrl + C`

在vs code的settings.json中添加以下内容：

```
"vim.handleKeys": {
	"<C-c>": false
}
```

