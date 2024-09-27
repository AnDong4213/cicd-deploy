```java
列出所有标签: git tag
查看标签信息：git show v1.0

# 创建一个轻量级标签
git tag v1.0

# 创建一个附注标签
git tag -a v1.0 -m "Version 1.0"

# 创建一个签名标签（需要GPG密钥）
git tag -s v1.0 -m "Signed version 1.0"

# 推送所有标签到远程仓库
git push origin --tags

# 只推送特定的标签
git push origin v1.0

git tag -d v1.0

git push origin :refs/tags/v1.0
```

## Nginx Command

```java
cd /usr/share/nginx
cd /usr/share
cd /etc/nginx   在这个下 cd /var/log/nginx

netstat -tupln | grep 80
ifconfig
nginx -s stop(立即停止)  Or nginx -s quit(优雅停止) 停止nginx

nginx -s reopen(更改日志名称后，重新按配置的记录)
nginx -t(检查文件有没有错误)
nginx -s reload
nginx -h


include /etc/nginx/conf.d/*.conf
include /etc/nginx/sites-enabled/*

// 具体配置
include /etc/nginx/conf.d/*.conf
include /etc/nginx/sites-enabled/* （主要是这个）

root /var/www/html;
```

> 在 Nginx 配置中，server_name 指令用于定义 Nginx 服务器块（server block）处理的域名。这个指令非常关键，因为它决定了 Nginx 如何处理进入的 HTTP 请求。当 Nginx 接收到一个 HTTP 请求时，它会根据请求的 Host 头部字段（即请求的域名）来查找对应的 server 块。
> server {

    listen       80;
    server_name  example.com www.example.com;
    ...

}

|                                                                第一列                                                                |                                    第二列                                     |                                    第三列                                     |
| :----------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------: | :---------------------------------------------------------------------------: |
| ![](https://mmbiz.qpic.cn/mmbiz_jpg/dXcQpaUc9y59kia8bJcvvVJw7uyNOoRdLYXuk4SA0uze6libh1lcQ8OBOibKicbYaEm11YzZw4Ub3VNU8sr8pd7uYQ/640)  | ![](https://p1.music.126.net/lp_KuGIlcvKQg-bnFrv3Qw==/109951164450570662.jpg) | ![](https://p1.music.126.net/WzCLWlYaoVQM9SATteticg==/109951169848359550.jpg) |
| ![](https://mmbiz.qpic.cn/mmbiz_jpg/X2HTlZAyIPKwXdVfBT3iaS58C31dOE6aPiaxpBnGuRHSKic7182YksuJsbzIEaz8bgKwe9PyXiaAPybqcicUWFp3RQg/640) | ![](https://p1.music.126.net/75W0e-j2HD1POLcna-2U7g==/109951168985978546.jpg) | ![](https://p1.music.126.net/4zTo5SYuGcO09mhWcsVlAg==/109951169681143034.jpg) |
|                            ![](https://p1.music.126.net/2-NPAXMOHpfpxujpkZwy5A==/109951167917220568.jpg)                             | ![](http://p1.music.126.net/5di7mpOTNUUUIvUK378-jQ==/109951169715267198.jpg)  | ![](http://p1.music.126.net/jMAmO3a46Ykr1SP2idK6yQ==/109951169663542990.jpg)  |
