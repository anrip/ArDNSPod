# ArDNSPod

基于DNSPod用户API实现的纯Shell动态域名客户端，适配网卡地址。

# Usage

复制`dns.conf.example`到任意目录下的`dns.conf`并根据你的配置修改即可。

执行时直接运行`ddnspod.sh [配置文件路径]`，支持cron任务。

配置文件格式：
```
# 安全起见，不推荐使用密码认证
# arMail="test@gmail.com"
# arPass="123"

# 推荐使用Token认证
# 按`TokenID,Token`格式填写
arToken="12345,7676f344eaeaea9074c123451234512d"

# 每行一个域名
arDdnsCheck "test.org" "subdomain" "ip_source" "source_args"

# ip_source(IP源):
# arIpSource_Auto : 自动获取IP 无参数
#     例: arDdnsCheck "test.org" "subdomain" "arIpSource_Auto"
# arIpSource_OpenWrtIF_IPv4 : openwrt下获取接口的IPv4地址 参数(source_args): 接口名称 如: pppoe-wan
#     例: arDdnsCheck "test.org" "subdomain" "arIpSource_OpenWrtIF_IPv4" "pppoe-wan"
```

# 最近更新

2015/2/24
- 增加token鉴权方式 (by wbchn)

2015/7/7
- 使用D+服务获取域名解析

2016/2/25
- 增加配置文件，分离脚本与配置，适配内网。
- 加入Mac支持
- sed脚本POSIX化，可跨平台

2016/3/23
- 进一步POSIX化，支持Mac和大部分Linux发行版
- 更改配置文件格式

# Credit

Original: anrip

This version maintained by ProfFan
