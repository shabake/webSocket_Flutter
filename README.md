# web_socket

Flutter webSocketDemo

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


