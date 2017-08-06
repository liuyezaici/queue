### 安装rabbitmq服务
```
yum install rabbitmq-server
service rabbitmq-server start
```
### 设置开机启动
```
chkconfig rabbitmq-server on
```
### 设置配置文件
```
cd /etc/rabbitmq
cp /usr/share/doc/rabbitmq-server-3.4.1/rabbitmq.config.example /etc/rabbitmq/
mv rabbitmq.config.example rabbitmq.config
```
### 开启用户远程访问
```
vi /etc/rabbitmq/rabbitmq.config
去掉loopback_user {},前的 百分号
#注意要去掉后面的逗号。
```
### 开启web界面管理工具
```
rabbitmq-plugins enable rabbitmq_management
service rabbitmq-server restart
```
### 防火墙开放15672端口
```
/sbin/iptables -I INPUT -p tcp --dport 15672 -j ACCEPT
/etc/rc.d/init.d/iptables save
```

## 安装php-amqplib扩展
```
yum install php-bcmath php-mbstring  php-dom php-curl
git  clone https://github.com/php-amqplib/php-amqplib.git
cd php-amqplib
composer update
```