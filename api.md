# RTC项目

# 1 开始录像
* 路径 /api/record/start
* 方法 POST
## 1.1 参数
| 字段名 | 字段类型 | 说明 |
| :----: | :----: | ------ |
|sessionId|数字|当前janus的会话标识|
|orgId|字符串|当前摄像头所属机构|
|cameraId|字符串|当前摄像头标识|
|timeout|数字|本次录像最长时间，以秒为单位|
* 示例
```
{
    "sessionId": 123,
    "orgId": "100342",
    "cameraId": "212468",
    "timeout": 600
}
```
* 备注: 参数参可以直接以url的query进行传递，也可以用application/json走body传
## 1.2 响应
| 字段名 | 字段类型 | 说明 |
| :----: | :----: | ------ |
|mountId|数字/本次录像的请求标识|
|startTime|时间|本次录像的开始时间|
* 示例
```
    {
        "code":0,
        "msg":"ok",
        "result": {
            "mountId": 498171233112234,
            "startTime": "2020-10-22 14:23:10.876"   
        }
    }
```
返回对想第一层的code为0表示成功,其它表示失败

# 2 结束录像
* 路径 /api/record/end
* 方法 POST
## 2.1 参数

| 字段名 | 字段类型 | 说明 |
| :----: | :----: | ------ |
|orgId|字符串|当前摄像头所属机构|
|cameraId|字符串|当前摄像头标识|
|mountId|字符串|开始录制时返回请求标识|
* 示例
```
{
    "orgId": "100342",
    "cameraId": "212468",
    "mountId": 498822333
}
```
* 备注: 参数参可以直接以url的query进行传递，也可以用application/json走body传
## 2.2 响应
| 字段名 | 字段类型 | 说明 |
| :----: | :----: | ------ |
|mountId|数字|本次录像的请求标识|
|playId|字符串|本次录像回放标识|
|file|字符串|本次录像下载标识|
|startTime|开始时间|本次录像的开始时间|
* 示例
```
    {
        "code":0,
        "msg":"ok",
        "result": {
            "mountId": 498171233112234,
            "playId": "摄像头标识/开始录制sessionId/mountId"
            "file": "http://111.111.111.111:8100/api/files/摄像头标识/开始录制sessionId/mountId.mp4",
            "startTime": "2020-10-22 14:23:10.876"   
        }
    }
```
返回对想第一层的code为0表示成功,其它表示失败

# 3 下载录像
* 路径 /api/files/摄像头标识/开始录制sessionId/mountId.mp4
* 方法 GET
此路径是上面结束录像时返回的,主机和端口则根据实际环境配置

