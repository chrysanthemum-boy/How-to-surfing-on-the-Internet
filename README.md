# How-to-surfing-on-the-Internet
如何通过VPS科学上网

## 前提
- 客户端为Windows系统
- 拥有一台没有被封禁IP的VPS

## 基础版

- 安装x-ui面板
  + [x-ui github地址](https://github.com/vaxilu/x-ui)
  ```
  bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
  ```  
- 在x-ui面板中选择不同协议的节点并开放端口  
- 复制节点信息至V2ray/Clash等客户端软件
  + [v2ray github地址](https://github.com/2dust/v2rayN)
  + [clash_for_windows_pkg github地址](https://github.com/Fndroid/clash_for_windows_pkg)

- 打开自动配置系统代理开始科学上网（或者获取SwitchyOmega和Proxifier对浏览器和本机程序做更为细致的代理)  
  + [SwitchyOmega](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif?hl=zh-CN)  
  + [Proxifier](https://www.proxifier.com/)  
    * Proxifier用户名：`zxhi` 
    * 注册码：`LYZGL-F2KX3-JW5W4-A33MC-25QHH`

## 进阶版

- 获取免费域名  
  [freenom](https://my.freenom.com/)  

- DNS解析域名  
  [Cloudflare](https://dash.cloudflare.com/)
  
- 使用Cloudflare对域名进行CDN代理（做流量的转发）  
  [Cloudflare](https://dash.cloudflare.com/)
  
- 使用CloudFront对域名进行CDN代理（做流量的转发）（可使节点的速度更快）  
  [CloudFront](https://us-east-1.console.aws.amazon.com/)
  
- 获取域名的证书，可以将节点所用的算法改为trojan或者其他算法加上TLS的操作 
  + trojan安装（也可以直接用x-ui）
    * 新建目录
    ```
    mkdr trojan
    ```
    * 下载[trojan-go](https://github.com/p4gefau1t/trojan-go)
    * 解压trojan-go
  + 申请证书：
    * 安装acme：
    ```
    curl https://get.acme.sh | sh
    ```  
    * 安装socat：
    ```
    apt install socat
    ```  
    * 添加软链接：  
    ```
    ln -s /root/.acme.sh/acme.sh /usr/local/bin/acme.sh
    ```
    * 注册账号：
    ```
    acme.sh --register-account -m my@example.com
    ```
    * 开放80端口：
    ```
    ufw allow 80
    ```  
    * 申请证书：
    ```
    acme.sh  --issue -d 你的域名  --standalone -k ec-256
    ```  
    * 安装证书：
    ```
    acme.sh --installcert -d 你的域名 --ecc --key-file  /root/trojan/server.key  --fullchain-file /root/trojan/server.crt
    ```
 
  + 如果默认CA无法颁发，则可以切换下列CA：
    * 切换 Let’s Encrypt：
    ```
    acme.sh --set-default-ca --server letsencrypt
    ```
    * 切换 Buypass：
    ```
    acme.sh --set-default-ca --server buypass
    ```
    * 切换 ZeroSSL：
    ```
    acme.sh --set-default-ca --server zerossl
    ```

## 非纯净IP解锁Netflix等网站的方法

- 使用[warp](https://github.com/fscarmen/warp)刷IP

- 使用[Cloudflare](https://dash.cloudflare.com/)/[CloudFront](https://us-east-1.console.aws.amazon.com/)CDN做流量转发
