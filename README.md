# ArDNSPod

基于 DNSPod 用户 API 实现的纯 Shell 动态域名客户端，优先适配网卡地址，无法获得合法外网地址则使用外部接口获取 IP 地址

# 使用方法

- 编辑`ddnspod.sh`，分别修改`/your_real_path/ardnspod`、`arToken`和`arDdnsCheck`为真实信息

- 运行`ddnspod.sh`，开启循环更新任务；建议将此脚本支持添加到计划任务；

- 成功运行后，结果如下所示：

```
Fetching Host Ip
> Host Ip: 11.22.33.55
> Record Type: A
Fetching Ids of test.rehi.org
> Domain Ids: 84982658 766956386
Checking Record for test.rehi.org
> Last Ip: 11.22.33.77
Updating Record for test.rehi.org
> arDdnsUpdate - success
```

### 小提示

如需单文件运行，参考`ddnspod.sh`中的配置项，添加到`ardnspod`底部，直接运行`ardnspod`即可

```
echo "arToken=12345,7676f344eaeaea9074c123451234512d" >> ./ardnspod
echo "arDdnsCheck test.org subdomain" >> ./ardnspod
```

### 代码提交

为保证脚本最大兼容性，提交代码时请注意以下2个问题

- 脚本应以`busybox`或`sh`环境为基础，请勿更改为`bash`或`dash`等shell环境
- 请保证`wget`命令参数兼容`busybox`模式，对于非嵌入式平台应尽量使用`curl`作为请求工具

# 最近更新

2021/6/29

- 优先采用 curl 请求网络
- 移除 wget 的 -t 参数

2021/3/3

- 强化获取IP结果检测
- 优化部分判断逻辑
- 优化消息输出

2021/2/8

- 添加 IPv6 支持
- 优化流程，减少 API 调用次数
- 完善出错提示

2020/8/5

- 修复 `get the wrong recordID` @C-Y-X

2020/1/1

- 适配新版 API（2019-11-26）
- 当`wget`不存在时，尝试使用`curl`提交
- 由于`readlink`不可靠，更改为手动设置路径
- 当无法从本地网卡获得外网 ip 时，尝试从外部 api 获取

2015/2/24

- 增加 token 鉴权方式 (by wbchn)

2015/7/7

- 使用 D+服务获取域名解析

2016/2/25

- 增加配置文件，分离脚本与配置，适配内网。
- 加入 Mac 支持
- sed 脚本 POSIX 化，可跨平台

2016/3/23

- 进一步 POSIX 化，支持 Mac 和大部分 Linux 发行版
- 更改配置文件格式

# 共同维护者

请参阅 <https://github.com/anrip/dnspod-shell/graphs/contributors>
