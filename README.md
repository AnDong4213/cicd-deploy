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

# 强制push
git push origin master --force

https://api.github.com/repos/AnDong4213/cicd-deploy/tags
https://gitee.com/api/v5/repos/zhaoandong4213/lerna-template
https://registry.npmmirror.com/@lernauniversal/commit
https://registry.npmjs.org/axios
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

vim: set nu显示行号
curl -v https://github.com
```

> 在 Nginx 配置中，server_name 指令用于定义 Nginx 服务器块（server block）处理的域名。这个指令非常关键，因为它决定了 Nginx 如何处理进入的 HTTP 请求。当 Nginx 接收到一个 HTTP 请求时，它会根据请求的 Host 头部字段（即请求的域名）来查找对应的 server 块。
> server {

    listen       80;
    server_name  example.com www.example.com;
    ...

}

> 在这个中，server_name 指令后面跟了两个域名：example.com 和 www.example.com。这意味着，当Nginx接收到Host头部为example.com或www.example.com的请求时，就会使用这个server块中的配置来处理这些请求。

### 注意事项

- 顺序：Nginx 按照配置文件中 server 块的顺序来读取 server_name。如果请求匹配了多个 server_name，Nginx 会选择最先匹配到的那个 server 块来处理请求。因此，请确保你的 server 块顺序是按照你的需求来安排的
- 默认服务器：如果没有任何 server*name 能够匹配请求的 Host 头部，Nginx 会选择一个默认的 server 块来处理这个请求。这个默认的 server 块通常监听在 80 或 443 端口上，并且没有 server_name 指令，或者 server_name 被设置为一个不太可能匹配到的值（如*或 default_server）。
- 性能：使用通配符和正则表达式可能会稍微降低 Nginx 处理请求的效率，因为 Nginx 需要对每个请求进行更复杂的匹配操作。但是，在大多数情况下，这种影响是可以忽略不计的。

##### 通过合理配置 server_name，你可以确保 Nginx 能够准确地根据请求的域名来分发请求，从而提供正确的服务和内容。

|                                                                第一列                                                                |                                    第二列                                     |                                    第三列                                     |
| :----------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------: | :---------------------------------------------------------------------------: |
| ![](https://mmbiz.qpic.cn/mmbiz_jpg/dXcQpaUc9y59kia8bJcvvVJw7uyNOoRdLYXuk4SA0uze6libh1lcQ8OBOibKicbYaEm11YzZw4Ub3VNU8sr8pd7uYQ/640)  | ![](https://p1.music.126.net/lp_KuGIlcvKQg-bnFrv3Qw==/109951164450570662.jpg) | ![](https://p1.music.126.net/WzCLWlYaoVQM9SATteticg==/109951169848359550.jpg) |
| ![](https://mmbiz.qpic.cn/mmbiz_jpg/X2HTlZAyIPKwXdVfBT3iaS58C31dOE6aPiaxpBnGuRHSKic7182YksuJsbzIEaz8bgKwe9PyXiaAPybqcicUWFp3RQg/640) | ![](https://p1.music.126.net/75W0e-j2HD1POLcna-2U7g==/109951168985978546.jpg) | ![](https://p1.music.126.net/4zTo5SYuGcO09mhWcsVlAg==/109951169681143034.jpg) |
|                            ![](https://p1.music.126.net/2-NPAXMOHpfpxujpkZwy5A==/109951167917220568.jpg)                             | ![](http://p1.music.126.net/5di7mpOTNUUUIvUK378-jQ==/109951169715267198.jpg)  | ![](http://p1.music.126.net/jMAmO3a46Ykr1SP2idK6yQ==/109951169663542990.jpg)  |
