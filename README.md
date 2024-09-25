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

|                                           第一列                                            |                                    第二列                                     |                                    第三列                                     |
| :-----------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------: | :---------------------------------------------------------------------------: |
| ![](https://gdp.alicdn.com/imgextra/i3/263817957/TB2oJU9oxHI8KJjy1zbXXaxdpXa-263817957.jpg) | ![](https://p1.music.126.net/lp_KuGIlcvKQg-bnFrv3Qw==/109951164450570662.jpg) | ![](https://p1.music.126.net/WzCLWlYaoVQM9SATteticg==/109951169848359550.jpg) |
|        ![](https://p1.music.126.net/eizz-_YikoaR_OCtaZCcrQ==/109951168521594108.jpg)        | ![](https://p1.music.126.net/75W0e-j2HD1POLcna-2U7g==/109951168985978546.jpg) | ![](https://p1.music.126.net/4zTo5SYuGcO09mhWcsVlAg==/109951169681143034.jpg) |
|        ![](https://p1.music.126.net/2-NPAXMOHpfpxujpkZwy5A==/109951167917220568.jpg)        | ![](http://p1.music.126.net/5di7mpOTNUUUIvUK378-jQ==/109951169715267198.jpg)  | ![](http://p1.music.126.net/jMAmO3a46Ykr1SP2idK6yQ==/109951169663542990.jpg)  |
