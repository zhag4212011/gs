### 一.allinone-LiveRedirect一键部署

```
docker run -d --restart unless-stopped --privileged=true -p 35455:35455 --name allinone youshandefeiyang/allinone
```
### 配置watchtower每天凌晨两点自动监听allinone镜像更新：
```
docker run -d --name watchtower --restart unless-stopped -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower allinone -c --schedule "0 0 2 * * *"
```
### 另外，如果你部署在公网上，由于代理了ts切片导致有可能被别人偷走大量流量，为此设置了一个指令，可以控制itv和ysptp的开关：

### 直接运行裸二进制且不想开启tv直播服务：
```
./allinone_linux_amd64 -tv=false
```
### 如果你用PM2运行裸二进制并且进程守护且不想开启tv直播服务：
```
pm2 start allinone_linux_amd64 --watch --name allinone -- -tv=false
```
如果你用Docker部署且不想开启tv直播服务：
```
docker run -d --restart unless-stopped --privileged=true -p 35455:35455 --name allinone youshandefeiyang/allinone -tv=false
```
### 当然默认不加-tv=false参数是提供直播服务的！

部署完成后的订阅地址如下

========================面板账户登录信息==========================

 【云服务器】请在安全组放行 22139 端口
 外网面板地址: 
```
https://103.146.53.122:22139/eb80ec66
```
 内网面板地址:
```
https://103.146.53.122:22139/eb80ec66
```
账号:
cppozp8n
密码:: 
d72e4022

IPTV直播：
```
http://27.152.28.47:35455/tv.m3u
```
```
http://124.70.221.57:5000/4gtv.m3u
```

虎牙一起看：http://你的IP:35455/huyayqk.m3u?url=http://你的IP:35455

斗鱼一起看：http://你的IP:35455/douyuyqk.m3u?url=http://你的IP:35455

YY轮播：http://你的IP:35455/yylunbo.m3u?url=http://你的IP:35455

BiliBili生活：http://你的IP:35455/bililive.m3u?url=http://你的IP:35455

另外，如果你想公网部署并且反代35455端口，也同样可以，比如：

https://example.com/tv.m3u

里面的节目列表会自动根据你的hostname和port修改的

特别强调一下，本群的DNS解析链接ottdns.com仅仅用于itv直播测试，请不要用来解析其他服务，如果导致被通告，我这边直接会下掉的，希望大家理解，之前的服务没必要部署了，allinone全部集成了，用go只是为了整合方便，我用java，php，python，go，nodejs我都会，go高并发而且占用内存极低，整个allinone程序才20多MB，你用其他语言根本不如它！



PS：各种奈飞、YouTuBe、HBO、Disney、ChatGPT、Apple TV、家庭影音搭建必备品可以访问本频道推荐合租平台下单！