~~~
    这个分支我准备用来加一些代码注释,包括push-server本身,以及三方库如socket.io
    所以这个分支包含node_modules目录下的代码,所以在安装运行这个分支时尤其需要注意这点。
    这个分支也能正常运行,且会不定期于将master分支合并进来,以保证最新的代码逻辑
~~~


push-server 5分钟搭建指南
=======================
一台普通配置的服务器, 如我们使用的16G内存 CPU Xeon E5-2620, 可以很轻松的支撑20万日活APP的推送任务.

##install 

* 安装nodejs环境, 推荐6.0以上, LTS版本

https://nodejs.org/en/download/package-manager/

#### 安装/启动redis
```
redis-server &
```

####  安装/更新socket.io-push
```
sudo npm install -g socket.io-push
```

####  新建工作目录, 用于存储日志, 配置文件
```
mkdir push-server    
cd push-server
generate-push-server-config
```

#### 配置

* [config-proxy.js](config-proxy.js), 存在则启动proxy进程.

* [config-api.js](config-api.js), 存在则启动api进程.

* [config-admin.js](config-admin.js) 进程配置,存在则启动admin进程.


#run
```
push-server -f
-f foreground启动,不指定会后台启动
```

* 管理后台 http://localhost:12001/

* 客户端SDK连接HTTP地址 : http://localhost:10001/ 

* 客户端SDK连接HTTPS地址: http://localhost:10443/ 

* api url: http://localhost:11001/
