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


#### webRTC大致流程
1. 获取本地媒体流放到video的src中
2. AB两点连接需要创建双方各自的 RTCPeerConnection
3. A点创建offer后设置本地视频setLocalDescription
4. A点发送带有本地sdp的offer给B点
5. B点收到offer并根据offer的sdp设置远端视频setRemoteDescription
6. B点创建answer后设置本地视频setLocalDescription
7. B点发送带有本地sdp的answer给A
7. A点收到answer并根据answer的sdp设置远端视频setRemoteDescription
8. 至此AB两点都设置了各自的本地和远端视频，点对点视频通话完成

##### 白话翻译：张三和李四视频通信过程
0. 首先张三和李四各自都有自己的本地视频标签video和远端视频标签video
1. 张三创建自己本地视频流并放到自己（张三）本地视频标签video中
2. 张三将自己（张三）的本地视频流发给李四
3. 李四收到张三的本地视频流并将其放到自己（李四）远端视频标签video中
4. 李四创建自己的本地视频流放到自己（李四）本地视频标签video中
5. 李四将自己（李四）的本地视频流发给张三
6. 张三收到李四的本地视频流并将其放到自己（张三）远端视频标签video中
7. 这样张三和李四就可以视频通信了


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
![输入图片说明](https://images.gitee.com/uploads/images/2019/0524/131822_cb1569bd_914638.png "WechatIMG476.png")
![输入图片说明](https://images.gitee.com/uploads/images/2019/0524/131837_6e9febdd_914638.png "WX20190524-130817@2x.png")
