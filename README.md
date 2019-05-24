# WebSocket-WebRTC

#### 介绍
WebSocket+WebRTC+nodejs实现多人视频加文本聊天室
使用了reconnecting-websocket.js解决了socket断线重连问题
使用了adapter.js方便使用webRTC

#### 功能
- 群聊视频通话功能 进入房间后可以与房间内所有人视频通话
- 打字聊天功能 可以使用键盘进行文本交流
- 房间号功能 不同房间号之间的视频及聊天内容互不影响
- 房间号用户名不能为空验证提醒功能
- 用户名重复提醒功能 同一房间用户名重复给予提示
- 用户退出提醒 其他用户自动断开与该用户链接并有提示


#### 软件架构
后端使用nodejs
- 框架使用express
> 主要用于生成静态服务器，完全可以不使用express，自己搭客户端文件的静态服务器比如http-server
- ws模块
> 这个是实现websocket的模块，封装了websocket的一些方法，方便开发者使用websocket做业务逻辑，而不用关心websocket底层实现



#### 安装教程

1. yarn 或者 npm i
2. node server
3. 打开两个窗口分别输入下面链接即可查看效果
> http://localhost:3000?room=10&name=aaa，http://localhost:3000?room=10&name=aaa

#### 使用说明

1. url上的room为房间号，name为用户名，可以自定义
3. 需要允许浏览器摄像头权限


### WebSocket 兼容性
- Internet Explorer 10
- Firefox 6
- Chrome 14
- Safari 6.0
- Opera 12.1
- iOS Safari 6.0
- 不支持ie9及以下
- Chrome for Android 27.0
#### 如何让旧浏览器兼容
- 可以使用 socket.io
> 使用这个 服务端和浏览器端都要使用 浏览器端使用socket.io-client，
> 如果是node 服务器端也可以使用基于socket.io的koa-socket
- 可以使用 SockJS
> 也是要客户端同时配合使用相应的服务器端的库 如：SockJS-node, SockJS-erlang, SockJS-tornado, SockJS-twisted, SockJS-ruby, SockJS-netty, SockJS-gevent (SockJS-gevent fork), SockJS-go


### webRTC 兼容性
- Chrome（支持最好）
- Firefox
- Safari（ iOS 11 和 Safari 11 ）（DataChannel不能用）
- Edge（支持一部分）
- 不支持ie


#### 效果截图
