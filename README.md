# How-to-surfing-on-the-Internet
如何通过VPS科学上网

## 前提

拥有一台没有被封禁IP的VPS

## 基础版

- 1.安装x-ui面板
https://github.com/vaxilu/x-ui

- 2.在x-ui面板中选择不同协议的节点并开放端口
```
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```

- 3.复制节点信息至V2ray/Clash等客户端软件

- 4.打开自动配置系统代理开始科学上网（或者获取SwitchyOmega和Proxifier对浏览器和本机程序做更为细致的代理)

## 进阶版

1.获取域名

2.DNS解析域名

3.使用Cloudflare对域名进行CDN代理（做流量的转发）

4.使用CloudFront对域名进行CDN代理（做流量的转发）（可使节点的速度更快）

5.获取域名的证书，可以将节点所用的算法改为trojan或者其他算法加上TLS的操作

## 解锁Netflix等网站的方法

1.使用warp自动刷IP（目前没有效果）

2.使用CDN做流量转发
