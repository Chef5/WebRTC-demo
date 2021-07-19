# WebRTC-demo

工作之余学习的WebRTC，写了一个简单的demo，和一个用vue.js写的`腾讯会议-山寨版`。

测试过成都市内、成都↔武汉、成都↔北京、成都↔沈阳，基本都成功进行了p2p视频通信！（有部分通信失败了，具体原因不明，应该是和通信商有关系吧）

> 参考了[WebRtcRoomServer](https://github.com/qdgx/WebRtcRoomServer)

**简单的demo：**

![webrtc-simple.jpg](http://img.cdn.1zdz.cn/github/readme/webrtc-simple.jpg)

**腾讯会议-山寨版：**

![webrtc-meeting0.jpg](http://img.cdn.1zdz.cn/github/readme/webrtc-meeting0.jpg)
![webrtc-meeting.jpg](http://img.cdn.1zdz.cn/github/readme/webrtc-meeting.jpg)
## 一、项目文件

### 1.1 `/signal-server`: 信令服务器(nodejs)

运行下面其中一个

- 运行（简单demo）：

``` shell
node app.js
```

- 运行（腾讯会议-山寨版）：

``` shell
node meeting.js
```

信令服务器使用的8443端口，如果有被其他项目占用，可以自行更改。

**重要！！！**

浏览器打开：`https://你本机的ip:8443/`，点击高级选项，选择继续访问，然后就可以直接关闭这个页面了
（这一步很重要，因为使用了自签名证书，浏览器不信任，这样操作后，就会让浏览器信任这个地址，接下来客户端需要用到这个地址）

### 1.2 `/webrtc-client/index.html`: 客户端(简单demo)

编辑：`/webrtc-client/js/config.js`，将信令服务器替换为`wss://你本机的ip:8443/`

``` js
// WebRTC配置文件
const THSConfig = {
  // 信令服务器
  signalServer: 'wss://192.168.1.6:8443/',
}
```

运行：

我是通过anywhere启动的一个本地服务，如果本机有nginx或者其他可以启动服务的，可以通过其他程序启动运行

``` shell
npm i anywhere -g
```

进入`/webrtc-client`目录执行：

``` shell
anywhere
```

然后浏览器就会自动打开咱们的客户端。

### 1.3 `/webrtc-client/vue.html`: 客户端(腾讯会议-山寨版)

编辑：`/webrtc-client/vue.html`，将信令服务器替换为`wss://你本机的ip:8443/`

然后按照上面的简单demo一样运行启动。
