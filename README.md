# jcrtc视频流服务器

基于webrtc完成视频展示的后端服务器，实现低延时(1s延时)并且无需插件实现视频流展示。
# 特性说明
1. 支持rtsp(tcp)或rtsp(udp)的流
2. 支持Restful视频录制接口,由前端操作完成录制
3. 支持事件通知(mqtt/kafka)进行录制，录制时间由事件消息中参数指定
4. 支持直接对接海康的nvr
5. 占用主机资源少
6. 目前使用webrtclib组件进行展示，由前端直接

