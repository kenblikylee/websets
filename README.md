# websets
web 大杂烩！

## 调试工具 CURL

### Get 请求

``` sh
curl <url>
```

添加查询参数：

``` sh
curl -G -d 'id=1' -d 'type=2' <url>
# 对数据做 URL 编码
curl -G --data-urlencode 'id=1&name=hello world' <url>
```

### Post 请求

> `-X post` 可省略

``` sh
curl -d 'name1=value1&name2=value2...' [-X POST] <url>
# 或者
curl -d 'name1=value1' -d 'name2=value2' <url>
```

> 使用-d参数以后，HTTP 请求会自动加上标头Content-Type : application/x-www-form-urlencoded。

对 POST 数据做 URL 编码：

``` sh
curl --data-urlencode 'name1=hello world' <url>
```

读取本地文件的数据：

``` sh
curl -d '@data.txt' <url>
```

### 上传二进制文件

``` sh
curl -F 'file=@image.png' <url>
```

> 上面命令会给 HTTP 请求加上标头Content-Type: multipart/form-data，然后将文件 image.png 作为file字段上传。

### 选项

- `-b` 发送 Cookie，`-b 'token=xxx;userid=123'` 或读取文件发送 `-b cookies.txt`
- `-c` 保存服务器设置的 Cookie，`-c cookies.txt`
- `-A` 添加 User-Agent 请求头
- `-e` 添加 Referer 请求头
- `-H` 添加请求头，`-H 'Accept-Language: en-US'`
- `-i` 打印响应标头
- `-I` 发送 HEAD 请求
- `-o` 输出保存到文件
- `-O` 输出保存到文件，使用 URL 最后部分作文件名
- `-s` 不输出错误和进度信息
- `-S` 只输出错误信息，通常与`-s`一起使用 `-sS`
- `-v` 参数输出通信的整个过程，用于调试
- `-x` 设置请求代理
- `-X` 设置 HTTP 请求方法
- `-u` 设置服务认证的用户名和密码，`curl -u username:password <url>`
