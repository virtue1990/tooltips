## ngrok简介
```
在后台程序开发过程中，需要向前端，或者其他应用开放接口进行测试，需要一个外部可访问的地址。
ngrok可监控本地的某一个端口，生成全网可访问的url链接
```

## 初级应用
使用 ./ngrok -h 查看帮助
1：ngrok http 8000
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
上面的命令是在后台开发过程中经常使用的命令。
上面的Forwarding地址即外部可访问的url,并转换到本地的8000端口  
可通过浏览器访问http://127.0.0.1:4040 查看详细的每次请求信息                          
```
2：ngrok http foo.dev:80
```
Tunnel to host:port instead of localhost
```

## 高级应用
1：Reserved Doamins
```
free的ngrok每次重新启动，域名都发生了变化，如果想保留固定的域名，需要付费
```
2：Reserved TCP Addredss
```
如果想保留固定的client IP地址（当你需要ssh，RDP...）,需要升级到专业版或企业版
```
3：ngrok tcp 22
```
Tunnel arbitrary tcp traffic to port 22
```
4：ngrok tls -hostname=foo.com 443
```
TLS traffic for foo.com to port 443
```
5：ngrok  confguration file
```
ngrok http -config=/opt/ngrok/conf/ngrok.conf 8000
配置文件格式参考
https://gist.github.com/samrain/31a4000d5b45d29377a9
```
