# electron起步

## 新建"package.json"

```json
{
    "name": "my-electron-app",
    "version": "0.0.1",
    "description": "Hello World!",
    "main": "main.js",
    "author": "Ant",
    "scripts": {
        "start": "electron ."
    },
}
```

## 新建"main.js"

```javascript
const { app, BrowserWindow } = require("electron");

function createWindow() {
  // Create the browser window.
  const mainWindow = new BrowserWindow({ width: 800, height: 600 });
  mainWindow.loadFile("index.html");
  // Open the DevTools.
  // mainWindow.webContents.openDevTools()
}

// This method will be called when Electron has finished
// initialization and is ready to create browser windows.
// Some APIs can only be used after this event occurs.
app.whenReady().then(() => {
  createWindow();
  // On macOS it's common to re-create a window in the app when the
  // dock icon is clicked and there are no other windows open.
  app.on("activate", function () {
    if (BrowserWindow.getAllWindows().length === 0) createWindow();
  });
});

// Quit when all windows are closed, except on macOS. There, it's common
// for applications and their menu bar to stay active until the user quits
// explicitly with Cmd + Q.
app.on("window-all-closed", function () {
  if (process.platform !== "darwin") app.quit();
});

```

## 新建网页主页面"index.html"

## 安装electron

```shell
npm install electron

```

## 启动electron

```shell
npm start
```

## 打包程序

```shell
npm install @electron-forge/cli
npx electron-forge import
npm run make
```
