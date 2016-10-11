## ngrok简介
```
ngrok可监控本地的一个端口，生成全网可访问的url地址
```

### 使用场景及对比
```
应用场景：
在程序开发过程中，需要向前端，或者其他应用开放接口进行测试，而且不在同一个网段内，此时需要一个外部可访问的地址。
解决办法：
布置到独立测试环境，以公网IP进行访问；
优点：
地址固定
缺点：
开发过程中修改麻烦，浪费IP

使用ngrok
优点：
随时在本地搭建，使用方便
缺点：
免费的ngrok每次启动，url地址都不一样，如果前端或其他应用直接使用，一旦ngrok地址发生改变，需要多人多个地方进行改动
解决办法：
在公网的IP机器上搭建一个简单服务，把接收到的请求转接到本地的ngrok地址。前端或者第三方应用每次都请求固定的公网IP，即使ngrok地址发生了改变，每次改动操作也较少。

```

### 使用方法
使用 ./ngrok -h 查看帮助
1：./ngrok http 8000
```
ngrok by @inconshreveable (Ctrl + C to quit)
Tunnel Status                 online
Update                        update available (version 2.1.3, Ctrl-U to update)
Version                       2.0.22/2.1.4       
Region                        United States (us)
Web Interface                 http://127.0.0.1:4040   
Forwarding                    http://1fe84e10.ngrok.io -> localhost:8000  
Forwarding                    https://1fe84e10.ngrok.io -> localhost:8000
Connections                   ttl     opn     rt1     rt5     p50     p90
                            0       0       0.00    0.00    0.00    0.00
主要信息说明：
Web Interface: 本地浏览器输入http://127.0.0.1:4040，可以查看每次api强求，返回的详细信息
Forwarding： 外部可访问的url http://1fe84e10.ngrok.io [处理api请求，并转换到本地的8000端口]

```
