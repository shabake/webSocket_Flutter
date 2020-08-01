# web_socket

Flutter webSocketDemo

WebSocket 是 HTML5 开始提供的一种在单个 TCP 连接上进行全双工通讯的协议。

在 WebSocket API 中，浏览器和服务器只需要完成一次握手，两者之间就直接可以创建持久性的连接，并进行双向数据传输。

![s.jpg](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5ea3fb84-f9f0-4860-ae4b-dcb659f9e5f1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200801%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200801T161619Z&X-Amz-Expires=86400&X-Amz-Signature=622f0d097027c74c0ea4e1e99c72d41388ae41e73aec9c64021b64ce4191a087&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)
## Getting Started


![未标题-2.jpg](https://upload-images.jianshu.io/upload_images/1419035-e2fb2b3c0dd2aa43.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

测试使用地址 

```
ws://echo.websocket.org
```

Flutter官网示例

```
https://flutterchina.club/cookbook/networking/web-sockets/
```

执行步骤

连接到WebSocket服务器。
```
var _webSocketChannel =
      new IOWebSocketChannel.connect('ws://echo.websocket.org');
```

监听来自服务器的消息。

```
new StreamBuilder(
                    stream: this._status == true
                        ? this._webSocketChannel.stream
                        : null,
                    builder: (context, snapshot) {
                      return new Padding(
                          padding: const EdgeInsets.symmetric(vertical: 24.0),
                          child: new Text(
                                  snapshot.hasData
                                      ? '服务器返回: ${snapshot.data}'
                                      : '',
                                  style: TextStyle(
                                      fontSize: 20, color: Colors.black38),
                                )
                              );
                    })
```
将数据发送到服务器。

```
  this._webSocketChannel.sink.add(_controller.text);

```
关闭WebSocket连接。
```
 this._webSocketChannel.sink.close().then((value) {
      print("关闭");
    });
```

[完整代码](https://github.com/shabake/webSocket_Flutter/blob/master/lib/main.dart)


